<template>
    <view class="dropdown-item">
        <view class="drop-item_title"
              :style="{'color': color, 'font-size': fontSize}"
              @click="selectOptions"
        >
            <text>{{title}}</text>
            <text class="iconfont" :class="[showList ? 'up' : 'down', iconType === 'solid-arrow' ? 'icon-xiajiantou' : 'icon-arrow-down']" :style="{'color': color}" style="margin-left: 4rpx;"/>
        </view>
        <view class="drop-item_content" :style="{'top': Number(top)*2+'rpx', 'color': color, 'font-size': fontSize}" v-show="showList">
            <view
                    v-for="(item, index) in options"
                    :key="index"
                    @click="selectHandle(item)"
                    class="drop-item_content-list"
                    :style="{'height': top+'rpx', color: activeIndex === item.value ? activeColor : color}">
               <text>{{item.text}}</text>
               <text v-if="activeIndex === item.value" class="iconfont icon-duigou"/>
            </view>
        </view>
        <view class="mark" @click="closeModal" v-show="showList && modal" :style="{'top': Number(top)*(options.length+2)+'rpx'}"></view>
    </view>
</template>

<script>
    export default {
        data() {
            return {
                title: '',
                showList: false,
                activeIndex: 1,
                active: false
            }
        },
        watch: {
            value(){
                this.init()
            }
        },
        props: {
            value: {
                type: [String, Number],
                default: 1
            },
            options: {
                type: Array,
                default: ()=>[]
            },
            top: {
                type: [String, Number],
                default: '80'
            },
            fontSize: {
                type: String,
                default: '24rpx'
            },
            color: {
                type: String,
                default: '#333333'
            },
            modal: {
                type: Boolean,
                default: true
            },
            onCloseModal: {
                type: Boolean,
                default: true
            },
            activeColor: {
                type: String,
                default: '#1989fa'
            },
            iconType: {
                type: String,
                default: 'solid-arrow' // 两种类型， 实心箭头 solid-arrow，和空箭头 arrow
            }
        },
        methods: {
            init(){
                this.activeIndex = this.value || this.options[0].value
                this.options.forEach(val => {
                    if(val.value === this.value){
                        this.title = val.text
                    }
                })
            },
            close() {
                this.showList = false
            },
            selectOptions(){
                this.active = !this.showList
                this.$parent.$emit('close');
                this.showList = this.active;
            },
            selectHandle(item){
                this.activeIndex = item.value;
                this.title = item.text;
                this.showList = false;
                this.$emit('input', item.value);
            },
            closeSelect(){
                console.log(99)
                if(this.showList) this.showList = false
            },
            closeModal(){
                if(!this.onCloseModal){
                    return
                }
                this.showList = false;
            }
        },
        mounted() {
            this.init();
        }
    }
</script>

<style lang="scss" scoped>
    @import "font.scss";
    .dropdown-item{
        flex: 1;
        .drop-item_title{
            display: flex;
            align-items: center;
            justify-content: center;
            background: #ffffff;
            .down {
                transition: transform .3s;
                transform: rotateZ(0);
            }
            .up {
                transition: transform .3s;
                transform: rotateZ(-180deg);
            }
        }
        .drop-item_content{
            position: fixed;
            width: 100%;
            left: 0;
            right: 0;
            align-items: center;
            z-index: 6;
            transition: 2s;
            &-list{
                display: flex;
                width: 100%;
                box-sizing: border-box;
                padding-left: 30rpx;
                padding-right: 30rpx;
                align-items: center;
                justify-content: space-between;
                background: #ffffff;
                border-top: 1rpx solid #fafafa;
            }
        }
        .mark{
            position: fixed;
            right: 0;
            left: 0;
            bottom: 0;
            z-index: 2;
            background: rgba(0, 0, 0, 0.5);
        }
    }
</style>