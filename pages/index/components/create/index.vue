<template>
	<view>
		<view class="create-todo" @click="create">
			<text class="iconfont icon-jia"></text>
		</view>
		<view class="create-todo" @click="cancel" v-show="active">
			<text class="iconfont icon-jinakangbaoicons18"></text>
		</view>
		<view v-if="active" class="create-content">
			<view class="create-input">
				<input type="text" value="" v-model="value" placeholder="请输入您要创建的todo">
			</view> 
			<view class="create-button" @click="add">创建</view>
		</view>
	</view>
</template>

<script>
	export default{
		name: 'createTodo',
		props:{
			active: {
				type: Boolean,
				required: true
			}
		},
		data(){
			return{
				value: ''
			}
		},
		methods:{
			create(){
				this.$emit('create');
			},
			cancel(){
				this.$emit('cancel');
			},
			add(){
				this.$emit('add', this.value,this.resetInput);
				
			},
			resetInput(){
				this.value = ''; //清空input
			}
			
		}
	}
</script>

<style>
	.create-todo{
		display: flex;
		align-items: center;
		justify-content: center;
		position: fixed;
		bottom: 20px;
		/* top: 0; */
		left: 0;
		right: 0;
		margin: 0 auto;
		/* border: 1px solid red; */
		width: 30px;
		height: 30px;
		border-radius: 50%;
		background-color: #deeff5;
		box-shadow: -1px 1px 5px 2px rgba(0,0,0,0.1),-1px 1px 1px 0 rgba(255,255,255) inset;
		
	}
	
	.icon-jia,.icon-jinakangbaoicons18{
		font-size: 30px;
		color: #add8e6;
		cursor: pointer;
	}
	
	.create-content{
		display: flex;
		align-items: center;
		position: fixed;
		bottom: 95px;
		left: 20px;
		right: 20px;
		padding: 0 0px 0 15px;
		border-radius: 50px;
		background-color: #FFFFFF;
		box-shadow: -1px 1px 5px 2px rgba(0,0,0,0.1);
	}
	
	.create-content:after{
		position: fixed;
		right: 50%;
		bottom: 75px;
		content: '';
		width: 0px;                 /*  宽高设置为0，很重要，否则达不到效果 */
		height: 0px;
		border: 10px solid #88d4ec;
		border-bottom-color: transparent;    /* 设置透明背景色 */
		border-left-color: transparent;
		border-right-color: transparent;
	}
	
	.create-input{
		width: 100%;
		padding-right: 15px;
		font-size: 12px;
	}
	.create-button{
		display: flex;
		align-items: center;
		justify-content: center;
		flex-shrink: 0;
		width: 50px;
		height: 30px;
		border-radius: 20px;
		font-size: 16px;
		color: #88d4ec;
		background-color: #555555;
	}
	
</style>
