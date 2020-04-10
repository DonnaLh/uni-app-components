<template>
	<view class="content">
		<dropDownMenu @close="close">
			<drop-down-item  v-model="type" :options="list"/>
			<drop-down-item :onCloseModal="false"  :options="list1"/>
			<drop-down-item :modal="false" activeColor="red" :options="list"/>
		</dropDownMenu>
		<cardTabs
				:tabsTitle="tabsTitle"
				v-model="type"
		>

		</cardTabs>

	</view>
</template>

<script>
	import cardTabs from '../components/lh-card-tabs/lh-card-tabs'
	import dropDownMenu from '../components/lh-dropdown/lh-drowdown-menu'
	import dropDownItem from '../components/lh-dropdown/lh-drowdown-item'
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
			cardTabs, dropDownMenu, dropDownItem
		},
		onLoad() {

		},
		methods: {
			tabChange(item){
			},
			closeDropdown(){
			}
		},
		mounted() {
			this.$on('close', ()=>{
			})
		},
	}
</script>

<style lang="scss">
	@import '../components/lh-dropdown/font.scss';
	.content {
		background: #fafafa;
		height: 1000rpx;
	}
</style>
