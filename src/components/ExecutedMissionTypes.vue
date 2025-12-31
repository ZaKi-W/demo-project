<!-- 本月已执行任务性质 -->
<script setup>
import { onMounted } from "vue";
import Card from "./Card.vue";
import * as echarts from "echarts";

let chartData = [
  {
    name: "类型1",
    value: 123,
  },
  {
    name: "类型2",
    value: 262,
  },
  {
    name: "类型3",
    value: 210,
  },
  {
    name: "类型4",
    value: 170,
  },
  {
    name: "类型5",
    value: 190,
  },
];

let dataArr = chartData.map((e) => e.value);
let max = Math.max(...dataArr) * 1.2;
let indicatorArr = chartData.map((e) => {
  return {
    text: e.name,
    max,
  };
});
const option5 = {
  tooltip: {
    trigger: "item",
  },
  radar: {
    radius: "50%",
    indicator: indicatorArr,
    splitNumber: 5,
    splitLine: {
      show: true,
      lineStyle: {
        width: 2,
        color: [
          "#102261",
          "#102261",
          "#102261",
          "#223876",
          "#102261",
          "#C0C0C0",
        ], // 分隔区域边框
        opacity: 0.3, // 边框透明度
      },
    },
    splitArea: {
      // 坐标轴在 grid中的分隔区域，默认不显示
      show: true,
      areaStyle: {
        // 分隔区域的样式设置
        color: [
          "rgba(0, 78, 156, 0.50)",
          "rgba(0, 31, 62, 1)",
          "rgba(0, 78, 156, 0.50)",
          "rgba(0, 31, 62, 1)",
          "rgba(0, 78, 156, 0.50)",
        ], // 分隔区域颜色数组
      },
    },
    axisLine: {
      lineStyle: {
        color: "#C0C0C0",
        width: 1,
        opacity: 0.2,
      },
    },
    name: {
      // 雷达图每个指示器的名称
      textStyle: {
        color: "#fff",
      },
    },
  },
  series: [
    {
      type: "radar",
      symbolSize: 0,
      areaStyle: {
        color: "rgba(21, 147, 231, .7)",
      },
      lineStyle: {
        width: 1,
        color: "rgba(24,167,188, 1)",
      },
      data: [
        {
          value: dataArr,
        },
      ],
    },
  ],
};

onMounted(() => {
  const charts5 = echarts.init(document.getElementById("demoId5"));
  charts5.setOption(option5);
});
</script>

<template>
  <Card class="w-36" title="本月已执行任务性质">
    <div style="height: 100%; display: flex; box-sizing: border-box">
      <div id="demoId5" style="width: 230px; height: 100%"></div>
      <div style="padding-top: 35px">
        <div
          style="
            margin-bottom: 23px;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            width: 96.5px;
            height: 46px;
            background-image: url('../../public/small-card-bg.png');
            background-position: center;
            background-repeat: no-repeat;
            background-size: cover;
          "
        >
          <div style="font-size: 10px; color: #fff">空中游览</div>
          <div style="color: #28f1ff; font-size: 16px; font-family: 'Digital'">
            116
          </div>
        </div>
        <div
          style="
            margin-bottom: 23px;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            width: 96.5px;
            height: 46px;
            background-image: url('../../public/small-card-bg.png');
            background-position: center;
            background-repeat: no-repeat;
            background-size: cover;
          "
        >
          <div style="font-size: 10px; color: #fff">航校训练</div>
          <div style="color: #28f1ff; font-size: 16px; font-family: 'Digital'">
            104
          </div>
        </div>
        <div
          style="
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            width: 96.5px;
            height: 46px;
            background-image: url('../../public/small-card-bg.png');
            background-position: center;
            background-repeat: no-repeat;
            background-size: cover;
          "
        >
          <div style="font-size: 10px; color: #fff">航空摄影</div>
          <div style="color: #28f1ff; font-size: 16px; font-family: 'Digital'">
            21
          </div>
        </div>
      </div>
    </div>
  </Card>
</template>
<style scoped></style>
