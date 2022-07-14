<template>
	<view>
		<view style="width: 100%;height: 400rpx;position: fixed;z-index: 1;">
			<video class="videoCss" :src="defaultSrc" controls :autoplay="false" :loop="true"></video>
			<button style="position: absolute;top: 0;right: 0; z-index: 2;opacity: 0.5;border-radius: 10rpx;" type="default" @click="chooseVideos" size="mini">更换视频</button>
		</view>
		<view style="height: 100%;width: 100%; display: flex;padding-top: 400rpx;">
			<view class="audioLeft"><buttons :list="jiListL" ref="buttonsRef1"></buttons></view>
			<view class="audioRight"><buttons :list="niList" ref="buttonsRef2"></buttons></view>
		</view>
		<view class="stopAudio"><button type="warn" @click="playStop">停止</button></view>
	</view>
</template>

<script>
import buttons from '../../components/buttons/buttons.vue';
export default {
	components: {
		buttons
	},
	data() {
		return {
			innerAudioContext: {},
			isPlay: true,
			BGMSRC: 'http://attachment.0sm.com/node0/2022/07/862C65F0453C9304-41a547ebe1e12776.mp3',
			defaultSrc: 'static/video/cxk.mp4',
			jiListL: [
				{
					name: '鸡你太美(版本1)',
					src: 'http://attachment.0sm.com/node0/2022/07/862C65EB4C14D7A4-45a533be03e49cb1.mp3'
				},
				{
					name: '鸡你太美(版本2)',
					src: 'http://attachment.0sm.com/node0/2022/07/862C65EB5EABCBAA-cd1c9424dec0cb58.mp3'
				},
				{
					name: '鸡你太美(版本3)',
					src: 'http://attachment.0sm.com/node0/2022/07/862C69625EBC5B75-43472fa74839079e.mp3'
				},
				{
					name: '鸡你太美(版本4)',
					src: 'http://attachment.0sm.com/node0/2022/07/862C696CD249F0FF-b78f6591fa060fa1.mp3'
				},
				{
					name: '鸡你太美(版本5)',
					src: 'http://attachment.0sm.com/node0/2022/07/862C696ED0BD08D7-115910793760e7e9.mp3'
				},
				{
					name: '鸡你太美(版本6)',
					src: 'http://attachment.0sm.com/node0/2022/07/862C69704DEE937E-43c22aefccc82c61.mp3'
				},
				{
					name: '鸡你太美(版本7)',
					src: 'http://attachment.0sm.com/node0/2022/07/862C6971DC34D5F4-3314053c034f4f9c.mp3'
				}
			],
			niList: [
				{
					name: '你干嘛(版本1)',
					src: 'http://attachment.0sm.com/node0/2022/07/862C69736A052820-bcb52db7f11beac5.mp3'
				},
				{
					name: '你干嘛(版本2)',
					src: 'http://attachment.0sm.com/node0/2022/07/862C697504368994-bafa959f71fa58c8.mp3'
				},
				{
					name: '你干嘛(版本3)',
					src: 'http://attachment.0sm.com/node0/2022/07/862C69765EC908DE-6f5204b415b0ef55.mp3'
				},
				{
					name: '你干嘛(版本4)',
					src: 'http://attachment.0sm.com/node0/2022/07/862C69778359FB26-9e0e1fba1034926e.mp3'
				},
				{
					name: '你干嘛(版本5)',
					src: 'http://attachment.0sm.com/node0/2022/07/862C6978CEA163DF-66721967646c1e50.mp3'
				}
			]
		};
	},
	created() {},
	mounted() {},
	methods: {
		playStop() {
			this.$refs.buttonsRef1.playStop();
			this.$refs.buttonsRef2.playStop();
		},
		chooseVideos() {
			uni.chooseVideo({
				sourceType: ['album'],
				success: res => {
					console.log(res);
					this.defaultSrc = res.tempFilePath;
				},
				fail: (res) => {
					console.log(res);
				}
			})
		}
	}
};
</script>

<style scoped>
.videoCss {
	width: 100%;
	height: 100%;
}
.stopAudio {
	width: 100%;
	position: fixed;
	bottom: 0;
}
.audioLeft,
.audioRight {
	width: 50%;
	background-color: blue;
}
.audioLeft {
	background-color: blue;
}
</style>
