<template>
	<view class="content">
		
		<button type="default" @click="top = 0 ">弹出遮罩</button>
		
		<maskalert
		opacity=".3"
		bkColor="#000"
		height='300'
		width="300"
		transition="2"
		:top='top'
		@click="computedTop"
		>
			<template v-slot:center>
				<view style="background-color: red;" class="w-100">
					2222 33333
					<view class="">
						sssssss
					</view>
				</view>
			</template>
		
		</maskalert>
		
	</view>
</template>

<script>
	import maskalert from "../../components/maskAlert/maskAlert.vue"
	export default {
		data() {
			return {
				title: 'Hello',
				top:100,
			}
		},
		components:{
			maskalert
		},
		
		onLoad() {

		},
		methods: {
			
			computedTop:function(){
				this.top == 0 ? this.top = 100 : this.top = 0;
			}
		}
	}
</script>

<style>
</style>
