<template>
	<view class="u-page">
		<!-- 2.0.19支持autoBack，默认为false -->
		<u-navbar title="xxshop" safeAreaInsetTop fixed placeholder>
			<view slot="left">
			</view>
		</u-navbar>
		<view class="u-content">
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
			}
		},
		mounted() {

		},
		methods: {
			tabChanged(t) {
				console.log(t)
				this.tabIndex = t
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
		background-color: $u-bg-color;

		.u-content {
			background-color: aquamarine;
			
		}

	}
</style>