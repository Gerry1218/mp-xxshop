<template>
	<view class="u-page">
		<!-- 2.0.19支持autoBack，默认为false -->
		<u-navbar title="xxshop" bg-color="#fae255" safeAreaInsetTop fixed placeholder>
			<view slot="left">
			</view>
		</u-navbar>
		<view class="u-content">
			<view class="u-item" v-for="(item, index) in indexList" :key="index" @click="itemClicked">
				<view class="u-user">
					<u-avatar :src="item.url"></u-avatar>
					<text>招聘速报</text>
				</view>
				<view>
					<text>甘肃省事业单位招聘信息，涉及武威市、嘉峪关市，甘肃省事业单位招聘啦</text>
				</view>
				<view>
					<image src="../../static/logo.png">
				</view>
				<view class="u-tools">
					<view class="u-tools-item" @click.stop="shareClicked">
						<u-icon name="share"></u-icon>
						<u--text text="分享"></u--text>
					</view>
					<view class="u-tools-item" @click.stop="commentClicked">
						<u-icon name="chat"></u-icon>
						<u--text text="评论"></u--text>
					</view>
					<view class="u-tools-item" @click.stop="zanClicked">
						<u-icon name="thumb-up"></u-icon>
						<u--text text="173"></u--text>
					</view>
				</view>
			</view>
		</view>

		<u-tabbar :value="tabIndex" :placeholder="false" @change="tabChanged" :fixed="true" :safeAreaInsetBottom="true">
			<u-tabbar-item text="首页" icon="home" dot></u-tabbar-item>
			<u-tabbar-item text="放映厅" icon="photo" badge="3"></u-tabbar-item>
			<u-tabbar-item text="直播" icon="play-right"></u-tabbar-item>
			<u-tabbar-item text="我的" icon="account"></u-tabbar-item>
		</u-tabbar>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				tabIndex: 1,
				indexList: [],
				urls: [
					'https://cdn.uviewui.com/uview/album/1.jpg',
					'https://cdn.uviewui.com/uview/album/2.jpg',
					'https://cdn.uviewui.com/uview/album/3.jpg',
					'https://cdn.uviewui.com/uview/album/4.jpg',
					'https://cdn.uviewui.com/uview/album/5.jpg',
					'https://cdn.uviewui.com/uview/album/6.jpg',
					'https://cdn.uviewui.com/uview/album/7.jpg',
					'https://cdn.uviewui.com/uview/album/8.jpg',
					'https://cdn.uviewui.com/uview/album/9.jpg',
					'https://cdn.uviewui.com/uview/album/10.jpg',
				]
			}
		},
		mounted() {
			this.loadmore()
		},
		methods: {
			tabChanged(t) {
				console.log(t)
				this.tabIndex = t
			},
			loadmore() {
				for (let i = 0; i < 30; i++) {
					this.indexList.push({
						url: this.urls[uni.$u.random(0, this.urls.length - 1)]
					})
				}
			},
			itemClicked() {
				console.log("itemClicked")
			},
			shareClicked() {
				console.log("shareClicked")
			},
			commentClicked() {
				console.log("commentClicked")
			},
			zanClicked() {
				console.log("zanClicked")
			}
		}
	}
</script>

<style lang="scss">
	/* #ifndef APP-NVUE */
	page {
		background-color: $u-bg-color;
	}

	/* #endif */

	.u-page {
		padding: 0;
		flex: 1;
		background-color: #FAE255;

		.u-content {
			background-color: white;
			padding-bottom: 88px;

			.u-item {
				.u-user {
					display: flex;
					flex-direction: row;
				}

				.u-tools {
					display: flex;
					flex-direction: row;
					justify-content: space-around;

					.u-tools-item {
						display: flex;
						flex-direction: row;
					}

				}
			}
		}

	}
</style>