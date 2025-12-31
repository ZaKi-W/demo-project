<!-- 情报数据 -->
<script setup>
import { onMounted } from "vue";
import Card from "./Card.vue";
import * as echarts from "echarts";

onMounted(() => {});
</script>
<template>
  <Card class="w-100" title="情报数据">
    <div
      style="
        height: 182px;
        flex: 1;
        padding: 10.5px 16px 12px 15.5px;
        box-sizing: border-box;
      "
    >
      <div
        style="
          height: 75px;
          background-color: rgba(255, 255, 255, 0.1);
          margin-bottom: 10px;
          padding: 11.5px;
          box-sizing: border-box;
        "
      >
        <div style="display: flex; align-items: center; margin-bottom: 12px">
          <div
            style="
              width: 14px;
              height: 14px;
              background-color: #28f1ff;
              border-radius: 50%;
              margin-right: 11.5px;
            "
          ></div>
          <div style="color: #28effa; font-size: 18px; line-height: 20px">
            [航行通告·危险活动]
          </div>
        </div>
        <div style="color: #fff; font-size: 18px; line-height: 20px">
          大同市云州区区域划定临时危险区，因大型跳伞活动，12月5日08:00-12:00
        </div>
      </div>
      <div
        style="
          height: 75px;
          background-color: rgba(255, 255, 255, 0.1);
          padding: 11.5px;
          box-sizing: border-box;
        "
      >
        <div style="display: flex; align-items: center; margin-bottom: 12px">
          <div
            style="
              width: 14px;
              height: 14px;
              background-color: #28f1ff;
              border-radius: 50%;
              margin-right: 11.5px;
            "
          ></div>
          <div style="color: #28effa; font-size: 18px; line-height: 20px">
            [航行通告·危险活动]
          </div>
        </div>
        <div style="color: #fff; font-size: 18px; line-height: 20px">
          大同市云州区区域划定临时危险区，因大型跳伞活动，12月5日08:00-12:00
        </div>
      </div>
    </div>
  </Card>
</template>
<style scoped></style>
