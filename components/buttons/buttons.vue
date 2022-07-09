<template>
	<view>
		<scroll-view scroll-y="true">
			<view style="width: 100%;height: 400rpx;">
				<button v-for="(item, index) in list" @click="playAudio(item.src)" type="primary">{{ item.name }}</button>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		name:"buttons",
		props: ['list'],
		data() {
			return {
				innerAudioContext: {},
				isPlay: true,
				BGMSRC: 'http://attachment.0sm.com/node0/2022/07/862C65F0453C9304-41a547ebe1e12776.mp3'
			};
		},
		created() {
			this.innerAudioContext = uni.createInnerAudioContext();
		},
		mounted() {
			this.playAudio(this.BGMSRC);
		},
		methods: {
			playAudio(e) {
				console.log(e);
				this.innerAudioContext.stop();
				this.innerAudioContext.src = e;
				this.innerAudioContext.loop = false;
				this.innerAudioContext.sessionCategory = 'soloAmbient';
				this.innerAudioContext.play();
				this.isPlay = false;
			},
			playStop() {
				this.innerAudioContext.stop();
				this.isPlay = true;
			},
			errorMessage(e) {
				console.log(e);
			}
		}
	}
</script>

<style>

</style>