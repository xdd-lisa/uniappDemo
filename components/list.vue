<template>
	<view class='com-list' @click="onClick">
		<list>{{name}}</list>
	</view>
</template>

<script>
	export default {
		props:{
			name: {
				type: String,
				default:''
			}
		},
		data() {
			return {
				
			};
		},
		methods:{
			onClick(){
				this.$emit('click',this.name);
			}
		}
	}
</script>

<style>
	.com-list{
		height: 40px;
		line-height: 40px;
		padding: 0 20px;
	}
</style>
