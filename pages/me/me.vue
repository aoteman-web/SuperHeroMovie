<template>
	<view class="page page-fill">
		<view class="header">
			<view v-if="userIsLogin">
				<image :src="userInfo.faceImage" class="face"></image>
			</view>
			
			<view v-else>
				<image src="http://122.152.205.72:88/group1/M00/00/05/CpoxxFw_-5-AFyVyAABLIH8xBTw233.png" class="face"></image>
			</view>
			
			<view class="info-wapper" v-if="userIsLogin">
				<view class="nickname">
					{{userInfo.nickname}}
				</view>
				<view class="nav-info">
					{{userInfo.id}}
				</view>
			</view>
			
			<view v-else>
				<navigator url="../registLogin/registLogin">
					<view class="nickname regist-login">
						注册/登录
					</view>
				</navigator>
			</view>
			<view class="set-wapper" v-if="userIsLogin">
				<navigator url="../settings/settings">
					<image src="../../static/icon/Settings.png" class="settings"></image>		
				</navigator>
			</view>	
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userIsLogin:false,
				userInfo:{}
			}
		},
		onShow() {
			// 用户状态的切换
			// var userInfo = uni.getStorageSync("globalUser")
			// if(userInfo != null && userInfo != "" && userInfo != undefined) {
			// 	this.userIsLogin = true
			// 	this.userInfo = userInfo
			// } else{
			// 	this.userIsLogin = false,
			// 	this.userInfo = {}
			// }
			
			// 使用挂载方法获取用户数据
			var userInfo = this.getGlobalUser("globalUser")
			if(userInfo != null) {
				this.userIsLogin = true
				this.userInfo = userInfo
			} else{
				this.userIsLogin = false,
				this.userInfo = {}
			}
		},
		methods: {
			
		}
	}
</script>

<style>
@import url("me.css");
</style>
