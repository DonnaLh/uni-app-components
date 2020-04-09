<template>
	<view class="content">
		<cardTabs
				:tabsTitle="tabsTitle"
				v-model="type"
		>
			ceshi
		</cardTabs>
	</view>
</template>

<script>
	import cardTabs from './lh-card-tabs'
	export default {
		data() {
			return {
				title: 'Hello',
				type: 2,
				tabsTitle: [
					{
						type: 1,
						name: '已生效'
					},
					{
						type: 2,
						name: '待生效'
					},
					{
						type: 3,
						name: '已失效'
					},
					{
						type: 5,
						name: '已失效'
					},
					{
						type: 4,
						name: '已失效'
					},
				],
			}
		},
		components: {
			cardTabs
		},
		onLoad() {

		},
		methods: {
			tabChange(item){
			},
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
