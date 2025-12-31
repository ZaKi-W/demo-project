<!-- 航天器月度执飞情况 -->
<script setup>
import { onMounted } from "vue";
import Card from "./Card.vue";
import * as echarts from "echarts";

const data4 = [150, 50, 230, 50, 150, 100];
const option4 = {
  grid: {
    left: "3%",
    right: "4%",
    bottom: "3%",
    top: "5%",
    containLabel: true,
  },
  tooltip: {
    trigger: "axis",
  },
  xAxis: {
    type: "category",
    data: ["1月", "2月", "3月", "4月", "5月", "6月"],
    axisLine: {
      show: true,
      lineStyle: {
        color: "#BAE7FF",
        width: 1,
        type: "solid",
      },
    },
    axisTick: {
      show: false,
    },
  },
  yAxis: {
    axisLine: {
      show: true,
      lineStyle: {
        color: "#BAE7FF",
        width: 1,
        type: "solid",
      },
    },
    splitLine: {
      lineStyle: {
        color: "rgba(186, 231, 255, 0.2)",
        type: "dashed",
      },
    },
    axisLabel: {
      show: true,
      textStyle: {
        color: "white", //更改坐标轴文字颜色
      },
    },
    axisTick: {
      show: false,
    },
  },
  series: [
    {
      name: "架次",
      type: "pictorialBar",
      barCategoryGap: "40%",
      symbol: "triangle",
      barWidth: "100%",
      symbol: "path://M0,10 L10,10 C5.5,10 5.5,5 5,0 C4.5,5 4.5,10 0,10 z",
      itemStyle: {
        normal: {
          opacity: 0.8,
          // color:'RGBA(133, 255, 105, 1)',
          color: new echarts.graphic.LinearGradient(
            0,
            1,
            0,
            0,
            [
              {
                offset: 0,
                color: "rgba(54, 144, 253, 1)", // 0% 处的颜色
              },
              {
                offset: 1,
                color: "rgba(40, 241, 255, 1)", // 60% 处的颜色
              },
              {
                offset: 1,
                color: "rgba(40, 241, 255, 1)", // 100% 处的颜色
              },
            ],
            false
          ),
          borderColor: "#15B1FF", // 边框颜色
          borderWidth: 2, // 边框宽度
          borderRadius: [100, 100],
        },
        emphasis: {
          opacity: 1,
        },
      },
      data: data4,
      z: 10,
    },
  ],
};

onMounted(() => {
  const charts4 = echarts.init(document.getElementById("demoId4"));
  charts4.setOption(option4);
});
</script>

<template>
  <Card class="w-60 mr-8" title="航空器月度执飞情况">
    <div
      style="
        height: 100%;
        display: flex;
        padding-left: 15px;
        padding-top: 15px;
        box-sizing: border-box;
      "
    >
      <div style="height: 100%; padding-top: 10px">
        <div style="display: flex; align-items: start; margin-bottom: 14.5px">
          <div style="font-size: 14px; color: #fff; width: 60px">固定翼：</div>
          <div
            style="
              font-size: 24px;
              color: #28f1ff;
              width: 60px;
              text-align: right;
              font-family: 'Digital';
              margin-right: 8.5px;
            "
          >
            8000
          </div>
          <div style="font-size: 14px; color: #fff; margin-right: 10px">
            架次
          </div>
          <div
            style="
              width: 70px;
              height: 30px;
              background-image: url('../../public/small-card-bg.png');
              background-position: center;
              background-size: contain;
              background-repeat: no-repeat;
              display: flex;
              justify-content: center;
              align-items: center;
            "
          >
            <div style="font-size: 10px; color: #fff">固定翼</div>
          </div>
        </div>
        <div style="display: flex; align-items: start; margin-bottom: 14.5px">
          <div style="font-size: 14px; color: #fff; width: 60px">单旋翼：</div>
          <div
            style="
              font-size: 24px;
              color: #28f1ff;
              width: 60px;
              text-align: right;
              font-family: 'Digital';
              margin-right: 8.5px;
            "
          >
            2000
          </div>
          <div style="font-size: 14px; color: #fff; margin-right: 10px">
            架次
          </div>
          <div
            style="
              width: 70px;
              height: 30px;
              background-image: url('../../public/small-card-bg.png');
              background-position: center;
              background-size: contain;
              background-repeat: no-repeat;
              display: flex;
              justify-content: center;
              align-items: center;
            "
          >
            <div style="font-size: 10px; color: #fff">单旋翼</div>
          </div>
        </div>
        <div style="display: flex; align-items: start; margin-bottom: 14.5px">
          <div style="font-size: 14px; color: #fff; width: 60px">多轴：</div>
          <div
            style="
              font-size: 24px;
              color: #28f1ff;
              width: 60px;
              text-align: right;
              font-family: 'Digital';
              margin-right: 8.5px;
            "
          >
            500
          </div>
          <div style="font-size: 14px; color: #fff; margin-right: 10px">
            架次
          </div>
          <div
            style="
              width: 70px;
              height: 30px;
              background-image: url('../../public/small-card-bg.png');
              background-position: center;
              background-size: contain;
              background-repeat: no-repeat;
              display: flex;
              justify-content: center;
              align-items: center;
            "
          >
            <div style="font-size: 10px; color: #fff">多轴</div>
          </div>
        </div>
        <div style="display: flex; align-items: start; margin-bottom: 14.5px">
          <div style="font-size: 14px; color: #fff; width: 60px">复合翼：</div>
          <div
            style="
              font-size: 24px;
              color: #28f1ff;
              width: 60px;
              text-align: right;
              font-family: 'Digital';
              margin-right: 8.5px;
            "
          >
            300
          </div>
          <div style="font-size: 14px; color: #fff; margin-right: 10px">
            架次
          </div>
          <div
            style="
              width: 70px;
              height: 30px;
              background-image: url('../../public/small-card-bg.png');
              background-position: center;
              background-size: contain;
              background-repeat: no-repeat;
              display: flex;
              justify-content: center;
              align-items: center;
            "
          >
            <div style="font-size: 10px; color: #fff">复合翼</div>
          </div>
        </div>
        <div style="display: flex; align-items: start">
          <div style="font-size: 14p0; color: #fff; width: 60px">其他：</div>
          <div
            style="
              font-size: 24px;
              color: #28f1ff;
              width: 60px;
              text-align: right;
              font-family: 'Digital';
              margin-right: 8.5px;
            "
          >
            400
          </div>
          <div style="font-size: 14px; color: #fff; margin-right: 10px">
            架次
          </div>
          <div
            style="
              width: 70px;
              height: 30px;
              background-image: url('../../public/small-card-bg.png');
              background-position: center;
              background-size: contain;
              background-repeat: no-repeat;
              display: flex;
              justify-content: center;
              align-items: center;
            "
          >
            <div style="font-size: 10px; color: #fff">其他</div>
          </div>
        </div>
      </div>
      <div style="flex: 1; display: flex; flex-direction: column">
        <div
          style="
            color: rgba(255, 255, 255, 0.64);
            font-size: 10px;
            align-self: flex-end;
            padding-right: 10px;
          "
        >
          单位：架次
        </div>
        <div id="demoId4" style="flex: 1"></div>
      </div>
    </div>
  </Card>
</template>
<style scoped></style>
