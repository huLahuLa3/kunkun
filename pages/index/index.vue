<template>
	<view>
		<view style="width: 100%;height: 400rpx;position: fixed;z-index: 1;">
			<video class="videoCss" src="/static/video/cxk.mp4" @error="errorMessage" controls :autoplay="false" :loop="true"></video>
		</view>
		<view style="height: 100%;width: 100%; background-color: red;display: flex;padding-top: 400rpx;">
			<view class="audioLeft">
				<scroll-view scroll-y="true">
					<view style="width: 100%;height: 400rpx;">
						<button v-for="(item, index) in jiListL" @click="playAudio(item.src)" type="primary">{{ item.name }}</button>
					</view>
				</scroll-view>
			</view>
			<view class="audioRight">
				<scroll-view scroll-y="true">
					<view style="width: 100%;height: 400rpx;">
						<button v-for="(item, index) in niList" @click="playAudio(item.src)" type="primary">{{ item.name }}</button>
					</view>
				</scroll-view>
			</view>
		</view>
		<view class="stopAudio"><button type="warn" @click="playStop">停止</button></view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			innerAudioContext: {},
			isPlay: true,
			BGMSRC: 'http://attachment.0sm.com/node0/2022/07/862C65F0453C9304-41a547ebe1e12776.mp3',
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
					src: '	http://attachment.0sm.com/node0/2022/07/862C697504368994-bafa959f71fa58c8.mp3'
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
			this.innerAudioContext.loop = true;
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
