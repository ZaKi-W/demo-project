<script setup>
import * as echarts from 'echarts';
import Card from './Card.vue';
import { onMounted } from 'vue';

const data = [
  { name: 'A类', value: 40, color: '#00ffff' },
  { name: 'B类', value: 30, color: '#3ba1ff' },
  { name: 'C类', value: 20, color: '#36cfc9' },
  { name: 'D类', value: 10, color: '#9254de' },
  { name: 'E类', value: 13, color: '#2234de' },
  { name: 'F类', value: 50, color: '#4254de' },
  { name: 'G类', value: 25, color: '#7254de' },
]

const option1 = {
    series: [
        {
        type: 'pie',
        radius: ['65%', '80%'],
        center: ['50%', '50%'],
        padAngle: 5,
        itemStyle: {
            borderRadius: 4
        },
        data: data.map(d => ({
            value: d.value,
            name: d.name,
            itemStyle: { color: d.color }
        })),
        label: { show: false },
        labelLine: { show: false }
        }
    ],
    graphic: [
        {
            type: 'circle',
            left: 'center',
            top: 'center',
            shape: { r: 60 },
            style: {
                fill: {
                type: 'radial',
                x: 0.5,
                y: 0.5,
                r: 0.5,
                colorStops: [
                    { offset: 0, color: 'rgba(0,255,255,0.05)' },
                    { offset: 0.8, color: 'rgba(0,255,255,0.3)' },
                    { offset: 1, color: 'rgba(0,255,255,0.8)' }
                ]
                }
            },
            silent: true
        },
        {
        type: 'group',
        left: 'center',
        top: 'center',
        silent: true,
        children: [
            {
                type: 'text',
                left: -10,
                top: -15,
                style: {
                    text: '75',
                    fill: '#00ffff',
                    fontSize: 32,
                    fontFamily: 'Digital',
                    textAlign: 'center'
                }
            },
            {
                type: 'text',
                top: 0,
                left: 30,
                style: {
                    text: '架次',
                    fill: '#8fdfff',
                    fontSize: 12,
                    textAlign: 'center'
                }
            },
            {
                type: 'text',
                top: 25,
                left: -15,
                style: {
                    text: '目前正在执行',
                    fill: '#8fdfff',
                    fontSize: 12,
                    textAlign: 'center'
                }
            }
        ]
        }
    ]
}

onMounted(() => {
    const charts1 = echarts.init(document.getElementById('demoId1'));
    charts1.setOption(option1);
})

</script>
<template>
<Card class="w-50 mr-8" title="今日飞行动态">
    <div style="height: 100%; display: flex;">
        <div id="demoId1" style="flex: 1; height: 100%;"></div>
        <div class="legend-box">
            <div class="legend-item" v-for="item in data">
                <div class="item-dot" :style="`background-color: ${item.color};`"></div>
                <div class="legend-title">{{ item.name }}</div>
                <div class="legend-percent">{{ item.value }}%</div>
                <div class="legend-value">{{ item.value }}</div>
            </div>
        </div>
    </div>
</Card>
</template>
<style scoped>
.legend-box {
    flex: 1;
    padding-top: 40px;
    padding-left: 30px;
}
.legend-item {
    display: flex;
    align-items: center;
    margin-bottom: 18px;
}
.item-dot {
    width: 6px;
    height: 6px;
    border-radius: 50%;
    margin-right: 8.5px;
}
.legend-title {
    font-size: 12px;
    color: #FFF;
    margin-right: 45px;
}
.legend-percent {
    font-size: 12px;
    color: #FFF;
    margin-right: 24px;
    width: 20px;
}
.legend-value {
    font-size: 12px;
    color: #FFF;
    text-align: right;
}
</style>