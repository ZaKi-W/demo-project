<!-- 报送计划统计 -->
<script setup>
import { onMounted } from "vue";
import Card from "./Card.vue";
import * as echarts from "echarts";

onMounted(() => {});
</script>
<template>
  <Card class="w-50" title="报送计划统计">
    <div style="height: 256px">
      <div
        style="
          display: flex;
          justify-content: space-between;
          align-items: flex-end;
          padding: 8px 10px 10px 20px;
        "
      >
        <div style="display: flex; flex-direction: column">
          <div style="font-size: 10px; color: #fff; margin-bottom: 5px">
            报送总次数
          </div>
          <div style="display: flex; align-items: baseline">
            <div
              style="
                font-size: 30px;
                color: #28f1ff;
                font-family: 'Digital';
                margin-right: 10px;
              "
            >
              430
            </div>
            <div style="font-size: 10px; color: #fff">次</div>
          </div>
        </div>
        <div style="font-size: 10px; color: rgba(255, 255, 255, 0.64)">
          单位：次
        </div>
      </div>
      <div
        style="display: flex; align-items: center; padding: 0 8.5px 0 21.5px"
      >
        <div
          style="
            width: 3.5px;
            height: 3.5px;
            background-color: #da6136;
            border-radius: 50%;
            flex: none;
          "
        ></div>
        <div style="background-color: #1a3d41; height: 1px; flex: 1"></div>
        <div
          style="
            width: 3.5px;
            height: 3.5px;
            background-color: #da6136;
            border-radius: 50%;
            flex: none;
          "
        ></div>
      </div>
      <div style="padding: 0 10px 0 20px">
        <div style="display: flex; align-items: center; height: 36px">
          <div
            style="width: 17px; height: 21px; margin-right: 9.5px; color: #fff"
          >
            1
          </div>
          <div style="font-size: 12px; color: #fff; margin-right: 10px">
            太原市
          </div>
          <div
            style="
              height: 9px;
              flex: 1;
              background-color: #28f1ff;
              margin-right: 4.5px;
            "
          ></div>
          <div
            style="
              height: 9px;
              width: 4px;
              background-color: #da6136;
              margin-right: 5px;
            "
          ></div>
          <div style="font-size: 12px; color: #fff; font-family: 'Digital'">
            98
          </div>
          <div style="font-size: 12px; color: #fff; font-family: 'Digital'">
            次
          </div>
        </div>
        <div style="display: flex; align-items: center; height: 36px">
          <div
            style="width: 17px; height: 21px; margin-right: 9.5px; color: #fff"
          >
            2
          </div>
          <div style="font-size: 12px; color: #fff; margin-right: 10px">
            大同市
          </div>
          <div
            style="
              height: 9px;
              flex: 0.8;
              background-color: #28f1ff;
              margin-right: 4.5px;
            "
          ></div>
          <div
            style="
              height: 9px;
              width: 4px;
              background-color: #da6136;
              margin-right: 5px;
            "
          ></div>
          <div style="font-size: 12px; color: #fff; font-family: 'Digital'">
            98
          </div>
          <div style="font-size: 12px; color: #fff; font-family: 'Digital'">
            次
          </div>
        </div>
        <div style="display: flex; align-items: center; height: 36px">
          <div
            style="width: 17px; height: 21px; margin-right: 9.5px; color: #fff"
          >
            3
          </div>
          <div style="font-size: 12px; color: #fff; margin-right: 10px">
            晋中市
          </div>
          <div
            style="
              height: 9px;
              flex: 0.6;
              background-color: #28f1ff;
              margin-right: 4.5px;
            "
          ></div>
          <div
            style="
              height: 9px;
              width: 4px;
              background-color: #da6136;
              margin-right: 5px;
            "
          ></div>
          <div style="font-size: 12px; color: #fff; font-family: 'Digital'">
            98
          </div>
          <div style="font-size: 12px; color: #fff; font-family: 'Digital'">
            次
          </div>
        </div>
        <div style="display: flex; align-items: center; height: 36px">
          <div
            style="width: 17px; height: 21px; margin-right: 9.5px; color: #fff"
          >
            4
          </div>
          <div style="font-size: 12px; color: #fff; margin-right: 10px">
            阳泉市
          </div>
          <div
            style="
              height: 9px;
              flex: 0.4;
              background-color: #28f1ff;
              margin-right: 4.5px;
            "
          ></div>
          <div
            style="
              height: 9px;
              width: 4px;
              background-color: #da6136;
              margin-right: 5px;
            "
          ></div>
          <div style="font-size: 12px; color: #fff; font-family: 'Digital'">
            98
          </div>
          <div style="font-size: 12px; color: #fff; font-family: 'Digital'">
            次
          </div>
        </div>
        <div style="display: flex; align-items: center; height: 36px">
          <div
            style="width: 17px; height: 21px; margin-right: 9.5px; color: #fff"
          >
            5
          </div>
          <div style="font-size: 12px; color: #fff; margin-right: 10px">
            长治市
          </div>
          <div
            style="
              height: 9px;
              flex: 0.2;
              background-color: #28f1ff;
              margin-right: 4.5px;
            "
          ></div>
          <div
            style="
              height: 9px;
              width: 4px;
              background-color: #da6136;
              margin-right: 5px;
            "
          ></div>
          <div style="font-size: 12px; color: #fff; font-family: 'Digital'">
            98
          </div>
          <div style="font-size: 12px; color: #fff; font-family: 'Digital'">
            次
          </div>
        </div>
      </div>
      <div
        style="display: flex; align-items: center; padding: 0 8.5px 0 21.5px"
      >
        <div
          style="
            width: 3.5px;
            height: 3.5px;
            background-color: #da6136;
            border-radius: 50%;
            flex: none;
          "
        ></div>
        <div style="background-color: #1a3d41; height: 1px; flex: 1"></div>
        <div
          style="
            width: 3.5px;
            height: 3.5px;
            background-color: #da6136;
            border-radius: 50%;
            flex: none;
          "
        ></div>
      </div>
    </div>
  </Card>
</template>
<style scoped></style>
