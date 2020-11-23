<template>
	<view class="container-login">
		<view v-if="num>5">{{message}}</view>
		<view v-else>{{param}}</view>
		<view v-for="(item, index) in detailList" class='list br'>
			<text key="item.id">{{item.name}}</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				message: 'hello uniapp-1111',
				param: 'hi',
				num: 6,
				detailList: [{id:'1',name:'张三'},{id:'2',name:'李四'},{id:'3',name:'王五'},{id:'4',name:'小旺'}]
			}
		},
		onLoad(e){
			// 接受上个页面传递的参数
			console.log('page2-onLoad', e);
			this.param = e.id;
		},
		onShow(){
			// 只要页面出现就会触发
			console.log('page2-onShow');
		},
		onReady(){
			// 监听页面初次渲染完成
			console.log('page2-onReady');
		},
		onHide(){
			// 监听页面隐藏
			console.log('page2-onHide');
		},
		onUnload(){
			// 监听页面卸载
			console.log('page2-onUnload');
		},
		methods: {
	
		}
	}
</script>

<style scoped>
	/*
		设计稿750 100px
		750*100/750 = 100rpx
	*/
	/* 
		设计稿640 100px
		750*100/640 = 117rpx
	*/
	.container-login {
		padding: 20px;
		font-size: 24px;
		line-height: 24px;
	}
	
	.list{
		/* width: 100rpx; */
		height: 100rpx;
		/* border: 1px solid red; */
	}
</style>





