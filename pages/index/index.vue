<template>
	<view class="u-page">
		<!-- 2.0.19支持autoBack，默认为false -->
		<u-navbar title="xxshop" bg-color="#fae255" safeAreaInsetTop fixed placeholder>
			<view slot="left">
			</view>
		</u-navbar>
		<view class="u-content">
			<view class="u-item" v-for="(item, index) in list" :key="index" @click="itemClicked">
				<view class="u-user">
					<u-avatar :src="item.icon" size="40"></u-avatar>
					<text>{{item.name}}</text>
				</view>
				<view>
					<text>{{item.content}}</text>
				</view>
				<view class="u-img-list" v-for="(img, idx) in item.images" :key="idx">
					<image :src="img" mode="aspectFill">
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
				<u-gap height="1" bg-color="#eee"></u-gap>
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
				list: [
					{
						"name":"铃兰",
						"icon":"https://sns-avatar-qc.xhscdn.com/avatar/64c86133a56eab8eaad1e2dd.jpg?imageView2/2/w/120/format/webp|imageMogr2/strip",
						"content":"柳州徒步登山⛰️无限风光在险峰",
						"images": [
							"http://sns-webpic-qc.xhscdn.com/202309081851/7329492c90eaecfc3918f3932e8530b5/1040g00830oob14qgj8005p1u6cb3jkidk3kaj6o!nd_whlt34_webp_wm_1"
						]
					},
					{
						"name":"我是慧雯呀",
						"icon":"https://sns-avatar-qc.xhscdn.com/avatar/1040g2jo30oht7fe7iu005p1u6cb3jkidkikpv80?imageView2/2/w/120/format/webp|imageMogr2/strip",
						"content":"生日快乐，处女座♍️",
						"images": [
							"http://sns-webpic-qc.xhscdn.com/202309081842/54912ff79dae7ba10fb0a6116d9f7b2b/1040g00830oj4pplb2e004a452l49a8d5k7k5q58!nc_n_webp_mw_1",
						]
					},
					{
						"name":"一见钟意",
						"icon":"https://sns-avatar-qc.xhscdn.com/avatar/64f96d58c88dbc4568ce543e.jpg?imageView2/2/w/120/format/webp|imageMogr2/strip",
						"content":"南京 奔三了，消息都会回",
						"images": [
							"http://sns-webpic-qc.xhscdn.com/202309081858/a23b7f6565cdbf2931a37a95826c15d4/1040g00830oolroanja0g5p7o6uj14sdjmfab2mg!nd_whlt34_webp_wm_1"
						]
					}
				],
				urls: [
					'https://sns-avatar-qc.xhscdn.com/avatar/6423d843cafb537ac047a998.jpg?imageView2/2/w/120/format/webp|imageMogr2/strip',
					
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
			padding: 10px;
			
			.u-item {
				margin-bottom: 10px;
				.u-user {
					display: flex;
					flex-direction: row;
					margin-bottom: 6px;
				}

				.u-tools {
					margin-top: 6px;
					margin-bottom: 10px;
					display: flex;
					flex-direction: row;
					justify-content: space-around;

					.u-tools-item {
						display: flex;
						flex-direction: row;
					}

				}
				.u-img-list {
					padding: 6px 0 6px 0;
					
				}
			}
		}

	}
</style>