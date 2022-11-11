<template>
	
		<cover-view class="tabbar" :style="{'padding-bottom':paddingBottomHeight+'rpx'}">
			<cover-view class="tabbar-item"
			v-for="(item,index) in list"
			:key="index"
			@click="tabbarChange(item.path)"
			:class="{'activeBgc':current==index}"
			>
			
				<cover-view class="icon"></cover-view>
				<cover-view class="item-name"  v-if="item.text">{{item.text}}</cover-view>
			</cover-view>
		</cover-view>
</template>

<script>
	export default {
		name:"TabBar",
		props:['current'],
		data() {
			return {
				paddingBottomHeight:0,//适配高度
				list:[
					{
						path:'/pages/home/home',
						text:'首页',
					},{
						path:'/pages/search/search',
						text:'寻房测温'
					},{
						path:'/pages/center/center',
						text:'个人中心'
					}
				]
			};
		},
		created(){
			let that =this;
			uni.getSystemInfo({
				success:function(res){
					let model = ['X','XR','XS',
					'11','12','13','14','15'];
					model.forEach(item=>{
						if(res.model.indexOf(item)!=-1&&res.model.indexOf('iPhone')!=-1){
							that.paddingBottomHeight=40;
						}
					})
				}
			})
		},
		methods:{
			tabbarChange(path){
				console.log(path);
				uni.switchTab({
					url:path
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	// .tabbarActive{
	// 	color:#fff!important;
	// }
	.activeBgc{
		background-color: #9b9b9b;
	}
	.tabbar{
		position: fixed;
		bottom: 0;
		left: 0;
		right: 0;
		display: flex;
		justify-content: space-around;
		align-items: center;
		width: 100%;
		height: 46rpx;
		background-color: #c2c2c2;
		.tabbar-item{
			display: flex;
			height: 100%;
			align-items: center;
			justify-content: center;
			width: 100rpx;
			// padding: 0 10rpx;
			.icon{
				height:24rpx;
				width:24rpx;
				border-radius: 12rpx;
				background-color: #fff;
				margin-right:10rpx;
			}
			.item-name{
				font-size: 14rpx;
				color: #ffffff;
			}
		}
	}
</style>