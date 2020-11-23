<script>
export default {
	onLaunch: function() {
		console.log('App Launch');
		// 登录  用户信息  储存我们的用户信息
	},
	onShow: function() {
		console.log('App Show');
		// 时间戳
	},
	onHide: function() {
		console.log('App Hide');
		// 进入后台需要执行的事件
	},
	onError: function(e){
		console.log(e)
	}
};
</script>

<style>
@import url("@/common/base.css");
/* 解决头条小程序组件内引入字体不生效的问题 */
/* #ifdef MP-TOUTIAO */
@font-face {
	font-family: uniicons;
	src: url('/static/uni.ttf');
}
/* #endif */



</style>
