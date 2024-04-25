<template>
	<view class="content">

		<view class="titleIos"></view>

		<div class="mui-content" style="margin-top: 16px;">

			<div id="container" style="height: 86vh; margin-top: 0px;"></div>


		</div>


	</view>
</template>

<script>
	
	import echarts from '/static/h5/echartsTwo';
	

	export default {
		data() {
			return {

			}
		},
		onReady() {




		},
		onLoad: function(e) {
			console.log(e);


		},
		onShow() {


		},
		mounted() {
			this.treeData()
		},

		methods: {
			treeData() {

				var dom = document.getElementById("container");
				var myChart = echarts.init(dom);

				//  颜色设定 不同颜色寓意不同权重
				var fatherColor = 'green';
				var midColor = 'rgb(193, 92, 31)';
				var smallColor = 'rgb(247, 203, 174)';



				var option;

				// 新能源汽车
				let swyyQ = {
					"name": "新能源汽车",
					itemStyle: {
						color: midColor
					},
					"children": [{
							"name": "大型企业",
							itemStyle: {
								color: fatherColor
							},


						},
						{
							"name": "中型企业",
							itemStyle: {
								color: midColor
							},

						},
						{
							"name": "小型企业",
							itemStyle: {
								color: smallColor
							},

						},
						{
							"name": "其他规模企业",
							itemStyle: {
								color: fatherColor
							},
						}
					]
				};

				// 新材料行业
				let xclkQ = {
					"name": "生物与新医药",
					itemStyle: {
						color: fatherColor
					},
					"children": [{
							"name": "大型企业",
							itemStyle: {
								color: fatherColor
							},


						},
						{
							"name": "中型企业",
							itemStyle: {
								color: midColor
							},

						},
						{
							"name": "小型企业",
							itemStyle: {
								color: smallColor
							},

						},
						{
							"name": "其他规模企业",
							itemStyle: {
								color: fatherColor
							},
						}
					]
				};;



				let data = {
					"name": "行业分类",
					itemStyle: {
						color: fatherColor
					},
					"children": [swyyQ, xclkQ]

				}
				// 获取网页宽度 设置树形条目实体宽高度
				let width = document.body.scrollWidth;
				let widthSize = 0.039 * width;
				if (widthSize > 36) {
					widthSize = 36;
				}
				let heightSize = widthSize * 2.2;

				myChart.setOption(
					(option = {
						tooltip: {
							trigger: 'item',
							triggerOn: 'mousemove'
						},
						series: [{
							type: 'tree',
							data: [data],
							left: '2%',
							right: '2%',
							top: '8%',
							bottom: '20%',
							symbol: 'square',
							symbolSize: [widthSize, heightSize],
							orient: 'vertical',
							expandAndCollapse: true,
							initialTreeDepth: 2,


							label: {
								position: 'top',
								rotate: 0,
								verticalAlign: 'middle',
								align: 'center',
								fontSize: 12
							},
							leaves: {
								label: {
									position: 'bottom',
									rotate: -90,
									verticalAlign: 'middle',
									align: 'left'
								}
							},
							animationDurationUpdate: 150
						}]
					})
				);



				if (option && typeof option === 'object') {
					myChart.setOption(option);
				}

			},

			

		}

	}
</script>


<style>
	.content {
		display: flex;
		flex-direction: column;

	}
</style>