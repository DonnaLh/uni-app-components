<template>
    <view :style="{'padding': padding}" class="book-tab-wrapper">
        <view class="tab-title-wrapper">
            <view class="book-tab" :style="{'width': width,'justifyContent': justifyContent, 'padding': paddingTitle}">
                <text class="book-tab-item" :class="{'active': activeType===item.type}"
                      v-for="item in tabsTitle"
                      :key="item.type"
                      @tap="tabChange(item)">
                    {{item.name}}
                    <text v-if="activeType===item.type" :style="{'height': lineHeight}" class="active-line"/>
                </text>
            </view>
        </view>
        <view :style="{'padding': paddingContent}" class="tab-content">
            <slot></slot>
        </view>
    </view>
</template>

<script>
    export default {
        name: "tabs",
        props: {
            tabsTitle: {
                defalut: ()=>[],
                type: Array
            },
            width: {
                default: '690rpx',
                type: String
            },
            value: {
                default: 1,
                type: [String, Number]
            },
            padding: {
                default: '30rpx',
                type: String
            },
            paddingContent: {
                default: '0',
                type: String
            },
            paddingTitle: {
                default: '0',
                type: String
            },
            justifyContent: {
                defalut: 'space-between',
                type: String
            },
            lineHeight: {
                defalut: '2rpx',
                type: String
            }
        },
        data(){
            return{
                activeType: ''
            }
        },
        methods: {
            tabChange(item){
                this.activeType = item.type;
                this.$emit('input', item.type);
                this.$emit('tabChange', item);
            }
        },
        mounted(){
            this.activeType= this.value
        }
    }
</script>

<style scoped lang="scss">
    .book-tab-wrapper{
        box-sizing: border-box;
        width: 100%;
        overflow-x: hidden;
    }
    .tab-title-wrapper{
        overflow-x: auto;
        padding-bottom: 10rpx;
    }
    .book-tab {
        display: flex;
        justify-content: space-between;
        box-sizing: border-box;
        font-size:28rpx;
        color:rgba(153,153,153,1);
        overflow-x: auto;
        &-item{
            position: relative;
            .active-line{
                position: absolute;
                width:50%;
                height:2rpx;
                background:#2BA8FC;
                border-radius:4rpx;
                top: 50rpx;
                left: 50%;
                transform: translateX(-50%);
            }
        }
        .active{
            font-size:32rpx;
            font-weight:bold;
            color:#2BA8FC;
        }
    }
</style>