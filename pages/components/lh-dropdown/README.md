#### 简述： tab切换，title和content可以动态配置
- 使用方式，参考example.vue  
- 大概功能描述  
1、可以设置多个项，每个项互相不影响  
2、可以对字体大小、行高、字体颜色、选中字体颜色、箭头样式进行修改  
- 文档说明    

-属性：    
# 具体属性说明，随后补  
-lh-down-menu 属性说明 
height: 高度  
lineHeight： 行高  
-lh-down-item 属性说明  
v-model 当前选项对应的value  
options: 选项数组 Array  
fontSize: 字体大小 String  
color: 字体颜色 String  
modal: 是否显示遮罩 Boolean  
onCloseModal: 点击遮罩是否可以关闭菜单栏 Boolean  
activeColor： 选中项的字体颜色 String  
iconType： 箭头类型，支持实心箭头和空箭头 String('solid-arrow'(默认), 'arrow')  
-事件    
@tabChange 返回tabsTitle中的每一项    
