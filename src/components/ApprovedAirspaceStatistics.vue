<!-- 批复空域统计 -->
<script setup>
import { onMounted } from "vue";
import Card from "./Card.vue";
import * as echarts from "echarts";

const data6 = [
  { name: "航线1", value: 38 },
  { name: "航线2", value: 65 },
  { name: "航线3", value: 44 },
  { name: "航线4", value: 52 },
  { name: "航线5", value: 81 },
  { name: "航线6", value: 250 },
  { name: "航线7", value: 100 },
  { name: "航线8", value: 80 },
];
const maxArray = new Array(data6.map((item) => item.value).length).fill(
  Math.max(...data6.map((item) => item.value))
);
const points = data6.map((item) => {
  let obj = {
    name: "top-line",
    xAxis: item.name,
    yAxis: item.value,
    symbol: "rect",
    symbolSize: [17, 3],
    itemStyle: {
      color: "rgba(255, 255, 255, 1)",
      shadowColor: "rgba(255, 255, 255, 1)",
      shadowBlur: 10,
      shadowOffsetY: -3,
    },
  };
  return obj;
});

const option6 = {
  tooltip: {
    show: true,
    trigger: "item",
    backgroundColor: "rgba(21, 154, 255, 0.32)",
    textStyle: {
      color: "#fff",
    },
  },
  backgroundColor: "rgba(8, 30, 80, 1)",
  grid: {
    top: "13%",
    left: "3%",
    right: "4%",
    bottom: "3%",
    containLabel: true,
  },
  // 添加第二个 xAxis 用于折线图偏移
  xAxis: {
    type: "category",
    data: data6.map((item) => item.name),
    // axisTick: {
    //     show: false
    // },
    // axisLabel: {
    //     color: "rgba(162, 217, 255, 1)",
    //     fontSize: 12,
    //     margin: 20
    // },
    // axisLine: {
    //     lineStyle: {
    //         color: "rgba(19, 44, 95, 1)",
    //         width: 1
    //     }
    // },
  },
  yAxis: {
    type: "value",
    // nameGap: 35,
    nameTextStyle: {
      color: "rgba(162, 217, 255, 1)",
      fontSize: 12,
    },
    // axisLine: {
    //     lineStyle: {
    //         color: '#3C6579'
    //     }
    // },
    axisTick: {
      show: false,
    },
    splitLine: {
      lineStyle: {
        color: "#173055",
        // type: 'dashed'
      },
    },
    // axisLabel: {
    //     color: 'rgba(162, 217, 255, 1)',
    //     fontSize: 12
    // },
  },
  series: [
    {
      type: "bar",
      barWidth: 6,
      data: data6.map((item) => item.value),
      itemStyle: {
        borderRadius: [0, 0, 0, 0],
        color: {
          type: "linear",
          x: 0,
          y: 0,
          x2: 0,
          y2: 1,
          colorStops: [
            { offset: 0, color: "rgba(86, 176, 254, 1)" },
            { offset: 0.1, color: "rgba(68, 163, 255, 1)" },
            { offset: 1, color: "rgba(46, 140, 255, 1)" },
          ],
          global: false,
        },
      },
    },
    {
      name: "",
      barGap: "-150%",
      type: "bar",
      z: 0,
      data: maxArray,
      barWidth: 12,
      itemStyle: {
        normal: {
          color: "rgba(11, 36, 89, 0.8)",
        },
      },
      tooltip: {
        show: false,
      },
    },
  ],
};

onMounted(() => {
  const charts6 = echarts.init(document.getElementById("demoId6"));
  charts6.setOption(option6);
});
</script>
<template>
  <Card class="w-50 mr-8" title="批复空域统计">
    <div style="height: 256px; position: relative" id="demoId6">
      <div
        style="
          position: absolute;
          right: 10px;
          top: 10px;
          color: rgba(255, 255, 255, 0.64);
          font-size: 10px;
        "
      >
        单位：次
      </div>
    </div>
  </Card>
</template>
<style scoped></style>
