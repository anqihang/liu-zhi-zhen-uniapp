<template>
	<view style="box-sizing:border-box;display:flex;flex-direction: column; #f2f2f2;height: 100vh;position: relative;border-top: 15rpx solid #919191;background-color:#f2f2f2;">
		<van-nav-bar
			title="患者详情"
			left-arrow
			@click-left="clickLeft"
			@click-right="clickRight"
		>
			<view class="rightIcon" slot="right">
				<image :mode="aspectFix" src="../../static/edit.svg"></image>
			</view>
		</van-nav-bar>
		<view class="screen">
			<view class="title">
				<view class="f">
					<view class="name">{{patientInfo.name}}</view>
					<view class="change">换绑设备</view>
				</view>
				<view class="s">
					<view>{{patientInfo.room}}房</view>
					<view>{{patientInfo.bed}}床</view>
				</view>
				<view class="t">
					<view>{{patientInfo.sex}}</view>
					<view></view>
					<view>{{patientInfo.height}}cm</view>
					<view></view>
					<view>{{patientInfo.weight}}kg</view>
				</view>
			</view>
			<view class="scroll">
				<scroll-view class="scroll-y" show-scrollbar="false" scroll-y="true">
					<view class="piece" v-for="(item,index) in list" :key="index">
						<view class="date">
							<view class="f">{{item.date}}</view>
							<view>{{item.time}}</view>
						</view>
						<view class="temperature">
							<text class="tem" :class="{red:item.tem>boundaries}">{{item.tem}}</text>
							<text>℃</text>
						</view>
					</view>
				</scroll-view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				boundaries:'37.5',
				patientInfo:{
					id:'',
					name:'张三',
					room:'701',
					bed:'A5',
					sex:'男',
					height:'175',
					weight:'65',
				},
				list:[
					{
						date:'11/02',
						time:'16:04',
						tem:'39.7'
					},
					{
						date:'11/02',
						time:'16:04',
						tem:'36.6'
					},
					{
						date:'11/02',
						time:'16:04',
						tem:'36.2'
					},
					{
						date:'11/02',
						time:'16:04',
						tem:'36.8'
					},
					{
						date:'11/02',
						time:'16:04',
						tem:'38.9'
					},
					{
						date:'11/02',
						time:'16:04',
						tem:'37.0'
					},
					{
						date:'11/02',
						time:'16:04',
						tem:'36.7'
					},
					{
						date:'11/02',
						time:'16:04',
						tem:'39.4'
					},
					{
						date:'11/02',
						time:'16:04',
						tem:'36.7'
					}
				]
			};
		},
		onLoad(){
			const eventChannel = this.getOpenerEventChannel()
			eventChannel.on('getPatientId',(data)=>{
				this.patientInfo.id = data.id;
			})
		},
		methods:{
			clickLeft(){
				uni.navigateBack({
					delta:1
				})
			}
		}
	}
</script>

<style lang="scss">
	.red{
		color:red;
	}
.custom-class{
	padding: 0!important;
}
.van-nav-bar{
	padding: 0!important;
}
.rightIcon{
	height: 100%;
	width: 40rpx;
	image{
		width:100%;
		height:100%;
	}
}
.screen{
	box-sizing: border-box;
	height: 100%;
	margin: 25rpx;
	background-color: #ffffff;
	border-radius: 20rpx;
	display: flex;
	flex-direction: column;
	.title{
		display: flex;
		flex-direction: column;
		margin: 40rpx 40rpx 0;
		padding-bottom: 30rpx;
		border-bottom: 1px solid #f2f2f2;;
		// background-color: pink;
		.f{
			display: flex;
			justify-content: space-between;
			align-items: center;
			.name{
				font-size:25rpx;
			}
			.change{
				color:#0081fd;
			}
		}
		.s{
			display: flex;
			margin-top: 3rpx;
			view{
				padding:2rpx 6rpx;
				background-color: #e6e6e6;
				margin-right: 6rpx;
			}
		}
		.t{
			margin-top: 10rpx;
			display: flex;
			align-items: center;
			view{
				color:#c1c1c1;
			}
			view:nth-child(even){
				width: 0;
				height:10rpx;
				border-right: 1px solid gray;
				margin: 0 7rpx;
			}
		}
	}
	.scroll{
		flex:1;
		margin:17rpx 40rpx;
		overflow: hidden;
		.scroll-y{
			height: 700rpx;
			overflow: hidden;
			.piece{
				height: 80rpx;
				// width:100%;
				background-color: #f7f7f7;
				border-radius: 7rpx;
				display: flex;
				justify-content: space-between;
				align-items: center;
				padding: 0 8rpx;
				margin-bottom: 10rpx;
				
				.date{
					display: flex;
					.f{
						margin-right: 5rpx;
					}
					
				}
				.temperature{
					.tem{
						font-size: 40rpx;
					}
				}
			}
		}
	}
}
</style>
