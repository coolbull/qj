<template>
	<view class="content">
		<!-- 顶部操作菜单 -->
		<paper-left-popup :show="show" @hide="hidepopup" @addfriend="addfrined" @clear="clear"></paper-left-popup>
		<!-- 轮播图 -->
		<Swiper :image="image"></Swiper>
		<!-- 提示框 -->
		<u-notice-bar mode="horizontal" :list="list"></u-notice-bar>
		<!-- 宫格导航 -->
		<u-grid :col="4" :border="false">
			<u-grid-item>
				<image src="../../static/index/gird1.png" mode=""></image>
				<view class="grid-text">钢琴调音</view>
			</u-grid-item>
			<u-grid-item>
				<image src="../../static/index/gird2.png" mode=""></image>
				<view class="grid-text">钢琴维修</view>
			</u-grid-item>
			<u-grid-item>
				<image src="../../static/index/gird3.png" mode=""></image>
				<view class="grid-text">钢琴搬运</view>
			</u-grid-item>
			<u-grid-item>
				<image src="../../static/index/gird4.png" mode=""></image>
				<view class="grid-text">关于我们</view>
			</u-grid-item>
		</u-grid>
		<!-- tab切换 -->
		<u-tabs :list="tabs" :is-scroll="false" :current="current" @change="change"></u-tabs>
		<block v-for="(item,indexs) in pic" :index="indexs">
			<view class="pic" v-show="current == indexs">
				<image :src='item'  mode=""></image>
			</view>
		</block>
		
	</view>
</template>

<script>
	import Swiper from "../../components/swiper/swiper.vue"
	import paperLeftPopup from '../../components/popup/paper-left-popup.vue';

	export default {
		components: {
			Swiper,
			paperLeftPopup,

		},
		data() {
			return {
				show: false,
				image: [{
						path: "../../static/index/swiper1.png"
					},
					{
						path: "../../static/index/swiper2.png"
					},
					{
						path: "../../static/index/swiper3.png"
					}
				],
				list: [
					'成都双流区',
					'立式钢琴',
					'一年未调298元',
					'11 - 28',
					'成都双流区',
					'立式钢琴',
					'一年未调298元',
					'11 - 28'
				],
				current: 0,
				tabs: [

					{
						name: "钢琴调音"
					},
					{
						name: "钢琴维修"
					},
					{
						name: "钢琴搬运"
					},

				],
				pic: [
					"../../static/index/tabnav1.png",
					"../../static/index/tabnav2.png",
					"../../static/index/tabnav3.png"
				]
			}
		},
		onLoad() {

		},
		methods: {
			//顶部操作菜单
			addfrined() {
				console.log('addfirend');
				this.hidepopup();
			},
			clear() {
				console.log();
				this.hidepopup();
			},
			hidepopup() {
				this.show = false;
			},
			showpopup() {
				this.show = true;
			},
			// 监听change事件
			change(index) {
				this.current = index;
			}
		},
		//监听原生导航栏点击事件
		onNavigationBarButtonTap(e) {
			// console.log(JSON.stringify());
			switch (e.index) {
				case 0:
					console.log("点击了左边按钮");
					uni.navigateTo({
						url: '../index/index',
					});
					break;
				case 1:
					this.showpopup();
					break;
				case 2:
					this.go();
					break;
				default:
					break;
			}
		}
	}
</script>

<style scoped>
	/* 宫格导航 */
	.u-grid {
		margin-top: 10upx;
		margin-bottom: 10upx;
	}

	.u-grid-item image {
		width: 108upx;
		height: 108upx;
		margin-bottom: 10upx;
	}

	/* tabnav */
	.pic image {
		height: 400upx;
		width: 100%;
		margin-bottom: 10upx;
	}
	.u-tabs{
		margin-bottom: 20upx;
	}
</style>
