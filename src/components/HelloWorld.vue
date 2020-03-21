<template>
	<div ref="map" class="map">
	</div>

</template>

<script>
import 'echarts/map/js/china.js';
import myEcharts from 'echarts';

export default {
	name: 'HelloWorld',
	props:['isCur'],
	data() {
		return {
			state:'现有',
			list: [],
			option: {
				title: {
					text: '疫情地图'
				},
				series: [
					{
						name: '已确诊人数',
						type: 'map',
						map: 'china',
						label: {
							show: true,
							
						}
					}
				],
				visualMap: [
					{
						type: 'piecewise',
						splitNumber: 6,
						pieces: [{ min: 10000 }, { min: 1000, max: 9999 }, { min: 500, max: 999 }, { min: 100, max: 499 }, { min: 10, max: 99 }, { min: 1, max: 9 }],
						bottom:'100',
						show: true,
					}
				],
				tooltip: {
					show: true,
					trigger: 'item',
					triggerOn: 'click',
					formatter: function(params) {
						var tip = '';
						
						tip = `${params.name}<br>确诊人数:${params.data.value}<br>死亡人数:${params.data.deathNum}<br>治愈人数${params.data.cureNum}`;
						return tip;
					}
				}
			}
		};
	},
	mounted() {
		this.chart = myEcharts.init(this.$refs.map);
		this.getData();
		console.log(this.isCur)
		// this.chart.setOption(this.option);
	},
	methods: {
		getData() {
			this.$jsonp('https://gwpre.sina.cn/interface/fymap2020_data.json?1582117092681', {}, (err, result) => {
				this.list = result.data.list.map(item => ({
					name: item.name,
					// value: item.value,
					value:item.value-item.deathNum-item.cureNum,
					deathNum: item.deathNum,
					cureNum: item.cureNum
				}));
				this.option.series[0].data = this.list;
				this.chart.setOption(this.option);
			});
		}
	},
watch: {
	isCur() {
		if(this.isCur){
			console.log('现有确诊人数')
			this.list.forEach((item)=>{
				item.value-=(item.deathNum+item.cureNum)
				
			})
			console.log(this.list)
			this.option.series[0].data = this.list;
			this.chart.setOption(this.option);
		}else{
			console.log('总共确诊人数')
			this.list.forEach((item)=>{
				item.value+=parseInt((item.deathNum+item.cureNum))
			})
			console.log('total')
			console.log( this.list)
			this.option.series[0].data = this.list;
			this.chart.setOption(this.option);
		}
	}
},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.map {
	float: left;
	height: 700px;
	width: 850px;
}
</style>
