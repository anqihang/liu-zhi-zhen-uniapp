<template>
	<view style="box-sizing:border-box;background-color: #f2f2f2;height: 100vh;position: relative;border-top: 15rpx solid #919191;">
		<van-tabs animated :active="active" @change="onChange" title-active-color="black" line-width="100rpx">
			<van-tab title="今日未测温">
				<view class="showList">
					<view class="block">
						<view class="top">
							<view class="name">
								<view>张三</view>
								<view class="icon">
									<image :mode="aspectFit" src="../../static/箭头 右.svg"></image>
								</view>
							</view>
							<view class="adress">
								<view>701房</view>
								<view>A5床</view>
							</view>
						</view>
						<view class="tem">
							<view class="temperature">
								<text class="noCheck">暂未测温</text>
							</view>
						</view>
					</view>
					<view class="block">
						<view class="top">
							<view class="name">
								<view>李四</view>
								<view class="icon">
									<image :mode="aspectFit" src="../../static/箭头 右.svg"></image>
								</view>
							</view>
							<view class="adress">
								<view>701房</view>
								<view>A5床</view>
							</view>
						</view>
						<view class="tem">
							<view class="temperature">
								<text class="noCheck">暂未测温</text>
							</view>
						</view>
					</view>
					<view class="block">
						<view class="top">
							<view class="name">
								<view>赵五</view>
								<view class="icon">
									<image :mode="aspectFit" src="../../static/箭头 右.svg"></image>
								</view>
							</view>
							<view class="adress">
								<view>701房</view>
								<view>A5床</view>
							</view>
						</view>
						<view class="tem">
							<view class="temperature">
								<text class="noCheck">暂未测温</text>
							</view>
						</view>
					</view>
					<view class="block">
						<view class="top">
							<view class="name">
								<view>陈六</view>
								<view class="icon">
									<image :mode="aspectFit" src="../../static/箭头 右.svg"></image>
								</view>
							</view>
							<view class="adress">
								<view>701房</view>
								<view>A5床</view>
							</view>
						</view>
						<view class="tem">
							<view class="temperature">
								<text class="noCheck">暂未测温</text>
							</view>
						</view>
					</view>
				</view>
			</van-tab>
			<van-tab title="测温记录">
				<view class="showList">
					<view class="block">
						<view class="top">
							<view class="name">
								<view>张三</view>
								<view class="icon" @click="toDetails('01')">
									<image :mode="aspectFit" src="../../static/箭头 右.svg"></image>
								</view>
							</view>
							<view class="adress">
								<view>701房</view>
								<view>A5床</view>
							</view>
						</view>
						<view class="tem">
							<view class="temperature">
								<text class="num">37.7</text>
								<text class="icon">℃</text>
							</view>
							<view class="date">
								<text class="today">今日</text>
								<text class="time">10:40</text>
							</view>
						</view>
					</view>
					<view class="block">
						<view class="top">
							<view class="name">
								<view>李四</view>
								<view class="icon">
									<image :mode="aspectFit" src="../../static/箭头 右.svg"></image>
								</view>
							</view>
							<view class="adress">
								<view>701房</view>
								<view>A5床</view>
							</view>
						</view>
						<view class="tem">
							<view class="temperature" :class="{danger:isDanger}">
								<text class="num">38.9</text>
								<text class="icon">℃</text>
							</view>
							<view class="date">
								<text class="today">今日</text>
								<text class="time">9:40</text>
							</view>
						</view>
					</view>
					<view class="block">
						<view class="top">
							<view class="name">
								<view>张三</view>
								<view class="icon">
									<image :mode="aspectFit" src="../../static/箭头 右.svg"></image>
								</view>
							</view>
							<view class="adress">
								<view>701房</view>
								<view>A5床</view>
							</view>
						</view>
						<view class="tem">
							<view class="temperature">
								<text class="num">37.7</text>
								<text class="icon">℃</text>
							</view>
							<view class="date">
								<text class="today">今日</text>
								<text class="time">10:40</text>
							</view>
						</view>
					</view>
					<view class="block">
						<view class="top">
							<view class="name">
								<view>张三</view>
								<view class="icon">
									<image :mode="aspectFit" src="../../static/箭头 右.svg"></image>
								</view>
							</view>
							<view class="adress">
								<view>701房</view>
								<view>A5床</view>
							</view>
						</view>
						<view class="tem">
							<view class="temperature">
								<text class="num">37.7</text>
								<text class="icon">℃</text>
							</view>
							<view class="date">
								<text class="today">今日</text>
								<text class="time">10:40</text>
							</view>
						</view>
					</view>

				</view>
			</van-tab>
		</van-tabs>
		<view class="scan" @click="toScan">
			<image :mode="aspectFit" src="../../static/scan.svg"></image>
		</view>
		<TabBar :current="0"></TabBar>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				active: '',
				isDanger: true,
			};
		},
		onShow() {
			uni.hideTabBar({
				animation: false
			})
		},
		methods: {
			toScan(){
				uni.navigateTo({
					url:'/pages/scan/scan'
				})
			},
			onChange(event) {
				console.log(1, event);
				//弹出框
				// uni.showToast({
				// 	title:`切换到标签${event.detail.name}`
				// })
			},
			toDetails(id) {
				uni.navigateTo({
					url: '/pages/details/details',
					animationType: "pop-in",
					animationDuration: 1000,
					success(res) {
						res.eventChannel.emit('getPatientId', {
							id
						})
					}
				});
			}
		}
	}
</script>

<style lang="scss">
	.danger {
		color: red;
	}

	.van-ellipsis {
		font-size: 20rpx;
	}

	.van-tabs__wrap {
		background-color: #c2c2c2;
	}

	.van-tabs__scroll {
		background-color: #c2c2c2 !important;
	}

	.van-tabs__nav {
		margin: 0 220rpx;
	}

	.van-tabs__line {
		background-color: #626262 !important;
	}

	.scan {
		width: var(--tabs-line-height, 44px);
		height: var(--tabs-line-height, 44px);
		position: absolute;
		top: 0;
		// right: 0;
		left: 0;
		z-index: 1;

		image {
			width: 100%;
			height: 100%;
		}
	}

	// .van-col{
	// 	display:flex;
	// 	justify-content: center;
	// 	align-items: center;
	// }
	.showList {
		display: flex;
		justify-content: space-evenly;
		flex-wrap: wrap;


		.block {
			display: flex;
			flex-direction: column;
			width: 300rpx;
			height: 150rpx;
			background-color: #ffffff;
			margin: 20rpx 0 0;
			padding: 30rpx 20rpx;
			border-radius: 10rpx;
			justify-content: space-between;

			.top {
				.name {
					display: flex;
					justify-content: space-between;
					font-size: 25rpx;

					.icon {
						width: 25rpx;
						height: 25rpx;
						border-radius: 15rpx;
						background-color: #f2f2f2;
						display: flex;
						justify-content: center;
						align-items: center;

						image {
							width: 80%;
							height: 80%;
						}
					}
				}

				.adress {
					display: flex;
					margin-top: 10rpx;

					view {
						background-color: #e6e6e6;
						margin: 0 10rpx 0 0;
						padding: 2rpx 5rpx;
					}
				}
			}

			.tem {
				display: flex;
				justify-content: space-between;
				align-items: flex-end;

				.temperature {
					.num {
						font-size: 35rpx;
						font-weight: 700;
					}

					.noCheck {
						font-size: 30rpx;
					}

					font-size: 20rpx;
				}

				.date {
					font-size: 20rpx;

					.today {
						margin-right: 10rpx;
					}

					.time {}
				}
			}
		}
	}
</style>
