<!-- 气象数据 -->
<script setup>
import { onMounted } from "vue";
import Card from "./Card.vue";
import * as echarts from "echarts";

onMounted(() => {});
</script>
<template>
  <Card class="w-100" title="气象数据">
    <div
      style="
        height: 182px;
        flex: 1;
        box-sizing: border-box;
        padding: 10.5px 13.5px 9.5px 17.5px;
      "
    >
      <div
        style="
          display: flex;
          align-items: center;
          height: 50px;
          margin-bottom: 6px;
          background-image: url('../../public/info-bg.png');
          background-position: center;
          background-size: cover;
          background-repeat: no-repeat;
          padding: 7px 0 7px 13px;
          box-sizing: border-box;
        "
      >
        <div
          style="
            height: 36px;
            width: 165.5px;
            margin-right: 21.5px;
            background-color: rgba(238, 62, 62, 0.3);
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 18px;
            color: #ee3e3e;
          "
        >
          大风红色预警
        </div>
        <div style="font-size: 18px; color: #fff">
          太原武宿机场区域，瞬时风力可达9级，预计持续至16:00。影响：所有低空起降
        </div>
      </div>
      <div
        style="
          display: flex;
          align-items: center;
          height: 50px;
          margin-bottom: 6px;
          background-image: url('../../public/info-bg.png');
          background-position: center;
          background-size: cover;
          background-repeat: no-repeat;
          padding: 7px 0 7px 13px;
          box-sizing: border-box;
        "
      >
        <div
          style="
            height: 36px;
            width: 165.5px;
            margin-right: 21.5px;
            background-color: rgba(251, 154, 85, 0.3);
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 18px;
            color: #fb9a55;
          "
        >
          低能见度
        </div>
        <div style="font-size: 18px; color: #fff">
          太原武宿机场区域，瞬时风力可达9级，预计持续至16:00。影响：所有低空起降
        </div>
      </div>
      <div
        style="
          display: flex;
          align-items: center;
          height: 50px;
          background-image: url('../../public/info-bg.png');
          background-position: center;
          background-size: cover;
          background-repeat: no-repeat;
          padding: 7px 0 7px 13px;
          box-sizing: border-box;
        "
      >
        <div
          style="
            height: 36px;
            width: 165.5px;
            margin-right: 21.5px;
            background-color: rgba(238, 62, 62, 0.3);
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 18px;
            color: #ee3e3e;
          "
        >
          大风红色预警
        </div>
        <div style="font-size: 18px; color: #fff">
          太原武宿机场区域，瞬时风力可达9级，预计持续至16:00。影响：所有低空起降
        </div>
      </div>
    </div>
  </Card>
</template>
<style scoped></style>
