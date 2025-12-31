<!-- 今日审核状态 -->
<script setup>
import Card from "./Card.vue";
import * as echarts from "echarts";
</script>

<template>
  <Card class="w-36" title="今日审核状态">
    <div
      style="
        display: flex;
        flex-direction: column;
        gap: 5px;
        height: 100%;
        justify-content: center;
        padding-left: 12.5px;
      "
    >
      <div style="display: flex; gap: 8.5px">
        <div style="width: 66px; height: 35px"></div>
        <div
          style="
            width: 75px;
            height: 35px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #fff;
            font-size: 14px;
          "
        >
          临时空域
        </div>
        <div
          style="
            width: 75px;
            height: 35px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #fff;
            font-size: 14px;
          "
        >
          长期计划
        </div>
        <div
          style="
            width: 75px;
            height: 35px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #fff;
            font-size: 14px;
          "
        >
          次日计划
        </div>
      </div>
      <div style="display: flex; gap: 8.5px">
        <div
          style="
            width: 66px;
            height: 35px;
            display: flex;
            align-items: center;
            justify-content: center;
            background: rgba(107, 217, 141, 0.2);
            color: #6bd98d;
            font-size: 14px;
            border: 1px solid #79bc8e;
          "
        >
          通过
        </div>
        <div
          style="
            width: 75px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #28f1ff;
            font-size: 24px;
            font-family: 'Digital';
            background-image: url('../../public/grid-bg-light.png');
            background-position: center;
            background-size: cover;
            background-repeat: no-repeat;
          "
        >
          12
        </div>
        <div
          style="
            width: 75px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #28f1ff;
            font-size: 24px;
            font-family: 'Digital';
            background-image: url('../../public/grid-bg-light.png');
            background-position: center;
            background-size: cover;
            background-repeat: no-repeat;
          "
        >
          8
        </div>
        <div
          style="
            width: 75px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #28f1ff;
            font-size: 24px;
            font-family: 'Digital';
            background-image: url('../../public/grid-bg-light.png');
            background-position: center;
            background-size: cover;
            background-repeat: no-repeat;
          "
        >
          4
        </div>
      </div>
      <div style="display: flex; gap: 8.5px">
        <div
          style="
            width: 66px;
            height: 35px;
            display: flex;
            align-items: center;
            justify-content: center;
            background: rgba(238, 62, 62, 0.2);
            color: #ee3e3e;
            font-size: 14px;
            border: 1px solid #ee3e3e;
          "
        >
          不通过
        </div>
        <div
          style="
            width: 75px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #28f1ff;
            font-size: 24px;
            font-family: 'Digital';
            background-image: url('../../public/grid-bg-dark.png');
            background-position: center;
            background-size: cover;
            background-repeat: no-repeat;
          "
        >
          2
        </div>
        <div
          style="
            width: 75px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #28f1ff;
            font-size: 24px;
            font-family: 'Digital';
            background-image: url('../../public/grid-bg-dark.png');
            background-position: center;
            background-size: cover;
            background-repeat: no-repeat;
          "
        >
          1
        </div>
        <div
          style="
            width: 75px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #28f1ff;
            font-size: 24px;
            font-family: 'Digital';
            background-image: url('../../public/grid-bg-dark.png');
            background-position: center;
            background-size: cover;
            background-repeat: no-repeat;
          "
        >
          1
        </div>
      </div>
      <div style="display: flex; gap: 8.5px">
        <div
          style="
            width: 66px;
            height: 35px;
            display: flex;
            align-items: center;
            justify-content: center;
            background: rgba(251, 154, 85, 0.2);
            color: #fb9a55;
            font-size: 14px;
            border: 1px solid #fb9a55;
          "
        >
          待分发
        </div>
        <div
          style="
            width: 75px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #28f1ff;
            font-size: 24px;
            font-family: 'Digital';
            background-image: url('../../public/grid-bg-light.png');
            background-position: center;
            background-size: cover;
            background-repeat: no-repeat;
          "
        >
          6
        </div>
        <div
          style="
            width: 75px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #28f1ff;
            font-size: 24px;
            font-family: 'Digital';
            background-image: url('../../public/grid-bg-light.png');
            background-position: center;
            background-size: cover;
            background-repeat: no-repeat;
          "
        >
          3
        </div>
        <div
          style="
            width: 75px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #28f1ff;
            font-size: 24px;
            font-family: 'Digital';
            background-image: url('../../public/grid-bg-light.png');
            background-position: center;
            background-size: cover;
            background-repeat: no-repeat;
          "
        >
          4
        </div>
      </div>
      <div style="display: flex; gap: 8.5px">
        <div
          style="
            width: 66px;
            height: 35px;
            display: flex;
            align-items: center;
            justify-content: center;
            background: rgba(40, 241, 255, 0.2);
            color: #28f1ff;
            font-size: 14px;
            border: 1px solid #28f1ff;
          "
        >
          审批中
        </div>
        <div
          style="
            width: 75px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #28f1ff;
            font-size: 24px;
            font-family: 'Digital';
            background-image: url('../../public/grid-bg-dark.png');
            background-position: center;
            background-size: cover;
            background-repeat: no-repeat;
          "
        >
          5
        </div>
        <div
          style="
            width: 75px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #28f1ff;
            font-size: 24px;
            font-family: 'Digital';
            background-image: url('../../public/grid-bg-dark.png');
            background-position: center;
            background-size: cover;
            background-repeat: no-repeat;
          "
        >
          2
        </div>
        <div
          style="
            width: 75px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #28f1ff;
            font-size: 24px;
            font-family: 'Digital';
            background-image: url('../../public/grid-bg-dark.png');
            background-position: center;
            background-size: cover;
            background-repeat: no-repeat;
          "
        >
          3
        </div>
      </div>
    </div>
  </Card>
</template>
<style scoped></style>
