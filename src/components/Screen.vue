<script setup>
import { onMounted } from "vue";
import Card from "./Card.vue";
import * as echarts from "echarts";
import FlightStatusOverview from "./FlightStatusOverview.vue";
import FlightPlanApplications from "./FlightPlanApplications.vue";
import FlightTrafficChart from "./FlightTrafficChart.vue";
import ApprovalStatusOverview from "./ApprovalStatusOverview.vue";
import AircraftMonthlyOperations from "./AircraftMonthlyOperations.vue";
import ExecutedMissionTypes from "./ExecutedMissionTypes.vue";
import ApprovedAirspaceStatistics from "./ApprovedAirspaceStatistics.vue";
import SubmittedPlanStatistics from "./SubmittedPlanStatistics.vue";
import IntelligenceDataPanel from "./IntelligenceDataPanel.vue";
import MeteorologicalDataPanel from "./MeteorologicalDataPanel.vue";
import WarningInfo from "./WarningInfo.vue";
import WeatherTimeBar from "./WeatherTimeBar.vue";

onMounted(() => {
  const screen = document.getElementById("screen");
  const scaleX = window.innerWidth / 3440;
  const scaleY = window.innerHeight / 1032;
  const scale = Math.min(scaleX, scaleY);
  screen.style.transform = `scale(${scale})`;
});
</script>
<template>
  <div id="viewport">
    <div id="screen">
      <div class="top-background"></div>
      <div class="left">
        <div class="banner">
          <div class="logo"></div>
          <div class="banner-text">
            <div class="banner-title">山西省低空交通管理平台</div>
            <div class="banner-subtitle">
              Shanxi Provice Low-Altitude Traffic Management Platform
            </div>
          </div>
        </div>
        <div class="rows">
          <div class="row">
            <FlightStatusOverview />
            <FlightPlanApplications />
          </div>

          <div class="row">
            <FlightTrafficChart />
            <ApprovalStatusOverview />
          </div>

          <div class="row">
            <AircraftMonthlyOperations />
            <ExecutedMissionTypes />
          </div>
        </div>
      </div>
      <div class="center">
        <Card title="低空交通全局态势图"></Card>
      </div>
      <div class="right">
        <WeatherTimeBar />
        <WarningInfo />
        <div class="rows">
          <div class="row">
            <ApprovedAirspaceStatistics />
            <SubmittedPlanStatistics />
          </div>
          <div class="row">
            <IntelligenceDataPanel />
          </div>
          <div class="row">
            <MeteorologicalDataPanel />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<style>
body,
html {
  margin: 0;
  padding: 0;
}
#screen {
  width: 3440px;
  height: 1032px;
  transform-origin: left top;
  background-color: #011a3e;
  position: relative;
}
.top-background {
  height: 83px;
  width: 3440px;
  top: 0;
  left: 0;
  background-position: center;
  background-image: url(/public/top-background.png);
  background-size: contain;
  background-repeat: no-repeat;
  position: absolute;
  z-index: 100;
}
.left {
  height: 1032px;
  width: 946px;
  padding-top: 8px;
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  flex-direction: column;
  box-sizing: border-box;
}
.banner {
  height: 81px;
  display: flex;
  box-sizing: border-box;
  padding: 12.5px 11.5px;
  align-items: center;
}
.logo {
  width: 50px;
  height: 50px;
  background-image: url("../../public/logo.png");
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  margin-right: 12.5px;
}
.banner-title {
  color: #fff;
  font-size: 30px;
  font-weight: 700;
}
.banner-subtitle {
  color: gray;
  font-size: 20px;
  font-weight: 500;
}
.rows {
  flex: 1;
  display: flex;
  flex-direction: column;
}
.row {
  flex: 1;
  display: flex;
  padding: 0 8px 8px 12px;
}
.center {
  height: 1032px;
  width: 1548px;
  position: absolute;
  top: 0;
  left: 946px;
}
.right {
  height: 1032px;
  width: 946px;
  position: absolute;
  top: 0;
  right: 0;
}
</style>
