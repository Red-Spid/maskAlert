<template>
	<view>
	
		<view  class="fixed ReturnToZero animation" :style="{opacity:opacity,background:bkColor,'top':top+'%','transition': 'all '+ transition+'s'}" @click="fatherEl"></view>
		
		<view class="MaskTips fixed" :style="{left:0,top:0}">
			<slot name="leftT"></slot>
		</view>
		
		<view class="MaskTips fixed" :style="{left:0,bottom:0}">
			<slot name="leftB"></slot>
		</view>
		
		<!-- <view class="MaskTips fixed"> -->
			<view class="MaskTipsCenter fixed w-100" :style="{'width':width,'height':height+'upx','top':topCenter+'%','transition': 'all '+ transition+'s'}">
				<slot name="center"></slot>
			</view>
		<!-- </view> -->
		
	</view>
</template>

<script>
export default {
	name:"maskStyle",
	data() {
		return {
			title: 'Hello',
			topCenter:50,
		};
	},
	props:{
		transition:{
			type:[Number,String],
			default:.3
		},
		top:{
			type:[Number,String],
			default:0
		},
		width:{
			type:String,
			default:'300'
		},
		height:{
			type:String,
			default:'300'
		},
		MaskTipsPosition:{
			type:String,
			default:'bottom'
		},
		bkColor:{
			type:String,
			default:'#000'
		},
		
		opacity:{
			type:String,
			default:"0.3",
		}
	},
	mounted() {
		var _self =this;
		console.log(this.top,this.top<=0)
		this.top <= 0 ? this.topCenter = 50 : this.topCenter = 100;
		uni.getSystemInfo({
		    success: function (res) {
		        // console.log(res.model);
		        // console.log(res.pixelRatio);
		        // console.log(res.windowWidth);
		        // console.log(res.windowHeight);
		        // console.log(res.language);
		        // console.log(res.version);
		        // console.log(res.platform);
				// _self.h = res.windowHeight;
		    }
		});
	},
	watch: {
	    // 计算属性的 getter
	    top: function () {
	      // `this` 指向 vm 实例
		   this.top <= 0 ? this.topCenter = 50 : this.topCenter = 100;
	      return this.topCenter
	    }
	 },
	methods: {
		fatherEl:function(){
			this.$emit("click")
		},
		MaskTipsPositionIS:function(){
			
		}
		
	}
};
</script>

<style>

.ReturnToZero {
	left: 0;
	top: 100%;
	width:100%;
	height:100%;
}
.fixed {
	position: fixed;
	z-index:98;
}

.MaskTips{
	z-index:99;
	width:100%;
	height:100%;
	top:0;
	left:0;
	pointer-events:none;
}

.MaskTipsCenter{
	left:50%;
	top:50%;
	width:30%;
	height:300upx;
	transform: translate(-50%,-50%);
}

</style>
