<template>
  <div class="index-wrap">
    <div class="index-left">
      <div class="index-left-block">
        <h2>树形侧边导航栏</h2>
        <ul v-for="menuItem in theModel">
          <myTree class="item" :model="menuItem"></myTree>
        </ul>
       
      </div>
    </div>
    <div class="index-right">
      <div class="index-right-block">
        <h2>echarts演示</h2>
        <div id="myChart" :style="{width: '300px',height: '300px'}"></div>
      </div>
    </div>
  </div>
</template>

<script>
import myTree from '../components/treeMenu.vue'
import echarts from 'echarts'
import Vue from 'vue'

Vue.prototype.$echarts = echarts
var myData =[{
  'id': '1',
  'menuName': 'echarts',
  'menuCode': '10',
  'children': [
  {
    'menuName': '地图',
    'menuCode': '11',
  },
  {
    'menuName': '柱状图',
    'menuCode': '12',
    'children': [
    {
      'menuName': '交错正负轴标签',
      'menuCode': '121'
    },
    {
      'menuName': '柱状图框选 ',
      'menuCode': '122'
    },
    {
      'menuName': '堆叠柱状图',
      'menuCode': '124'
    }]
  },
  {
    'menuName': '条形图',
    'menuCode': '13'
  }]
},
{
  'id': '2',
  'menuName': '树形结构',
  'menuCode': '21'
},
{
  'id': '3',
  'menuName': 'gird分页',
  'menuCode': '30'
            }]

export default {
  name: 'items',
  props: ['model'],
  components: {
    myTree
  },
  data () {
    return {
      theModel: myData
    }
  },
  mounted() {
    this.drawLine();
  },
  methods: {
    drawLine() {
      let myChart = this.$echarts.init(document.getElementById('myChart'))
      myChart.setOption({
        title: {
          
        },
        tooltip: {

        },
        xAxis: {
          data: ["衬衫","羊毛衫","雪纺衫","裤子","高跟鞋","袜子"]
        },
        yAxis: {
        },
        series: [{
          name: '销量',
          type: 'bar',
          data: [5,20,36,10,10,20]
        }]
      });
    }
  }
 
}
   
</script>

<style scoped>
.index-wrap {
  width: 1200px;
  margin: 0 auto;
  overflow: hidden;
}
.index-left {
  float: left;
  width: 300px;
  text-align: left;
}
.index-right {
  float: left;
  width: 900px;
}
.index-left-block, .index-right-block{
  height: 450px;
  margin: 15px;
  background: #fff;
  box-shadow: 0 0 1px #ddd;
}

.index-left-block h2,.index-right-block h2 {
  background: #4fc08d;
  color: #fff;
  padding: 20px 20px;
  font-size: 1.5em;
}

.item {
  cursor: pointer;
}
ul{
  line-height: 40px;
  list-style-type: dot;
}

li div:active,li div:hover {
  background: #9FDABE;
  color: #eee;
}

ul li:hover {
  background: #A6C2B0;
}

</style>
