<script setup>
import * as echarts from "echarts";
import Card from "./Card.vue";
import { onMounted } from "vue";

const data3 = [
  20, 280, 70, 232, 256, 76, 135, 162.2, 32.6, 20.0, 6.4, 3.3, 40, 210, 120,
  180, 190, 85, 101, 77, 250, 67, 99,
];

// 把柱子的宽度缩窄一半
const offsetX = 9;
const offsetY = 5;
const CubeLeft = echarts.graphic.extendShape({
  shape: {
    x: 0,
    y: 0,
  },
  buildPath: function (ctx, shape) {
    const xAxisPoint = shape.xAxisPoint;
    const c0 = [shape.x, shape.y];
    const c1 = [shape.x - offsetX, shape.y - offsetY];
    const c2 = [xAxisPoint[0] - offsetX, xAxisPoint[1] - offsetY];
    const c3 = [xAxisPoint[0], xAxisPoint[1]];
    ctx
      .moveTo(c0[0], c0[1])
      ?.lineTo(c1[0], c1[1])
      .lineTo(c2[0], c2[1])
      .lineTo(c3[0], c3[1])
      .closePath();
  },
});

// 绘制右侧面
const CubeRight = echarts.graphic.extendShape({
  shape: {
    x: 0,
    y: 0,
  },
  buildPath: function (ctx, shape) {
    const xAxisPoint = shape.xAxisPoint;
    const c1 = [shape.x, shape.y];
    const c2 = [xAxisPoint[0], xAxisPoint[1]];
    const c3 = [xAxisPoint[0] + offsetX, xAxisPoint[1] - offsetY];
    const c4 = [shape.x + offsetX, shape.y - offsetY];
    ctx
      .moveTo(c1[0], c1[1])
      ?.lineTo(c2[0], c2[1])
      .lineTo(c3[0], c3[1])
      .lineTo(c4[0], c4[1])
      .closePath();
  },
});

// 绘制顶面
const CubeTop = echarts.graphic.extendShape({
  shape: {
    x: 0,
    y: 0,
  },
  buildPath: function (ctx, shape) {
    const c1 = [shape.x, shape.y];
    const c2 = [shape.x + offsetX, shape.y - offsetY];
    const c3 = [shape.x, shape.y - offsetY * 2];
    const c4 = [shape.x - offsetX, shape.y - offsetY];
    ctx
      .moveTo(c1[0], c1[1])
      ?.lineTo(c2[0], c2[1])
      .lineTo(c3[0], c3[1])
      .lineTo(c4[0], c4[1])
      .closePath();
  },
});

// 注册三个面图形
echarts.graphic.registerShape("CubeLeft", CubeLeft);
echarts.graphic.registerShape("CubeRight", CubeRight);
echarts.graphic.registerShape("CubeTop", CubeTop);
const option3 = {
  backgroundColor: "#022051",
  tooltip: {
    trigger: "axis",
    axisPointer: {
      type: "shadow",
    },
  },
  grid: {
    left: "2%",
    right: "4%",
    bottom: "15%", // 留出底部滚动条位置
    top: "15%",
    containLabel: true,
  },
  // 调整图像x轴
  xAxis: {
    data: [
      "00",
      "01",
      "02",
      "03",
      "04",
      "05",
      "06",
      "07",
      "08",
      "09",
      "10",
      "11",
      "12",
      "13",
      "14",
      "15",
      "16",
      "17",
      "18",
      "19",
      "20",
      "21",
      "22",
    ],
    axisTick: {
      show: false,
    },
    axisLabel: {
      show: true,
      color: "#333",
      //  rotate: 30,
      textStyle: {
        color: "rgba(189, 217, 255, 1)",
        fontSize: 14,
      },
    },
    axisLine: {
      show: true,
      lineStyle: {
        color: "rgba(189, 217, 255, 1)",
      },
    },
  },
  //调整图像y轴
  yAxis: [
    {
      type: "value",
      alignTicks: true,
      nameTextStyle: {
        color: "rgba(189, 217, 255, 1)",
        fontSize: 14,
      },
      lineStyle: {
        show: "none",
        type: "dashed",
      },

      axisLine: {
        show: true,
        lineStyle: {
          color: "rgba(189, 217, 255, 1)",
        },
      },
      axisTick: { show: false },
      axisLabel: {
        show: true,
        color: "rgba(189, 217, 255, 1)",
        fontSize: 14,
      },
      splitLine: {
        show: true,
        lineStyle: {
          color: "rgba(83, 132, 201, 1)", // 极淡的分割线
          type: "solid",
        },
      },
    },
  ],
  series: [
    {
      type: "custom",
      yAxisIndex: 0,
      renderItem: (_, api) => {
        const location = api.coord([api.value(0), api.value(1)]);
        return {
          type: "group",
          children: [
            {
              type: "CubeLeft",
              shape: {
                api,
                xValue: api.value(0),
                yValue: api.value(1),
                x: location[0],
                y: location[1],
                xAxisPoint: api.coord([api.value(0), 0]),
              },
              style: {
                fill: new echarts.graphic.LinearGradient(
                  0,
                  0,
                  0,
                  1, // 坐标：从上(0,0) 到 下(0,1)，即 CSS 的 180deg
                  [
                    {
                      offset: 0, // 对应 0%
                      color: "rgba(4, 45, 209, .5)",
                    },
                    {
                      offset: 1, // 对应 100%
                      color: "rgba(102, 165, 242, .5)",
                    },
                  ]
                ),
              },
            },
            {
              type: "CubeRight",
              shape: {
                api,
                xValue: api.value(0),
                yValue: api.value(1),
                x: location[0],
                y: location[1],
                xAxisPoint: api.coord([api.value(0), 0]),
              },
              style: {
                fill: new echarts.graphic.LinearGradient(
                  0,
                  0,
                  0,
                  1, // 坐标：(x1, y1) -> (x2, y2)，从上(0,0)到下(0,1)
                  [
                    {
                      offset: 0, // 0% 处的颜色
                      color: "rgba(31, 72, 241, .5)",
                    },
                    {
                      offset: 1, // 100% 处的颜色
                      color: "rgba(97, 168, 255, .5)",
                    },
                  ]
                ),
              },
            },
            {
              type: "CubeTop",
              shape: {
                api,
                xValue: api.value(0),
                yValue: api.value(1),
                x: location[0],
                y: location[1],
                xAxisPoint: api.coord([api.value(0), 0]),
              },
              style: {
                // fill: '#6BB6FF',
                fill: new echarts.graphic.LinearGradient(
                  // 坐标：(x1, y1, x2, y2)
                  // 161.62度大约是从 "左上(略偏右)" 指向 "右下"
                  // 这里使用近似值模拟 161度 (x从0到0.33, y从0到1)
                  0,
                  0,
                  0.33,
                  1,
                  [
                    {
                      offset: 0,
                      color: "rgba(145, 231, 255, 1)", // 0% 处的颜色
                    },
                    {
                      offset: 0.1597,
                      color: "rgba(0, 187, 255, 1)", // 15.97% 处的颜色
                    },
                    {
                      offset: 1,
                      color: "rgba(0, 125, 184, 1)", // 100% 处的颜色
                    },
                  ]
                ),
              },
            },
          ],
        };
      },
      data: data3,
    },
    {
      type: "bar",
      barWidth: 10, // 原来20，缩窄一半
      label: {
        show: false,
        position: "top",
        formatter: (e) => {
          return e.value + "%";
        },
        fontSize: 16,
        fontWeight: 700,
        color: "#333",
        offset: [0, -15],
      },
      // yAxisIndex: 0,
      itemStyle: {
        color: "transparent",
      },
      tooltip: { show: false },
      data: data3,
    },
    {
      name: "Temperature",
      type: "line",
      smooth: true,
      symbolSize: 0,
      lineStyle: {
        width: 2,
        color: "#29F1FA",
      },
      tooltip: {
        valueFormatter: function (value) {
          return value;
        },
      },
      data: data3,
    },
  ],
};

onMounted(() => {
  const charts3 = echarts.init(document.getElementById("demoId3"));
  charts3.setOption(option3);
});
</script>
<template>
  <Card class="w-60 mr-8" title="航班流量">
    <div style="height: 100%; flex: 1; display: flex; flex-direction: column">
      <div
        style="
          height: 60px;
          margin-bottom: 8px;
          display: flex;
          flex-direction: column;
        "
      >
        <div
          style="
            padding-left: 30px;
            padding-top: 10px;
            font-size: 10px;
            color: #fff;
          "
        >
          飞行总时长
        </div>
        <div
          style="
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding-left: 25px;
            padding-right: 20px;
          "
        >
          <div style="display: flex; align-items: center; padding-top: 10px">
            <div
              style="
                font-size: 24px;
                color: #00ffff;
                font-family: 'Digital';
                margin-right: 10px;
              "
            >
              2430
            </div>
            <div style="font-size: 10px; color: #fff">小时</div>
          </div>
          <div style="color: #ffffffa3; font-size: 10px">单位：小时</div>
        </div>
      </div>
      <div id="demoId3" style="height: 100%"></div>
    </div>
  </Card>
</template>
<style scoped></style>
