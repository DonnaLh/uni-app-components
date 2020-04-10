<template>
    <div class="dropdown-menu" :style="{'height': height+'rpx', 'line-height': lineHeight+'rpx'}">
      <slot :top="height"></slot>
    </div>
</template>

<script>
    export default {
        props: {
            height: {
                type: String,
                default: '80'
            },
            lineHeight: {
                type: String,
                default: '80'
            }
        },
        data() {
            return {
                activeItem: false
            }
        },
        methods: {
            closeDropdown() {
                this.$children.forEach(item =>{
                    item.close();
                })
            }
        },
        created() {
            this.$on('close', this.closeDropdown)
        },
    }
</script>

<style lang="scss" scoped>
   .dropdown-menu{
       display: flex;
       background: #ffffff;
       position: relative;
       justify-content: space-between;
   }
</style>
