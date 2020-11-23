<template>
	<view class="container">
		<!-- 有代办数据时，头部展示数据导航 -->
		<hd v-if="list.length!=0" :activeIndex="activeIndex" @tab="tab()" :listData="listData"></hd>
		<!-- 没有数据展示 -->
		<nodata v-else></nodata>
		
		
		<!-- todo数据列表 -->
		<view v-if="list.length!=0" class="todo-content">
			<view v-for="(item,index) in listData" class="todo-list" :class="{'todo-finish': item.checked}" :key="index" @click="finish(item.id)">
				<view class="todo-list-checkbox"></view>
				<view class="todo-list-content">{{item.content}}</view>
			</view>
		</view>
		<!-- 创建按钮 -->
		
		
		<ct @create="create()" @cancel="cancel()" :active="active"  @add="add()" ></ct>
		
	</view>
</template>

<script>
	import list from '@/components/list.vue';
	import hd from '@/pages/index/components/header/index.vue';
	import nodata from '@/pages/index/components/noData/index.vue';
	import ct from '@/pages/index/components/create/index.vue';
	export default {
		components:{
			list,
			hd,
			nodata,
			ct
		},
		data() {
			return {
				//全部数据
				list:[
					{
						checked: false,
						content: 'test1',
						id: 'id' + new Date().getTime()
					},{
						checked: true,
						content: "test2",
						id: 'id' + new Date().getTime()
					}
				],
				// listData:[],    //页面展示的数据
				active: false,  //默认隐藏添加todo的输入框
				// value: '',      //添加todo事项的输入框的值
				activeIndex: 0  //右边tab当前所在
			}
		},
		onLoad(e){
			// 接受上个页面传递的参数
			console.log('page-onLoad');
		},
		onShow(){
			// 只要页面出现就会触发
			console.log('page-onShow');
		},
		onReady(){
			// 监听页面初次渲染完成
			console.log('page-onReady');
		},
		onHide(){
			// 监听页面隐藏
			console.log('page-onHide');
		},
		onUnload(){
			// 监听页面卸载
			console.log('page-onUnload');
		},
		methods: {
			create(){
				this.active = true;
			},
			add(value, resetInput){
				console.log(value,'val');
				if(value){
					this.list.unshift({
						checked: false,
						content: value,
						id: 'id'+new Date().getTime()
					})
					this.active= false; //收起输入框
					resetInput && resetInput();
				}else{
					uni.showToast({
						title: '请输入内容',
						icon: 'none'
					})
				}
			},
			
			// 点击代办列表
			finish(id){
				let index = this.list.findIndex((item) => item.id == id);
				this.list[index].checked = !this.list[index].checked;
			},
			
			// 点击右边tab切换
			tab(index){
				this.activeIndex = index;
				console.log(index)
			},
			cancel(){
				this.active = false;
			}
			
			
		},
		computed:{
			listData(){
				const list = JSON.parse(JSON.stringify(this.list));
				let newList = [];
				if(this.activeIndex === 0){
					// 全部数据
					newList = list;
				}else if(this.activeIndex === 1){
					// 代办
					list.forEach(item => {
						if(!item.checked){
							newList.push(item);
						}
					})
					
				}else if(this.activeIndex === 2){
					// 已完成
					list.forEach(item => {
						if(item.checked){
							newList.push(item);
						}
					})
				}
				return newList;
			}
		}
		
		
		// 页面生命周期
		// 从 a -> b(a页面中通过路由跳转到b页面)
		// 1.a onHide
		// 2.b onLoad onShow onReady
		
		// 从 b -> a(通过返回按钮回到a页面)
		// 1.b onUnload
		// 2.a onShow
		
			
	}
</script>

<style>
	@import "../../common/icon.css";
	.bj{
		font-size:24px;
	}
	.c{
		color: red;
	}
	
	
	.todo-content{
		position: relative;
		/* padding: 10px; */
		padding-top: 50px;
		padding-bottom: 100px;
	}
	.todo-list{
		display: flex;
		position: relative;
		align-items: center;
		background-color: #cfebfd;
		margin: 10px;
		padding: 10px;
		color: #0c3854;
		border-radius: 7px;
		box-shadow: -1px 1px 5px 1px rgba(0,0,0,0.1);
		overflow: hidden;
	}
	.todo-list::after{
		position: absolute;
		content: '';
		left: 0;
		top: 0;
		bottom: 0;
		width: 5px;
		background-color: #91d1e8;
		display: block;
	}
	.todo-list-checkbox{
		width: 12px;
		height: 12px;
		border-radius: 50%;
		background-color: #fff;
		margin-left: 10px;
		box-shadow: 0 0 5px 1px rgba(0,0,0,0.1) -1px 2px 1px 0 rgb(255,255,255) inset;
	}
	.todo-list-content{
		padding-left: 8px;
		font-size: 12px;
	}
	.todo-finish .todo-list-checkbox{
		position: relative;
		background-color: #eee;
	}
	.todo-finish .todo-list-checkbox:after{
		position: absolute;
		content: '';
		width: 10px;
		height: 10px;
		top: 0;
		left: 0;
		bottom: 0;
		right: 0;
		margin: auto;
		background-color: #CFEBFD;
		border-radius: 50%;
		box-shadow: 0 0 2px 0 rgba(0,0,0,0.2) inset;
	}
	.todo-finish .todo-list-content{
		color: #999999;
	}
	.todo-finish.todo-list:after{
		background: #ccc;
	}
	.todo-finish.todo-list:before{
		content: '';
		position: absolute;
		top: 0;
		left: 30px;
		right: 10px;
		bottom: 0;
		height: 2px;
		margin: auto 0;
		display: block;
		background: #bdcdd8;
	}
	
	
	
</style>
