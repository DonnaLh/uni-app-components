<template>
	<div class="dropdown-menu">
		<slot></slot>
	</div>
</template>

<script>
	export default {
		data() {
			return {
			}
		},
		mounted() {
			this.$on('close', this.closeDropdown)
		},
		methods: {
			closeDropdown() {
				console.log(8912)
				this.$children.forEach(item =>{
					item.close();
				})
			}
		}
	}
</script>

<style lang="scss">
	.dropdown-menu {
		display: flex;
		overflow: auto;
		white-space: nowrap;
	}
	dropdown-item {
		flex: 1;
	}
</style>
