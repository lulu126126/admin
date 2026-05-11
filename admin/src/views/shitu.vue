<template>
  <div class="main" style="height: 100%; width: 100%">

    <div class="quarter-div" style="; height: 220px;
  width: 48%;  float: left ;
  position: relative  ;" id="blue">
    </div>
    <div class="quarter-div " style=" height:  220px;
  width: 48%;  float:right;
  position: relative  ;" id="green"></div>
    <div class="quarter-div "  style="height:  220px;
  width: 48%; float: left;
  position: relative  ;" id="orange"></div>
    <div class="quarter-div " style=" height:  220px;
  width: 48%; float: right;
  position: relative  ;" id="yellow"></div>

  </div>
</template>

<script>
import * as echarts from 'echarts';
export default {
  name: "shitu",
  mounted() {
    /*this.getZsEcharts()();*/
    let btName1=[];
    let btValue1=[];
    const chartDom3 = this.$echarts.init(document.getElementById('blue'));
    this.$http({
      url: `/statistical/selete1`,
      method: "get",

    }).then(res=>{
      btName1 = res.data.data.name;
      btValue1 = res.data.data.frequency;

      chartDom3.setOption({

        tooltip: {
          trigger: 'item'
        },
        legend: {
          top: '2%',
          left: 'center'
        },
        series: [
          {
            name: '数量',
            type: 'pie',
            radius: ['30%', '70%'],
            center:['50%','60%'],
            avoidLabelOverlap: false,
            itemStyle: {
              borderRadius: 10,
              borderColor: '#fff',
              borderWidth: 2
            },
            label: {
              show: false,
              position: 'center'
            },
            emphasis: {
              label: {
                show: true,
                fontSize: 15,
                fontWeight: 'bold'
              }
            },
            labelLine: {
              show: false
            },
            data: [
              { value: btValue1[0], name: btName1[0] },
             { value: btValue1[1], name: btName1[1]  },
              { value: btValue1[2], name: btName1[2]  },
              { value: btValue1[3], name: btName1[3]  },
              { value: btValue1[4], name: btName1[4]  },

            ]
          }
        ]
      })
    })
   let btName2=[];
    let btValue2=[];
    const chartDom2 = echarts.init(document.getElementById('green'));

    this.$http({
      url: `/statistical/selete2`,
      method: "get",

    }).then(res=>{

      btName2 = res.data.data.name;
      btValue2 = res.data.data.frequency;
      console.log(btName2)
      console.log(btName2)
      console.log(btValue2)
      console.log(btValue2)
      chartDom2.setOption({
        title: {
          text: '用户人员性别统计',
          left: 'center'
        },
        tooltip: {
          trigger: 'item'
        },
        legend: {
          orient: 'vertical',
          left: 'left'
        },
        series: [
          {
            name: '人员数：',
            type: 'pie',
            radius: '50%',
            data: [
              { value: btValue2[0], name: btName2[0]},
              { value: btValue2[1], name: btName2[1] },

            ],
            emphasis: {
              itemStyle: {
                shadowBlur: 10,
                shadowOffsetX: 0,
                shadowColor: 'rgba(0, 0, 0, 0.5)'
              }
            }
          }
        ]
      })
    })
  let btName3=[];
   let btValue3=[];
   const chartDom1 = echarts.init(document.getElementById('orange'));
   this.$http({
     url: `/statistical/selete3`,
     method: "get",

   }).then(res=>{
     console.log(res)
     console.log(res)
     console.log(res)
     btName3 = res.data.data.name;
     btValue3 = res.data.data.frequency;
     chartDom1.setOption({
       title: {
         text: '失物招领情况季度分析'
       },
       tooltip: {
         trigger: 'axis'
       },

       grid: {
         left: '3%',
         right: '4%',
         bottom: '3%',
         containLabel: true
       },
       toolbox: {
         feature: {
           saveAsImage: {}
         }
       },
       xAxis: {
         type: 'category',
         boundaryGap: false,
         //取分类数
         data: btName3
       },
       yAxis: {
         type: 'value'
       },
       series: [
         {
           name: '失物招领数量',
           type: 'line',
           stack: 'Total',
           data: btValue3
         },
       ]

     })
   })
    let zxName4=[];
  let zxValue4=[];
  const chartDom = echarts.init(document.getElementById('yellow'));
  this.$http({
    url: `/statistical/selete4`,
    method: "get",

  }).then(res=>{
    console.log(res)
    console.log(res)
    console.log(res)
    zxName4 = res.data.data;
    zxValue4= res.data.data;
    chartDom.setOption({
      ooltip: {
        trigger: 'axis',
        axisPointer: {
          // Use axis to trigger tooltip
          type: 'shadow' // 'shadow' as default; can also be 'line' or 'shadow'
        }
      },
      legend: {},
      grid: {
        left: '3%',
        right: '4%',
        bottom: '3%',
        containLabel: true
      },
      xAxis: {
        type: 'value'
      },
      yAxis: {
        type: 'category',
        data: ['第一季度','第二季度','第三季度','第四季度',]
      },
      series: [
        {
          name: zxName4.location[0],
          type: 'bar',
          stack: 'total',
          label: {
            show: true
          },
          emphasis: {
            focus: 'series'
          },
          data: zxValue4.sj1
        },
        {
          name: zxName4.location[1],
          type: 'bar',
          stack: 'total',
          label: {
            show: true
          },
          emphasis: {
            focus: 'series'
          },
          data: zxValue4.sj2
        },
        {
          name: zxName4.location[2],
          type: 'bar',
          stack: 'total',
          label: {
            show: true
          },
          emphasis: {
            focus: 'series'
          },
          data: zxValue4.sj3
        },


      ]

    });
    })



  },


}
</script>


<style  lang="scss" type="text/css">

quarter-div{

  border: #515a6e 1px solid;
}




</style>