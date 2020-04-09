#### 简述： tab切换，title和content可以动态配置
- 使用方式，参考example.vue
- 文档说明

-属性：
tabsTitle： 标题列表 Array 格式 [{ type: 1, name: '已生效'}]
v-model: 当前激活的type值, String, Number
padding: tab的padding值， String
paddingContent: 内容的padding值，默认值 0， String
paddingTitle: 内容的padding值，默认值 0， String

-事件
@tabChange 返回tabsTitle中的每一项
