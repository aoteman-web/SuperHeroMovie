<template name="trailerStars">
	<view class="movie-score-wapper">
		<image 
			v-for="yellow in yellowScore"
			src="../static/icon/yellow-star.png" 
			class="star-ico"></image>
		<image
			v-for="grey in greyScore"
			src="../static/icon/grey-star.png" 
			class="star-ico"></image>
		<view class="movie-score" v-if="showNum == 1">
			{{innerScore}}
		</view>
	</view>
</template>

<script>
	export default {
		name:"trailerStars",
		data() {
			return {
				yellowScore:0,
				greyScore:5
			};
		},
		props:{
			innerScore:0,   // 定义外部传入的分数
			showNum:0		// 是否需要显示具体的分数   1：显示     0：不显示
		},
		// 实例创建完成后被调用
		created() {
			console.log("this.innerscore",this.innerScore)
			
			var tempScore = 0;
			if(this.innerScore != null && this.innerScore != undefined && this.innerScore != ''){
				tempScore = this.innerScore
			}
			
			var yellowScore = parseInt(tempScore / 2)
			var greyScore = 5 - yellowScore
			
			this.yellowScore = yellowScore
			this.greyScore = greyScore
		}
	}
</script>

<style scoped>
.movie-score-wapper{
	display: flex;
	flex-direction: row;
}
.star-ico{
	width: 20upx;
	height: 20upx;
	margin-top: 6upx;
}
.movie-score{
	font-size: 12px;
	color: grey;
	margin-left: 8upx;
}
</style>
