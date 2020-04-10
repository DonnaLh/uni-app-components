<template>
	<view class="content">
		<dropDownMenu>
			<drop-down-item  v-model="type" :options="list"/>
			<drop-down-item  v-model="type" :options="list" icon-type="arrow"/>
			<drop-down-item :onCloseModal="false"  :options="list1"/>
			<drop-down-item :modal="false" activeColor="red" :options="list"/>
		</dropDownMenu>
	</view>
</template>

<script>
	import dropDownMenu from './lh-drowdown-menu'
	import dropDownItem from './lh-drowdown-item'
	export default {
		data() {
			return {
				title: 'Hello',
				type: 2,
				list: [
					{
						text: '全部商品',
						value: 1
					},
					{
						text: '新款商品',
						value: 2
					},
					{
						text: '活动商品',
						value: 3
					}
				],
				list1: [
					{
						text: '测试1',
						value: 1
					},
					{
						text: '测试2',
						value: 2
					},
					{
						text: '测试3',
						value: 3
					}
				],
			}
		},
		components: {
			dropDownMenu, dropDownItem
		},
		methods: {
		},
		mounted() {
		},
	}
</script>

<style lang="scss">
	@import './font.scss';
</style>
