<script setup>
import { onMounted } from "vue";
import Card from "./Card.vue";
import * as echarts from "echarts";
const data = [
  { name: "A类", value: 40, color: "#00ffff" },
  { name: "B类", value: 30, color: "#3ba1ff" },
  { name: "C类", value: 20, color: "#36cfc9" },
  { name: "D类", value: 10, color: "#9254de" },
  { name: "E类", value: 13, color: "#2234de" },
  { name: "F类", value: 50, color: "#4254de" },
  { name: "G类", value: 25, color: "#7254de" },
];

const option2 = {
  series: [
    {
      type: "pie",
      radius: ["60%", "98%"], // 增大内外半径比例
      center: ["50%", "50%"],
      data: data.map((d) => ({
        value: d.value,
        name: d.name,
        itemStyle: { color: d.color },
      })),
      label: { show: false },
      labelLine: { show: false },
    },
  ],
  graphic: [
    {
      type: "group",
      left: "center",
      top: "center",
      silent: true,
      children: [
        {
          type: "text",
          left: -10,
          top: -15,
          style: {
            text: "13",
            fill: "#00ffff",
            fontSize: 32,
            fontFamily: "Digital",
            textAlign: "center",
          },
        },
        {
          type: "text",
          top: 0,
          left: 30,
          style: {
            text: "条",
            fill: "#8fdfff",
            fontSize: 12,
            textAlign: "center",
          },
        },
        {
          type: "text",
          top: 25,
          left: -15,
          style: {
            text: "当日申请",
            fill: "#8fdfff",
            fontSize: 12,
            textAlign: "center",
          },
        },
      ],
    },
  ],
};
onMounted(() => {
  const charts2 = echarts.init(document.getElementById("demoId2"));
  charts2.setOption(option2);
});
</script>
<template>
  <Card class="w-50" title="今日申请计划">
    <div style="height: 100%; display: flex">
      <div class="num-box">
        <div class="num-item">
          <div class="num">45</div>
          <div class="text">申请总数(条)</div>
        </div>
        <div class="num-item">
          <div class="num">45</div>
          <div class="text">临时空域(条)</div>
        </div>
        <div class="num-item">
          <div class="num">45</div>
          <div class="text">长期计划(条)</div>
        </div>
        <div class="num-item">
          <div class="num">45</div>
          <div class="text">次日计划(条)</div>
        </div>
      </div>
      <div id="demoId2" style="flex: 1; height: 100%"></div>
      <div class="legend-box">
        <div class="legend-item" v-for="item in data">
          <div
            class="item-dot"
            :style="`background-color: ${item.color};`"
          ></div>
          <div class="legend-title">{{ item.name }}</div>
          <div class="legend-percent">{{ item.value }}%</div>
        </div>
      </div>
    </div>
  </Card>
</template>
<style scoped>
.num-box {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 11px;
  justify-content: space-between;
}
.num-item {
  background-image: url("../../public/legend-img.png");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  width: 101px;
  height: 53px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 8px;
  box-sizing: border-box;
}
.num-item .num {
  font-family: "Digital";
  font-size: 24px;
  color: #00ffff;
}
.num-item .text {
  font-size: 10px;
  color: #fff;
}
</style>
