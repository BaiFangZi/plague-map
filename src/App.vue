<template>
	<div id="app">
		<div class="text">
			<h1 style="font-size: 20px;font-weight: 600;">新型冠状病毒肺炎</h1>
			<p class="section">
				新型冠状病毒肺炎（“Novel coronavirus pneumonia”，简称“NCP”），简称“新冠肺炎”，是指
				<a href="https://baike.baidu.com/item/2019%E6%96%B0%E5%9E%8B%E5%86%A0%E7%8A%B6%E7%97%85%E6%AF%92/24267858">2019新型冠状病毒</a>
				感染导致的肺炎。2019年12月以来，湖北省武汉市部分医院陆续发现了多例有华南海鲜市场暴露史的
				<a href="https://baike.baidu.com/item/%E4%B8%8D%E6%98%8E%E5%8E%9F%E5%9B%A0%E8%82%BA%E7%82%8E/4211489">不明原因肺炎</a>
				病例，现已证实为2019新型冠状病毒感染引起的急性呼吸道传染病。 [1-4] 2020年2月5日，国家卫健委发布了
				<a
					href="https://baike.baidu.com/item/%E6%96%B0%E5%9E%8B%E5%86%A0%E7%8A%B6%E7%97%85%E6%AF%92%E6%84%9F%E6%9F%93%E7%9A%84%E8%82%BA%E7%82%8E%E8%AF%8A%E7%96%97%E6%96%B9%E6%A1%88%EF%BC%88%E8%AF%95%E8%A1%8C%E7%AC%AC%E4%BA%94%E7%89%88%EF%BC%89/24312167"
				>
					《新型冠状病毒感染的肺炎诊疗方案（试行第五版）》
				</a>
				。 2020年2月11日，世界卫生组织总干事谭德塞在瑞士日内瓦宣布，将新型冠状病毒感染的肺炎命名为“COVID-19”
			</p>
			<h2>传播途径</h2>
			<p class="section">
				据央视新闻消息，上海疫情防控工作发布会介绍：卫生防疫专家强调，可以确定的新冠肺炎传播途径主要为直接传播、气溶胶传播和接触传播。直接传播是指患者喷嚏、咳嗽、说话的飞沫，呼出的气体近距离直接吸入导致的感染；气溶胶传播是指飞沫混合在空气中，形成气溶胶，吸入后导致感染；接触传播是指飞沫沉积在物品表面，接触污染手后，再接触口腔、鼻腔、眼睛等粘膜，导致感染
			</p>
			<h2>专家观点</h2>
			<p class="section">
				2020年2月10日，武汉市金银潭医院党委副书记、院长张定宇介绍，新冠肺炎实际是一种自限性疾病。绝大部分患者，包括重症及危重症患者，经过各种氧疗、对症治疗和免疫调节治疗以后，均可以顺利出院。
			</p>
			<p class="from">
				--简要摘抄于
				<a
					href="https://baike.baidu.com/item/%E6%96%B0%E5%9E%8B%E5%86%A0%E7%8A%B6%E7%97%85%E6%AF%92%E8%82%BA%E7%82%8E/24282529?fr=aladdin&fromtitle=%E6%96%B0%E5%9E%8B%E5%86%A0%E7%8A%B6%E7%97%85%E6%AF%92%E6%84%9F%E6%9F%93%E7%9A%84%E8%82%BA%E7%82%8E&fromid=24282048"
				>
					百度百科
				</a>
			</p>
			<button @click="switchCur" class="btn-state">现有确诊</button>
			<button @click="switchTol"  class="btn-state">累计确诊</button>
		</div>
		<my-map :isCur='isCur'></my-map>
		<!-- <router-view   /> -->
	</div>
</template>

<script>
import map from './components/HelloWorld';
export default {
	name: 'App',
	components:{
		myMap:map,
	},
	data() {
		return {
			isCur: true
		};
	},
	methods: {
		switchCur() {	
			this.isCur = true;
		},
		switchTol() {
			this.isCur = false;
		}
	}
};
</script>

<style>
#app {
	min-width: 1200px;
}
.text {
	float: right;
	width: 600px;
	margin-right: 20px;
}
.btn-state{
	display: inline-block;
	    width: 200px;
	    height: 40px;
	    background: bisque;
}
p.section {
	text-indent: 2em;
}
p.from {
	text-align: right;
}
h2 {
	font-weight: 600;
}
</style>
