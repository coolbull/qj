<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style lang="scss">
	
	 /* 注意要写在第一行，同时给style标签加入lang="scss"属性 */
	    @import "uview-ui/index.scss";
		
	/*每个页面公共css */
	
	/* 默认样式重置 */
	@import "./common/normalize.css";
	
	/* iconfont字体库 */
	@import url("//at.alicdn.com/t/font_2033227_6qq52zt40l4.css");
</style>
