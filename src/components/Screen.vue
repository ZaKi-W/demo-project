<script setup>
import { onMounted } from 'vue';
import Card from './Card.vue';
import * as echarts from 'echarts';
import FlightStatusOverview from './FlightStatusOverview.vue';

const data = [
  { name: 'A类', value: 40, color: '#00ffff' },
  { name: 'B类', value: 30, color: '#3ba1ff' },
  { name: 'C类', value: 20, color: '#36cfc9' },
  { name: 'D类', value: 10, color: '#9254de' },
  { name: 'E类', value: 13, color: '#2234de' },
  { name: 'F类', value: 50, color: '#4254de' },
  { name: 'G类', value: 25, color: '#7254de' },
]

    onMounted(() => {
        const screen = document.getElementById('screen');
        const scaleX = window.innerWidth / 3440
        const scaleY = window.innerHeight / 1032
        const scale = Math.min(scaleX, scaleY)
        screen.style.transform = `scale(${scale})`

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
        const option2 = {
            series: [
                {
                type: 'pie',
                radius: ['60%', '98%'], // 增大内外半径比例
                center: ['50%', '50%'],
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
                            text: '13',
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
                            text: '条',
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
                            text: '当日申请',
                            fill: '#8fdfff',
                            fontSize: 12,
                            textAlign: 'center'
                        }
                    }
                ]
                }
            ]
        }
        const data3 = [20, 280, 70, 232, 256, 76, 135, 162.2, 32.6, 20.0, 6.4, 3.3, 40, 210, 120, 180, 190, 85, 101, 77, 250, 67, 99];
        const option31 = {
            tooltip: {
                trigger: 'axis',
                axisPointer: {
                    type: 'cross',
                    crossStyle: {
                        color: '#999'
                    }
                }
            },
            grid: {
                left: '3%',
                right: '3%',
                top: '10%',
                bottom: '0%',
                containLabel: true
            },
            xAxis: [
                {
                    type: 'category',
                    data: [
                        '00', '01', '02', '03', '04', '05', '06', '07', '08', '09', '10', '11',
                        '12', '13', '14', '15', '16', '17', '18', '19', '20', '21', '22'
                    ],
                    axisTick: { alignWithLabel: true }
                }
            ],
            yAxis: [
                {
                    type: 'value',
                    min: 0,
                    max: 300,
                    interval: 50
                }
            ],
            series: [
                {
                    name: 'Evaporation',
                    type: 'bar',
                    barWidth: '50%',
                    tooltip: {
                        valueFormatter: function (value) {
                            return value + ' ml';
                        }
                    },
                    data: data3
                },
                {
                    name: 'Temperature',
                    type: 'line',
                    symbolSize: 10,
                    lineStyle: {
                        width: 3
                    },
                    tooltip: {
                        valueFormatter: function (value) {
                            return value + ' °C';
                        }
                    },
                    data: data3
                }
            ]
        }


        // 把柱子的宽度缩窄一半
        const offsetX = 9
        const offsetY = 5
        const CubeLeft = echarts.graphic.extendShape({
            shape: {
                x: 0,
                y: 0,
            },
            buildPath: function (ctx, shape) {
                const xAxisPoint = shape.xAxisPoint
                const c0 = [shape.x, shape.y]
                const c1 = [shape.x - offsetX, shape.y - offsetY]
                const c2 = [xAxisPoint[0] - offsetX, xAxisPoint[1] - offsetY]
                const c3 = [xAxisPoint[0], xAxisPoint[1]]
                ctx
                    .moveTo(c0[0], c0[1])
                    ?.lineTo(c1[0], c1[1])
                    .lineTo(c2[0], c2[1])
                    .lineTo(c3[0], c3[1])
                    .closePath()
            },
        })

        // 绘制右侧面
        const CubeRight = echarts.graphic.extendShape({
        shape: {
            x: 0,
            y: 0,
        },
        buildPath: function (ctx, shape) {
            const xAxisPoint = shape.xAxisPoint
            const c1 = [shape.x, shape.y]
            const c2 = [xAxisPoint[0], xAxisPoint[1]]
            const c3 = [xAxisPoint[0] + offsetX, xAxisPoint[1] - offsetY]
            const c4 = [shape.x + offsetX, shape.y - offsetY]
            ctx
                .moveTo(c1[0], c1[1])
                ?.lineTo(c2[0], c2[1])
                .lineTo(c3[0], c3[1])
                .lineTo(c4[0], c4[1])
                .closePath()
        },
        })

        // 绘制顶面
        const CubeTop = echarts.graphic.extendShape({
            shape: {
                x: 0,
                y: 0,
            },
            buildPath: function (ctx, shape) {
                const c1 = [shape.x, shape.y]
                const c2 = [shape.x + offsetX, shape.y - offsetY]
                const c3 = [shape.x, shape.y - offsetY * 2]
                const c4 = [shape.x - offsetX, shape.y - offsetY]
                ctx
                    .moveTo(c1[0], c1[1])
                    ?.lineTo(c2[0], c2[1])
                    .lineTo(c3[0], c3[1])
                    .lineTo(c4[0], c4[1])
                    .closePath()
            },
        })

        // 注册三个面图形
        echarts.graphic.registerShape('CubeLeft', CubeLeft)
        echarts.graphic.registerShape('CubeRight', CubeRight)
        echarts.graphic.registerShape('CubeTop', CubeTop)

        const option3 = {
            backgroundColor:'#022051',
            tooltip: {
                trigger: 'axis',
                axisPointer: {
                    type: 'shadow',
                },
            },
            grid: {
                left: '2%',
                right: '4%',
                bottom: '15%', // 留出底部滚动条位置
                top: '15%',
                containLabel: true,
            },
            // 调整图像x轴
            xAxis: {
                data: [
                    '00', '01', '02', '03', '04', '05', '06', '07', '08', '09', '10', '11',
                    '12', '13', '14', '15', '16', '17', '18', '19', '20', '21', '22'
                ],
                axisTick: {
                    show: false,
                },
                axisLabel: {
                    show: true,
                    color: '#333',
                    //  rotate: 30,
                    textStyle: {
                        color: 'rgba(189, 217, 255, 1)',
                        fontSize: 14,
                    },
                },
                axisLine: {
                    show: true,
                    lineStyle: {
                        color: 'rgba(189, 217, 255, 1)',
                    },
                },
            },
            //调整图像y轴
            yAxis: [
                {
                    type: 'value',
                    alignTicks: true,
                    nameTextStyle: {
                        color: 'rgba(189, 217, 255, 1)',
                        fontSize: 14,
                    },
                    lineStyle: {
                        show: 'none',
                        type: 'dashed',
                    },

                    axisLine: {
                        show: true,
                        lineStyle: {
                        color: 'rgba(189, 217, 255, 1)',
                        },
                    },
                    axisTick: { show: false },
                    axisLabel: {
                        show: true,
                        color: 'rgba(189, 217, 255, 1)',
                        fontSize: 14,
                    },
                    splitLine: {
                        show: true,
                        lineStyle: {
                        color: 'rgba(83, 132, 201, 1)', // 极淡的分割线
                        type: 'solid',
                        },
                    },
                },
            ],
            series: [
                {
                    type: 'custom',
                    yAxisIndex: 0,
                    renderItem: (_, api) => {
                        const location = api.coord([api.value(0), api.value(1)])
                        return {
                        type: 'group',
                        children: [
                            {
                                type: 'CubeLeft',
                                shape: {
                                    api,
                                    xValue: api.value(0),
                                    yValue: api.value(1),
                                    x: location[0],
                                    y: location[1],
                                    xAxisPoint: api.coord([api.value(0), 0]),
                                },
                                style: {
                                    fill: new echarts.graphic.LinearGradient(
                                    0,
                                    0,
                                    0,
                                    1, // 坐标：从上(0,0) 到 下(0,1)，即 CSS 的 180deg
                                    [
                                        {
                                            offset: 0, // 对应 0%
                                            color: 'rgba(4, 45, 209, .5)',
                                        },
                                        {
                                            offset: 1, // 对应 100%
                                            color: 'rgba(102, 165, 242, .5)',
                                        },
                                    ]
                                    ),
                                },
                            },
                            {
                                type: 'CubeRight',
                                shape: {
                                    api,
                                    xValue: api.value(0),
                                    yValue: api.value(1),
                                    x: location[0],
                                    y: location[1],
                                    xAxisPoint: api.coord([api.value(0), 0]),
                                },
                                style: {
                                    fill: new echarts.graphic.LinearGradient(
                                    0,
                                    0,
                                    0,
                                    1, // 坐标：(x1, y1) -> (x2, y2)，从上(0,0)到下(0,1)
                                    [
                                        {
                                            offset: 0, // 0% 处的颜色
                                            color: 'rgba(31, 72, 241, .5)',
                                        },
                                        {
                                            offset: 1, // 100% 处的颜色
                                            color: 'rgba(97, 168, 255, .5)',
                                        },
                                    ]
                                    ),
                                },
                            },
                            {
                                type: 'CubeTop',
                                shape: {
                                    api,
                                    xValue: api.value(0),
                                    yValue: api.value(1),
                                    x: location[0],
                                    y: location[1],
                                    xAxisPoint: api.coord([api.value(0), 0]),
                                },
                                style: {
                                    // fill: '#6BB6FF',
                                    fill: new echarts.graphic.LinearGradient(
                                    // 坐标：(x1, y1, x2, y2)
                                    // 161.62度大约是从 "左上(略偏右)" 指向 "右下"
                                    // 这里使用近似值模拟 161度 (x从0到0.33, y从0到1)
                                    0,
                                    0,
                                    0.33,
                                    1,
                                    [
                                        {
                                            offset: 0,
                                            color: 'rgba(145, 231, 255, 1)', // 0% 处的颜色
                                        },
                                        {
                                            offset: 0.1597,
                                            color: 'rgba(0, 187, 255, 1)', // 15.97% 处的颜色
                                        },
                                        {
                                            offset: 1,
                                            color: 'rgba(0, 125, 184, 1)', // 100% 处的颜色
                                        },
                                    ]
                                    ),
                                },
                            },
                        ],
                        }
                    },
                    data: data3,
                },
                {
                    type: 'bar',
                    barWidth: 10, // 原来20，缩窄一半
                    label: {
                        show: false,
                        position: 'top',
                        formatter: e => {
                        return e.value + '%'
                        },
                        fontSize: 16,
                        fontWeight: 700,
                        color: '#333',
                        offset: [0, -15],
                    },
                    // yAxisIndex: 0,
                    itemStyle: {
                        color: 'transparent',
                    },
                    tooltip: { show: false },
                    data: data3,
                },
                {
                    name: 'Temperature',
                    type: 'line',
                    smooth: true,
                    symbolSize: 0,
                    lineStyle: {
                        width: 2,
                        color: '#29F1FA'
                    },
                    tooltip: {
                        valueFormatter: function (value) {
                            return value;
                        }
                    },
                    data: data3
                }
            ],
        };

        const data4 = [150, 50, 230, 50, 150, 100]
        const option4 = {
            grid: {
                left: '3%',
                right: '4%',
                bottom: '3%',
                top: '5%',
                containLabel: true
            },
            tooltip: {
                trigger: 'axis',
            },
            xAxis: {
                type: 'category',
                data: ['1月', '2月', '3月', '4月', '5月', '6月'],
                axisLine: {
                    show: true,
                    lineStyle: {
                        color: "#BAE7FF",
                        width: 1,
                        type: "solid"
                    }
                },
                axisTick: {
                    show: false
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
                        color: 'rgba(186, 231, 255, 0.2)',
                        type: "dashed"
                    }
                },
                axisLabel: {
                    show: true,
                    textStyle: {
                        color: 'white', //更改坐标轴文字颜色
                    }
                },
                axisTick: {
                    show: false
                }
            },
            series: [{
                name: '架次',
                type: 'pictorialBar',
                barCategoryGap: '40%',
                symbol: 'triangle',
                barWidth: '100%',
                symbol: 'path://M0,10 L10,10 C5.5,10 5.5,5 5,0 C4.5,5 4.5,10 0,10 z',
                itemStyle: {
                    normal: {
                        opacity: 0.8,
                        // color:'RGBA(133, 255, 105, 1)',
                        color: new echarts.graphic.LinearGradient(0, 1, 0, 0, [{
                            offset: 0,
                            color: "rgba(54, 144, 253, 1)" // 0% 处的颜色
                        }, {
                            offset: 1,
                            color: "rgba(40, 241, 255, 1)" // 60% 处的颜色
                        }, {
                            offset: 1,
                            color: "rgba(40, 241, 255, 1)" // 100% 处的颜色
                        }], false),
                        borderColor: '#15B1FF', // 边框颜色
                        borderWidth: 2 ,// 边框宽度
                        borderRadius:[100,100],
                    },
                    emphasis: {
                        opacity: 1
                    }
                },
                data: data4,
                z: 10
            }]
        };

        let chartData = [{
            name: '类型1',
            value: 123
            }, {
            name: '类型2',
            value: 262
            }, {
            name: '类型3',
            value: 210
            }, {
            name: '类型4',
            value: 170
            }, {
            name: '类型5',
            value: 190
        }];

        let dataArr = chartData.map(e => e.value);
        let max = Math.max(...dataArr) * 1.2;
        let indicatorArr = chartData.map(e => {
            return {
                text: e.name,
                max
            }
        });
        const option5 = {
            tooltip: {
                trigger: 'item',
            },
            radar: {
                radius: '50%',
                indicator: indicatorArr,
                splitNumber: 5,
                splitLine: {
                    show: true,
                    lineStyle: {
                        width: 2,
                        color: ['#102261', '#102261', '#102261', '#223876', '#102261', '#C0C0C0'], // 分隔区域边框
                        opacity: 0.3 // 边框透明度
                    }
                },
                splitArea: { // 坐标轴在 grid中的分隔区域，默认不显示
                    show: true,
                    areaStyle: { // 分隔区域的样式设置
                        color: ['rgba(0, 78, 156, 0.50)', 'rgba(0, 31, 62, 1)', 'rgba(0, 78, 156, 0.50)', 'rgba(0, 31, 62, 1)', 'rgba(0, 78, 156, 0.50)'], // 分隔区域颜色数组

                    }
                },
                axisLine: {
                    lineStyle: {
                        color: '#C0C0C0',
                        width: 1,
                        opacity: 0.2
                    }
                },
                name: { // 雷达图每个指示器的名称
                    textStyle: {
                        color: '#fff'
                    }
                },
            },
            series: [{
                type: 'radar',
                symbolSize: 0,
                areaStyle: {
                    color: 'rgba(21, 147, 231, .7)'
                },
                lineStyle: {
                    width: 1,
                    color: 'rgba(24,167,188, 1)'
                },
                data: [{
                    value: dataArr,
                }]
            }]
        };



        const data6 = [
            {name: '航线1', value: 38},
            {name: '航线2', value: 65},
            {name: '航线3', value: 44},
            {name: '航线4', value: 52},
            {name: '航线5', value: 81},
            {name: '航线6', value: 250},
            {name: '航线7', value: 100},
            {name: '航线8', value: 80},
        ]
        const maxArray = new Array(data6.map(item => item.value).length).fill(Math.max(...(data6.map(item => item.value))));
        const points = data6.map(item => {
            let obj = {
                name: 'top-line',
                xAxis: item.name,
                yAxis: item.value,
                symbol: 'rect',
                symbolSize: [17, 3],
                itemStyle: {
                    color: 'rgba(255, 255, 255, 1)',
                    shadowColor: 'rgba(255, 255, 255, 1)',
                    shadowBlur: 10,
                    shadowOffsetY: -3
                }
            }
            return obj
        })

        const option6 = {
            tooltip: {
                show: true,
                trigger: "item",
                backgroundColor: 'rgba(21, 154, 255, 0.32)',
                textStyle: {
                color: '#fff'
                },
            },
            backgroundColor: 'rgba(8, 30, 80, 1)',
            grid: {
                top: "13%",
                left: "3%",
                right: "4%",
                bottom: "3%",
                containLabel: true
            },
            // 添加第二个 xAxis 用于折线图偏移
            xAxis: {
                type: "category",
                data: data6.map(item => item.name),
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
                type: 'value',
                // nameGap: 35,
                nameTextStyle: {
                    color: 'rgba(162, 217, 255, 1)',
                    fontSize: 12
                },
                // axisLine: {
                //     lineStyle: {
                //         color: '#3C6579'
                //     }
                // },
                axisTick: {
                    show: false
                },
                splitLine: {
                    lineStyle: {
                        color: '#173055',
                        // type: 'dashed'
                    }
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
                    data: data6.map(item => item.value),
                    itemStyle: {
                        borderRadius: [0, 0, 0, 0],
                        color: {
                            type: 'linear',
                            x: 0, y: 0, x2: 0, y2: 1,
                            colorStops: [
                                { offset: 0, color: 'rgba(86, 176, 254, 1)' },
                                { offset: 0.1, color: 'rgba(68, 163, 255, 1)' },
                                { offset: 1, color: 'rgba(46, 140, 255, 1)' }
                            ],
                            global: false
                        }
                    }
                },
                {
                    name: "",
                    barGap: '-150%',
                    type: 'bar',
                    z: 0,
                    data: maxArray,
                    barWidth: 12,
                    itemStyle: {
                        normal: {
                            color: 'rgba(11, 36, 89, 0.8)'
                        }
                    },
                    tooltip: {
                        show: false
                    }
                },
            ]
        };





        const charts1 = echarts.init(document.getElementById('demoId1'));
        charts1.setOption(option1);
        const charts2 = echarts.init(document.getElementById('demoId2'));
        charts2.setOption(option2);
        const charts3 = echarts.init(document.getElementById('demoId3'));
        charts3.setOption(option3);
        const charts4 = echarts.init(document.getElementById('demoId4'));
        charts4.setOption(option4);
        const charts5 = echarts.init(document.getElementById('demoId5'));
        charts5.setOption(option5);
        const charts6 = echarts.init(document.getElementById('demoId6'));
        charts6.setOption(option6);
    })
    // demoId
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
                        <div class="banner-subtitle">Shanxi Provice Low-Altitude Traffic Management Platform</div>
                    </div>
                </div>
                <div class="rows">
                    <div class="row">
                        <FlightStatusOverview />
                        <!-- <Card class="w-50 mr-8" title="今日飞行动态">
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
                        </Card> -->
                        <Card class="w-50" title="今日申请计划">
                            <div style="height: 100%; display: flex;">
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
                                <div id="demoId2" style="flex: 1; height: 100%;"></div>
                                <div class="legend-box">
                                    <div class="legend-item" v-for="item in data">
                                        <div class="item-dot" :style="`background-color: ${item.color};`"></div>
                                        <div class="legend-title">{{ item.name }}</div>
                                        <div class="legend-percent">{{ item.value }}%</div>
                                    </div>
                                </div>
                            </div>
                        </Card>
                    </div>

                    <div class="row">
                        <Card class="w-60 mr-8" title="航班流量">
                            <div style="height: 100%; flex: 1; display: flex; flex-direction: column;">
                                <div style="height: 60px; margin-bottom: 8px; display: flex; flex-direction: column;">
                                    <div style="padding-left: 30px; padding-top: 10px; font-size: 10px; color: #FFF;">飞行总时长</div>
                                    <div style="display: flex; align-items: center; justify-content: space-between; padding-left: 25px; padding-right: 20px;">
                                        <div style="display: flex; align-items: center; padding-top: 10px;">
                                            <div style="font-size: 24px; color: #00ffff; font-family: 'Digital'; margin-right: 10px;">2430</div>
                                            <div style="font-size: 10px; color: #FFF;">小时</div>
                                        </div>
                                        <div style="color: #FFFFFFA3; font-size: 10px;">单位：小时</div>
                                    </div>
                                </div>
                                <div id="demoId3" style="height: 100%;"></div>
                            </div>
                        </Card>
                        <Card class="w-36" title="今日审核状态">
                        <!-- INSERT_YOUR_CODE -->
                        <div style="display: flex; flex-direction: column; gap: 5px; height: 100%; justify-content: center; padding-left: 12.5px;">
                            <!-- Header Row -->
                            <div style="display: flex; gap: 8.5px;">
                                <div style="width: 66px; height: 35px;"></div>
                                <div style="width: 75px; height: 35px; display: flex; align-items: center; justify-content: center; color: #FFF; font-size: 14px;">临时空域</div>
                                <div style="width: 75px; height: 35px; display: flex; align-items: center; justify-content: center; color: #FFF; font-size: 14px;">长期计划</div>
                                <div style="width: 75px; height: 35px; display: flex; align-items: center; justify-content: center; color: #FFF; font-size: 14px;">次日计划</div>
                            </div>
                            <!-- 第一行：通过 -->
                            <div style="display: flex; gap: 8.5px;">
                                <div style="width: 66px; height: 35px; display: flex; align-items: center; justify-content: center;
                                    background: rgba(107,217,141,0.2); color: #6BD98D; font-size: 14px;
                                    border: 1px solid #79BC8E;">
                                    通过
                                </div>
                                <div style="width: 75px; height: 40px; display: flex; align-items: center; justify-content: center;
                                    color: #28F1FF; font-size: 24px; font-family: 'Digital';
                                    background-image: url('../../public/grid-bg-light.png'); background-position: center; background-size: cover; background-repeat: no-repeat;">
                                    12
                                </div>
                                <div style="width: 75px; height: 40px; display: flex; align-items: center; justify-content: center;
                                    color: #28F1FF; font-size: 24px; font-family: 'Digital';
                                    background-image: url('../../public/grid-bg-light.png'); background-position: center; background-size: cover; background-repeat: no-repeat;">
                                    8
                                </div>
                                <div style="width: 75px; height: 40px; display: flex; align-items: center; justify-content: center;
                                    color: #28F1FF; font-size: 24px; font-family: 'Digital';
                                    background-image: url('../../public/grid-bg-light.png'); background-position: center; background-size: cover; background-repeat: no-repeat;">
                                    4
                                </div>
                            </div>
                            <!-- 第二行：不通过 -->
                            <div style="display: flex; gap: 8.5px;">
                                <div style="width: 66px; height: 35px; display: flex; align-items: center; justify-content: center;
                                    background: rgba(238,62,62,0.2); color: #EE3E3E; font-size: 14px;
                                    border: 1px solid #EE3E3E;">
                                    不通过
                                </div>
                                <div style="width: 75px; height: 40px; display: flex; align-items: center; justify-content: center;
                                    color: #28F1FF; font-size: 24px; font-family: 'Digital';
                                    background-image: url('../../public/grid-bg-dark.png'); background-position: center; background-size: cover; background-repeat: no-repeat;">
                                    2
                                </div>
                                <div style="width: 75px; height: 40px; display: flex; align-items: center; justify-content: center;
                                    color: #28F1FF; font-size: 24px; font-family: 'Digital';
                                    background-image: url('../../public/grid-bg-dark.png'); background-position: center; background-size: cover; background-repeat: no-repeat;">
                                    1
                                </div>
                                <div style="width: 75px; height: 40px; display: flex; align-items: center; justify-content: center;
                                    color: #28F1FF; font-size: 24px; font-family: 'Digital';
                                    background-image: url('../../public/grid-bg-dark.png'); background-position: center; background-size: cover; background-repeat: no-repeat;">
                                    1
                                </div>
                            </div>
                            <!-- 第三行：待分发 -->
                            <div style="display: flex; gap: 8.5px;">
                                <div style="width: 66px; height: 35px; display: flex; align-items: center; justify-content: center;
                                    background: rgba(251,154,85,0.2); color: #FB9A55; font-size: 14px;
                                    border: 1px solid #FB9A55;">
                                    待分发
                                </div>
                                <div style="width: 75px; height: 40px; display: flex; align-items: center; justify-content: center;
                                    color: #28F1FF; font-size: 24px; font-family: 'Digital';
                                    background-image: url('../../public/grid-bg-light.png'); background-position: center; background-size: cover; background-repeat: no-repeat;">
                                    6
                                </div>
                                <div style="width: 75px; height: 40px; display: flex; align-items: center; justify-content: center;
                                    color: #28F1FF; font-size: 24px; font-family: 'Digital';
                                    background-image: url('../../public/grid-bg-light.png'); background-position: center; background-size: cover; background-repeat: no-repeat;">
                                    3
                                </div>
                                <div style="width: 75px; height: 40px; display: flex; align-items: center; justify-content: center;
                                    color: #28F1FF; font-size: 24px; font-family: 'Digital';
                                    background-image: url('../../public/grid-bg-light.png'); background-position: center; background-size: cover; background-repeat: no-repeat;">
                                    4
                                </div>
                            </div>
                            <!-- 第四行：审批中 -->
                            <div style="display: flex; gap: 8.5px;">
                                <div style="width: 66px; height: 35px; display: flex; align-items: center; justify-content: center;
                                    background: rgba(40,241,255,0.2); color: #28F1FF; font-size: 14px;
                                    border: 1px solid #28F1FF;">
                                    审批中
                                </div>
                                <div style="width: 75px; height: 40px; display: flex; align-items: center; justify-content: center;
                                    color: #28F1FF; font-size: 24px; font-family: 'Digital';
                                    background-image: url('../../public/grid-bg-dark.png'); background-position: center; background-size: cover; background-repeat: no-repeat;">
                                    5
                                </div>
                                <div style="width: 75px; height: 40px; display: flex; align-items: center; justify-content: center;
                                    color: #28F1FF; font-size: 24px; font-family: 'Digital';
                                    background-image: url('../../public/grid-bg-dark.png'); background-position: center; background-size: cover; background-repeat: no-repeat;">
                                    2
                                </div>
                                <div style="width: 75px; height: 40px; display: flex; align-items: center; justify-content: center;
                                    color: #28F1FF; font-size: 24px; font-family: 'Digital';
                                    background-image: url('../../public/grid-bg-dark.png'); background-position: center; background-size: cover; background-repeat: no-repeat;">
                                    3
                                </div>
                            </div>
                        </div>
                        </Card>
                    </div>

                    <div class="row">
                        <Card class="w-60 mr-8" title="航空器月度执飞情况">
                            <div style="height: 100%; display: flex; padding-left: 15px; padding-top: 15px; box-sizing: border-box;">
                                <div style="height: 100%; padding-top: 10px;">
                                    <div style="display: flex; align-items: start; margin-bottom: 14.5px;">
                                        <div style="font-size: 14px; color: #FFF; width: 60px;">固定翼：</div>
                                        <div style="font-size: 24px; color: #28F1FF; width: 60px; text-align: right; font-family: 'Digital'; margin-right: 8.5px;">8000</div>
                                        <div style="font-size: 14px; color: #FFF; margin-right: 10px;">架次</div>
                                        <div style="width: 70px; height: 30px; background-image: url('../../public/small-card-bg.png'); background-position: center; background-size: contain; background-repeat: no-repeat;
                                            display: flex; justify-content: center; align-items: center;
                                        ">
                                            <div style="font-size: 10px; color: #FFF;">固定翼</div>
                                        </div>
                                    </div>
                                    <div style="display: flex; align-items: start; margin-bottom: 14.5px;">
                                        <div style="font-size: 14px; color: #FFF; width: 60px;">单旋翼：</div>
                                        <div style="font-size: 24px; color: #28F1FF; width: 60px; text-align: right; font-family: 'Digital'; margin-right: 8.5px;">2000</div>
                                        <div style="font-size: 14px; color: #FFF; margin-right: 10px;">架次</div>
                                        <div style="width: 70px; height: 30px; background-image: url('../../public/small-card-bg.png'); background-position: center; background-size: contain; background-repeat: no-repeat;
                                            display: flex; justify-content: center; align-items: center;
                                        ">
                                            <div style="font-size: 10px; color: #FFF;">单旋翼</div>
                                        </div>
                                    </div>
                                    <div style="display: flex; align-items: start; margin-bottom: 14.5px;">
                                        <div style="font-size: 14px; color: #FFF; width: 60px;">多轴：</div>
                                        <div style="font-size: 24px; color: #28F1FF; width: 60px; text-align: right; font-family: 'Digital'; margin-right: 8.5px;">500</div>
                                        <div style="font-size: 14px; color: #FFF; margin-right: 10px;">架次</div>
                                        <div style="width: 70px; height: 30px; background-image: url('../../public/small-card-bg.png'); background-position: center; background-size: contain; background-repeat: no-repeat;
                                            display: flex; justify-content: center; align-items: center;
                                        ">
                                            <div style="font-size: 10px; color: #FFF;">多轴</div>
                                        </div>
                                    </div>
                                    <div style="display: flex; align-items: start; margin-bottom: 14.5px;">
                                        <div style="font-size: 14px; color: #FFF; width: 60px;">复合翼：</div>
                                        <div style="font-size: 24px; color: #28F1FF; width: 60px; text-align: right; font-family: 'Digital'; margin-right: 8.5px;">300</div>
                                        <div style="font-size: 14px; color: #FFF; margin-right: 10px;">架次</div>
                                        <div style="width: 70px; height: 30px; background-image: url('../../public/small-card-bg.png'); background-position: center; background-size: contain; background-repeat: no-repeat;
                                            display: flex; justify-content: center; align-items: center;
                                        ">
                                            <div style="font-size: 10px; color: #FFF;">复合翼</div>
                                        </div>
                                    </div>
                                    <div style="display: flex; align-items: start;">
                                        <div style="font-size: 14p0; color: #FFF; width: 60px;">其他：</div>
                                        <div style="font-size: 24px; color: #28F1FF; width: 60px; text-align: right; font-family: 'Digital'; margin-right: 8.5px;">400</div>
                                        <div style="font-size: 14px; color: #FFF; margin-right: 10px;">架次</div>
                                        <div style="width: 70px; height: 30px; background-image: url('../../public/small-card-bg.png'); background-position: center; background-size: contain; background-repeat: no-repeat;
                                            display: flex; justify-content: center; align-items: center;
                                        ">
                                            <div style="font-size: 10px; color: #FFF;">其他</div>
                                        </div>
                                    </div>
                                </div>
                                <div style="flex: 1; display: flex; flex-direction: column;">
                                    <div style="color: rgba(255, 255, 255, 0.64); font-size: 10px; align-self: flex-end; padding-right: 10px;">单位：架次</div>
                                    <div id="demoId4" style="flex: 1;"></div>
                                </div>
                            </div>
                        </Card>
                        <Card class="w-36" title="本月已执行任务性质">
                            <div style="height: 100%; display: flex; box-sizing: border-box;">
                                <div id="demoId5" style="width: 230px; height: 100%;"></div>
                                <div style="padding-top: 35px;">
                                    <div style="margin-bottom: 23px; display: flex; justify-content: center; align-items: center; flex-direction: column; width: 96.5px; height: 46px; background-image: url('../../public/small-card-bg.png'); background-position: center; background-repeat: no-repeat; background-size: cover;">
                                        <div style="font-size: 10px; color: #FFF;">空中游览</div>
                                        <div style="color: #28F1FF; font-size: 16px; font-family: 'Digital';">116</div>
                                    </div>
                                    <div style="margin-bottom: 23px; display: flex; justify-content: center; align-items: center; flex-direction: column; width: 96.5px; height: 46px; background-image: url('../../public/small-card-bg.png'); background-position: center; background-repeat: no-repeat; background-size: cover;">
                                        <div style="font-size: 10px; color: #FFF;">航校训练</div>
                                        <div style="color: #28F1FF; font-size: 16px; font-family: 'Digital';">104</div>
                                    </div>
                                    <div style="display: flex; justify-content: center; align-items: center; flex-direction: column; width: 96.5px; height: 46px; background-image: url('../../public/small-card-bg.png'); background-position: center; background-repeat: no-repeat; background-size: cover;">
                                        <div style="font-size: 10px; color: #FFF;">航空摄影</div>
                                        <div style="color: #28F1FF; font-size: 16px; font-family: 'Digital';">21</div>
                                    </div>
                                </div>
                            </div>
                        </Card>
                    </div>
                </div>
            </div>
            <div class="center">
                <Card title="低空交通全局态势图"></Card>
            </div>
            <div class="right">
                <div style="display: flex; justify-content: space-around; align-items: center; padding: 20px 0;">
                    <div style="display: flex; align-items: center;">
                        <div style="display: flex; flex-direction: column; justify-content: center; align-items: center; margin-right: 18px;">
                            <div style="color: #D8D8D8; font-size: 18px; margin-bottom: 3px;">北京时间</div>
                            <div style="background-image: url('../../public/time.png'); background-position: center; background-size: cover; background-repeat: no-repeat; width: 45px; height: 45px;"></div>
                        </div>
                        <div style="display: flex; flex-direction: column; align-items: start;">
                            <div style="color: #FFF; font-size: 24px; font-family: 'Digital'; margin-bottom: 5px;">15:28:09</div>
                            <div style="color: #D8D8D8; font-size: 18px;">2021/12/26 星期四</div>
                        </div>
                    </div>
                    <div style="display: flex; align-items: center;">
                        <div style="display: flex; flex-direction: column; justify-content: center; align-items: center; margin-right: 18px;">
                            <div style="color: #D8D8D8; font-size: 18px; margin-bottom: 3px;">UTC时间</div>
                            <div style="background-image: url('../../public/time.png'); background-position: center; background-size: cover; background-repeat: no-repeat; width: 45px; height: 45px;"></div>
                        </div>
                        <div style="display: flex; flex-direction: column; align-items: start;">
                            <div style="color: #FFF; font-size: 24px; font-family: 'Digital'; margin-bottom: 5px;">15:28:09</div>
                            <div style="color: #D8D8D8; font-size: 18px;">2021/12/26 星期四</div>
                        </div>
                    </div>
                    <div style="display: flex; align-items: center;">
                        <div style="background-image: url('../../public/yun.png'); background-position: center; background-size: cover; background-repeat: no-repeat; width: 62.5px; height: 44px; margin-right: 18px;"></div>
                        <div>
                            <div style="color: #FFF; font-size: 24px;">
                                32
                                <span style="font-size: 12px;">℃</span>
                            </div>
                            <div style="font-size: 18px; color: #D8D8D8;">晴转多云</div>
                        </div>
                    </div>
                </div>
                <div style="display: flex; padding: 0 12px 0 8px; margin-bottom: 8px;">
                    <div style="width: 180px; height: 130px; padding-top: 17px; box-sizing: border-box; background-image: url('../../public/warning-bg-type1.png'); background-position: center; background-size: cover; background-repeat: no-repeat; margin-right: 6.5px; display: flex; align-items: center; flex-direction: column;">
                        <div style="color: #FFF; font-size: 14px; margin-bottom: 15px;">RA禁区告警</div>
                        <div style="display: flex; align-items: baseline; margin-bottom: 18px;">
                            <div style="font-size: 36px; color: #28F1FF; font-family: 'Digital';">10</div>
                            <div style="font-size: 12px; color: #28F1FF;">次</div>
                        </div>
                        <div style="width: 54px; height: 7.5px; background-color: #28F1FF; opacity: 0.54; border-bottom-left-radius: 3px; border-bottom-right-radius: 3px;"></div>
                    </div>
                    <div style="width: 180px; height: 130px; padding-top: 17px; box-sizing: border-box; background-image: url('../../public/warning-bg-type2.png'); background-position: center; background-size: cover; background-repeat: no-repeat; margin-right: 6.5px; display: flex; align-items: center; flex-direction: column;">
                        <div style="color: #FFF; font-size: 14px; margin-bottom: 15px;">RA禁区告警</div>
                        <div style="display: flex; align-items: baseline; margin-bottom: 18px;">
                            <div style="font-size: 36px; color: #28F1FF; font-family: 'Digital';">10</div>
                            <div style="font-size: 12px; color: #28F1FF;">次</div>
                        </div>
                        <div style="width: 54px; height: 7.5px; background-color: #28F1FF; opacity: 0.54; border-bottom-left-radius: 3px; border-bottom-right-radius: 3px;"></div>
                    </div>
                    <div style="width: 180px; height: 130px; padding-top: 17px; box-sizing: border-box; background-image: url('../../public/warning-bg-type2.png'); background-position: center; background-size: cover; background-repeat: no-repeat; margin-right: 6.5px; display: flex; align-items: center; flex-direction: column;">
                        <div style="color: #FFF; font-size: 14px; margin-bottom: 15px;">RA禁区告警</div>
                        <div style="display: flex; align-items: baseline; margin-bottom: 18px;">
                            <div style="font-size: 36px; color: #28F1FF; font-family: 'Digital';">10</div>
                            <div style="font-size: 12px; color: #28F1FF;">次</div>
                        </div>
                        <div style="width: 54px; height: 7.5px; background-color: #28F1FF; opacity: 0.54; border-bottom-left-radius: 3px; border-bottom-right-radius: 3px;"></div>
                    </div>
                    <div style="width: 180px; height: 130px; padding-top: 17px; box-sizing: border-box; background-image: url('../../public/warning-bg-type3.png'); background-position: center; background-size: cover; background-repeat: no-repeat; margin-right: 6.5px; display: flex; align-items: center; flex-direction: column;">
                        <div style="color: #FFF; font-size: 14px; margin-bottom: 15px;">RA禁区告警</div>
                        <div style="display: flex; align-items: baseline; margin-bottom: 18px;">
                            <div style="font-size: 36px; color: #28F1FF; font-family: 'Digital';">10</div>
                            <div style="font-size: 12px; color: #28F1FF;">次</div>
                        </div>
                        <div style="width: 54px; height: 7.5px; background-color: #28F1FF; opacity: 0.54; border-bottom-left-radius: 3px; border-bottom-right-radius: 3px;"></div>
                    </div>
                    <div style="width: 180px; height: 130px; padding-top: 17px; box-sizing: border-box; background-image: url('../../public/warning-bg-type4.png'); background-position: center; background-size: cover; background-repeat: no-repeat; display: flex; align-items: center; flex-direction: column;">
                        <div style="color: #FFF; font-size: 14px; margin-bottom: 15px;">RA禁区告警</div>
                        <div style="display: flex; align-items: baseline; margin-bottom: 18px;">
                            <div style="font-size: 36px; color: #28F1FF; font-family: 'Digital';">10</div>
                            <div style="font-size: 12px; color: #28F1FF;">次</div>
                        </div>
                        <div style="width: 54px; height: 7.5px; background-color: #28F1FF; opacity: 0.54; border-bottom-left-radius: 3px; border-bottom-right-radius: 3px;"></div>
                    </div>
                </div>
                <div class="rows">
                    <div class="row">
                        <Card class="w-50 mr-8" title="批复空域统计">
                            <div style="height: 256px; position: relative;" id="demoId6">
                                <div style="position: absolute; right: 10px; top: 10px; color: rgba(255, 255, 255, 0.64); font-size: 10px;">单位：次</div>
                            </div>
                        </Card>
                        <Card class="w-50" title="报送计划统计">
                            <div style="height: 256px;">
                                <div style="display: flex; justify-content: space-between; align-items: flex-end; padding: 8px 10px 10px 20px;">
                                    <div style="display: flex; flex-direction: column;">
                                        <div style="font-size: 10px; color: #FFF; margin-bottom: 5px;">报送总次数</div>
                                        <div style="display: flex; align-items: baseline;">
                                            <div style="font-size: 30px; color: #28F1FF; font-family: 'Digital'; margin-right: 10px;">430</div>
                                            <div style="font-size: 10px; color: #FFF;">次</div>
                                        </div>
                                    </div>
                                    <div style="font-size: 10px; color: rgba(255, 255, 255, 0.64);">单位：次</div>
                                </div>
                                <div style="display: flex; align-items: center; padding: 0 8.5px 0 21.5px;">
                                    <div style="width: 3.5px; height: 3.5px; background-color: #DA6136; border-radius: 50%; flex: none;"></div>
                                    <div style="background-color: #1A3D41; height: 1px; flex: 1;"></div>
                                    <div style="width: 3.5px; height: 3.5px; background-color: #DA6136; border-radius: 50%; flex: none;"></div>
                                </div>
                                <div style="padding: 0 10px 0 20px;">
                                    <div style="display: flex; align-items: center; height: 36px;">
                                        <div style="width: 17px; height: 21px; margin-right: 9.5px; color: #FFF;">1</div>
                                        <div style="font-size: 12px; color: #FFF; margin-right: 10px;">太原市</div>
                                        <div style="height: 9px; flex: 1; background-color: #28F1FF; margin-right: 4.5px;"></div>
                                        <div style="height: 9px; width: 4px; background-color: #DA6136; margin-right: 5px;"></div>
                                        <div style="font-size: 12px; color: #FFF; font-family: 'Digital';">98</div>
                                        <div style="font-size: 12px; color: #FFF; font-family: 'Digital';">次</div>
                                    </div>
                                    <div style="display: flex; align-items: center; height: 36px;">
                                        <div style="width: 17px; height: 21px; margin-right: 9.5px; color: #FFF;">2</div>
                                        <div style="font-size: 12px; color: #FFF; margin-right: 10px;">大同市</div>
                                        <div style="height: 9px; flex: 0.8; background-color: #28F1FF; margin-right: 4.5px;"></div>
                                        <div style="height: 9px; width: 4px; background-color: #DA6136; margin-right: 5px;"></div>
                                        <div style="font-size: 12px; color: #FFF; font-family: 'Digital';">98</div>
                                        <div style="font-size: 12px; color: #FFF; font-family: 'Digital';">次</div>
                                    </div>
                                    <div style="display: flex; align-items: center; height: 36px;">
                                        <div style="width: 17px; height: 21px; margin-right: 9.5px; color: #FFF;">3</div>
                                        <div style="font-size: 12px; color: #FFF; margin-right: 10px;">晋中市</div>
                                        <div style="height: 9px; flex: 0.6; background-color: #28F1FF; margin-right: 4.5px;"></div>
                                        <div style="height: 9px; width: 4px; background-color: #DA6136; margin-right: 5px;"></div>
                                        <div style="font-size: 12px; color: #FFF; font-family: 'Digital';">98</div>
                                        <div style="font-size: 12px; color: #FFF; font-family: 'Digital';">次</div>
                                    </div>
                                    <div style="display: flex; align-items: center; height: 36px;">
                                        <div style="width: 17px; height: 21px; margin-right: 9.5px; color: #FFF;">4</div>
                                        <div style="font-size: 12px; color: #FFF; margin-right: 10px;">阳泉市</div>
                                        <div style="height: 9px; flex: 0.4; background-color: #28F1FF; margin-right: 4.5px;"></div>
                                        <div style="height: 9px; width: 4px; background-color: #DA6136; margin-right: 5px;"></div>
                                        <div style="font-size: 12px; color: #FFF; font-family: 'Digital';">98</div>
                                        <div style="font-size: 12px; color: #FFF; font-family: 'Digital';">次</div>
                                    </div>
                                    <div style="display: flex; align-items: center; height: 36px;">
                                        <div style="width: 17px; height: 21px; margin-right: 9.5px; color: #FFF;">5</div>
                                        <div style="font-size: 12px; color: #FFF; margin-right: 10px;">长治市</div>
                                        <div style="height: 9px; flex: 0.2; background-color: #28F1FF; margin-right: 4.5px;"></div>
                                        <div style="height: 9px; width: 4px; background-color: #DA6136; margin-right: 5px;"></div>
                                        <div style="font-size: 12px; color: #FFF; font-family: 'Digital';">98</div>
                                        <div style="font-size: 12px; color: #FFF; font-family: 'Digital';">次</div>
                                    </div>
                                </div>
                                <div style="display: flex; align-items: center; padding: 0 8.5px 0 21.5px;">
                                    <div style="width: 3.5px; height: 3.5px; background-color: #DA6136; border-radius: 50%; flex: none;"></div>
                                    <div style="background-color: #1A3D41; height: 1px; flex: 1;"></div>
                                    <div style="width: 3.5px; height: 3.5px; background-color: #DA6136; border-radius: 50%; flex: none;"></div>
                                </div>
                            </div>
                        </Card>
                    </div>
                    <div class="row">
                        <Card class="w-100" title="情报数据">
                            <div style="height: 182px; flex: 1; padding: 10.5px 16px 12px 15.5px; box-sizing: border-box;">
                                <div style="height: 75px; background-color: rgba(255, 255, 255, 0.10); margin-bottom: 10px; padding: 11.5px; box-sizing: border-box;">
                                    <div style="display: flex; align-items: center; margin-bottom: 12px;">
                                        <div style="width: 14px; height: 14px; background-color: #28F1FF; border-radius: 50%; margin-right: 11.5px;"></div>
                                        <div style="color: #28EFFA; font-size: 18px; line-height: 20px;">[航行通告·危险活动]</div>
                                    </div>
                                    <div style="color: #FFF; font-size: 18px; line-height: 20px;">大同市云州区区域划定临时危险区，因大型跳伞活动，12月5日08:00-12:00</div>
                                </div>
                                <div style="height: 75px; background-color: rgba(255, 255, 255, 0.10); padding: 11.5px; box-sizing: border-box;">
                                    <div style="display: flex; align-items: center; margin-bottom: 12px;">
                                        <div style="width: 14px; height: 14px; background-color: #28F1FF; border-radius: 50%; margin-right: 11.5px;"></div>
                                        <div style="color: #28EFFA; font-size: 18px; line-height: 20px;">[航行通告·危险活动]</div>
                                    </div>
                                    <div style="color: #FFF; font-size: 18px; line-height: 20px;">大同市云州区区域划定临时危险区，因大型跳伞活动，12月5日08:00-12:00</div>
                                </div>
                            </div>
                        </Card>
                    </div>
                    <div class="row">
                        <Card class="w-100" title="气象数据">
                            <div style="height: 182px; flex: 1; box-sizing: border-box; padding: 10.5px 13.5px 9.5px 17.5px;">
                                <div style="display: flex; align-items: center; height: 50px; margin-bottom: 6px; background-image: url('../../public/info-bg.png'); background-position: center; background-size: cover; background-repeat: no-repeat; padding: 7px 0 7px 13px; box-sizing: border-box;">
                                    <div style="height: 36px; width: 165.5px; margin-right: 21.5px; background-color: rgba(238, 62, 62, 0.30); display: flex; justify-content: center; align-items: center; font-size: 18px; color: #EE3E3E;">
                                        大风红色预警
                                    </div>
                                    <div style="font-size: 18px; color: #FFF;">太原武宿机场区域，瞬时风力可达9级，预计持续至16:00。影响：所有低空起降</div>
                                </div>
                                <div style="display: flex; align-items: center; height: 50px; margin-bottom: 6px; background-image: url('../../public/info-bg.png'); background-position: center; background-size: cover; background-repeat: no-repeat; padding: 7px 0 7px 13px; box-sizing: border-box;">
                                    <div style="height: 36px; width: 165.5px; margin-right: 21.5px; background-color: rgba(251, 154, 85, 0.30); display: flex; justify-content: center; align-items: center; font-size: 18px; color: #FB9A55;">
                                        低能见度
                                    </div>
                                    <div style="font-size: 18px; color: #FFF;">太原武宿机场区域，瞬时风力可达9级，预计持续至16:00。影响：所有低空起降</div>
                                </div>
                                <div style="display: flex; align-items: center; height: 50px; background-image: url('../../public/info-bg.png'); background-position: center; background-size: cover; background-repeat: no-repeat; padding: 7px 0 7px 13px; box-sizing: border-box;">
                                    <div style="height: 36px; width: 165.5px; margin-right: 21.5px; background-color: rgba(238, 62, 62, 0.30); display: flex; justify-content: center; align-items: center; font-size: 18px; color: #EE3E3E;">
                                        大风红色预警
                                    </div>
                                    <div style="font-size: 18px; color: #FFF;">太原武宿机场区域，瞬时风力可达9级，预计持续至16:00。影响：所有低空起降</div>
                                </div>
                            </div>
                        </Card>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<style>
    body,html {
        margin: 0;
        padding: 0;
    }
    #screen {
        width: 3440px;
        height: 1032px;
        transform-origin: left top;
        background-color: #011A3E;
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
        color: #FFF;
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
    .num-box {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 11px;
        justify-content: space-between;
    }
    .num-item {
        background-image: url('../../public/legend-img.png');
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
        font-family: 'Digital';
        font-size: 24px;
        color: #00ffff;
    }
    .num-item .text {
        font-size: 10px;
        color: #FFF;
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