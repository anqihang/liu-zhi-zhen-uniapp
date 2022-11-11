<template>
	<view
		style="box-sizing:border-box;display:flex;flex-direction: column; #f2f2f2;height: 100vh;position: relative;border-top: 15rpx solid #919191;background-color:#f2f2f2;">
		<van-nav-bar @click-left="toScan" title="绑定患者" left-arrow></van-nav-bar>
		<view class="screen">
			<view class="screen__item">
				<view class="title">
					<view class="icon">
						<image src="../../static/设置齿轮.svg"></image>
					</view>
					<view class="id">
						<view class="name">蓝牙留置针</view>
						<view class="mac">{{id}}</view>
					</view>
				</view>
				<view class="info">
					<view class='form'>
						<form>
							<label for="name">患者姓名</label>
							<input class="input0" type="text" id="name" placeholder="请输入姓名"
								v-model:value="patientInfo.name">
							<!-- <label for="">性别</label> -->
							<view class="uni-title uni-common-mt">性别</view>
							<view class="sex">
								<checkbox-group>
									<label style="margin-right: 60rpx;">
										<checkbox style="margin-right:18rpx;" value="male" />男
									</label>
									<label>
										<checkbox style="margin-right:18rpx;" value="female" />女
									</label>
								</checkbox-group>
							</view>

							<label for="height">身高</label>
							<input class="input0" type="text" id="height" placeholder="请输入身高"
								v-model:value="patientInfo.height">
							<label for="weight">体重</label>
							<input class="input0" type="text" id="weight" placeholder="请输入体重"
								v-model:value="patientInfo.weight">
							<view class="select">
								<view>
									房号
									<van-dropdown-menu>
										<van-dropdown-item :value='value1' :options="room">
											</van-dropdown-item>
									</van-dropdown-menu>					
								</view>

								<view>
									床号
									<van-dropdown-menu>
										<van-dropdown-item :value='value2' :options="bed"></van-dropdown-item>
									</van-dropdown-menu>
								</view>
							</view>
						</form>
					</view>
					<view class="bottom">完成并绑定设备</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				id: '',
				patientInfo: {
					name: '张三',
					sex: 'man',
					height: '175',
					weight: '66',
					room: '701',
					bed: 'A5',
				},
				room: [{
						text: '701房',
						value: 0
					},
					{
						text: '702房',
						value: 1
					},
					{
						text: '703房',
						value: 2
					},
					{
						text: '704房',
						value: 3
					},
				],
				bed: [{
						text: 'A5床',
						value: 0
					},
					{
						text: 'A6床',
						value: 1
					},
					{
						text: 'A7床',
						value: 2
					},
					{
						text: 'A8床',
						value: 3
					},
				],
				value1:0,
				value2:0,
			};
		},
		onLoad() {
			const eventChannel = this.getOpenerEventChannel();
			eventChannel.on('getDeviceId', (data) => {
				this.id = data.id;
				console.log(data);
			})
		}
	}
</script>

<style lang="scss" scoped>
	/deep/.van-dropdown-menu__title{
		width:100%;
	}
	/deep/.van-dropdown-menu__title:after{
		right:20rpx;
	}
	/deep/.van-dropdown-menu {
		height: 40rpx;
		border-radius: 10rpx;
		box-shadow: none;
		background-color: #f2f2f2;
	}

	/deep/.van-dropdown-menu__item {
		justify-content: space-between !important;
	}

	/deep/.van-ellipsis {}

	/deep/.van-nav-bar {
		padding: 0 !important;
		background-color: #c2c2c2 !important;
	}

	.screen {
		box-sizing: border-box;
		flex: 1;
		height: 100%;
		width: 100%;
		padding: 20rpx;

		&__item {
			border-radius: 10rpx;
			height: 100%;
			background-color: #ffffff;
			position: relative;
			border: 1px solid transparent;
			position: relative;
			.title {
				box-sizing: border-box;
				margin: 37rpx 37rpx 0;
				padding-bottom: 30rpx;
				border-bottom: 1px solid #ececec;
				display: flex;
				align-items: center;

				.icon {
					margin-right: 30rpx;
					height: 80rpx;
					width: 80rpx;

					image {
						width: 100%;
						height: 100%;
					}
				}

				.id {
					.name {
						font-size: 24rpx;
					}

					mac {
						font-size: 14rpx;
						color: #adadad;
					}
				}
			}

			.form {
				margin: 30rpx 37rpx;

				.input0 {
					width: 100%;
					height: 40rpx;
					background-color: #f2f2f2;
					border-radius: 10rpx;
					padding-left: 10rpx;
					margin: 5rpx 0 15rpx 0;
					box-sizing: border-box;
				}

				.sex {
					margin: 15rpx 0 30rpx 0;
				}

				.select {
					display: flex;
					justify-content: space-between;
					view {
						width: 48%;

						select {
							height: 40rpx;
							line-height: 40rpx;
							background-color: #f2f2f2;
							border-radius: 10rpx;
							// padding-left: 10rpx;
						}
					}
				}
			}
			.bottom{
				position: absolute;
				bottom: 20rpx;
				left: 0;
				right: 0;
				margin: 0 auto;
				background-color: #9b9b9b;
				width: 400rpx;
				height:40rpx;
				color:#ffffff;
				text-align: center;
			}
			
		}
	}
</style>
