<template>
	<!-- 有代办数据时，头部展示数据导航 -->
	<view  class="todo-header">
		<view class='todo-header-left'>
			<text class='todo-header-left-item'>
				
				{{activeIndex === 0? '全部': activeIndex === 1?'待办':'已完成'}}
				
			</text>
			<text>{{listData.length}}条</text>
		</view>
		<view class='todo-header-right'>
			<view class='todo-header-right-item' :class="{'active': activeIndex == 0}" @click="tab(0)">全部</view>
			<view class='todo-header-right-item' :class="{'active': activeIndex == 1}" @click="tab(1)">待办</view>
			<view class='todo-header-right-item' :class="{'active': activeIndex == 2}" @click="tab(2)">已完成</view>
		</view>
	</view>
</template>

<script>
	export default{
		name: 'header',
		props:{
			activeIndex:{
				type: Number,
				required: true
			},
			listData:{
				type: Array,
				required: true
			}
		},
		methods:{
			tab(index){
				this.$emit('tab',index);
			}
		}
	}
</script>

<style>
	.todo-header{
		display: flex;
		height: 45px;
		align-items: center;
		box-shadow: -1px 1px 5px 0 rgba(0,0,0,0.1);
		font-size: 12px;
		color: #333;
		background: #FFFFFF;
		padding: 0 15px;
		position: fixed;
		left: 0;
		top: 0;
		width: 100%;
		z-index: 999;
		box-sizing: border-box;
	}
	.todo-header-left{
		width: 100%;
	}
	.todo-header-left-item{
		padding-right: 3px;
		font-size: 14px;
		color: #007AFF;
	}
	.todo-header-right{
		flex-shrink: 0;
		display: flex;
	}
	.todo-header-right-item{
		padding: 0 5px;
	}
	.active{
		color: #007AFF;
	}
	
</style>
