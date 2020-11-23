<template>
	<view v-else class="default">
		<view class="image-default">
			<image src="@/static/default.jpeg" mode="aspectFit"/>
		</view>
		<view class="default-info">
			<view class="default-info_text">您还没有创建任何代办事项</view>
			<view class="default-info_text">点击下方+号创建一个吧</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	.default{
		padding-top: 20px;
	}
	
	.default-info{
		text-align: center;
		font-size: 14px;
		color: #ccc;
	}
</style>
