# Frontends 第五轮考核

## 目的

- 掌握组件封装的思想和技巧，拥有编写基础组件的能力
- 熟练使用ES6，SCSS等基本技能
- 深入学习vue3的api和组合化的思想
- 学习使用vitest编写单元测试
- 学习monorepo架构，并学会使用npm进行发包

## 背景

张三是一位喜欢的思考的同学，面对经常遇到的重复的代码，改动起来不方便，这让他掉了不少头发，因此他想自己写一些常用的组件，减少编写重复代码，请帮他设计一些**常用组件**

## 任务

> 请你自己实现一些**常用前端组件**，让张三少写一些代码（少掉一些头发）

至少完成以下几个组件，请结合新的学习内容进行实现，同时你需要完成下面这几个要点

- 完成每个组件的要求
- 每个组件至少包含规定的属性，插槽和事件，可以看情况进行添加更多属性
- 每个组件至少写4组单元测试
- 架构合理，将样式和组件分离，便于打包时分开打包

样式上不要求原创，可以仿照一些组件库的样式

### Button按钮组件

1. 按照配置生成多种样式（大小，颜色，禁用状态）

#### 属性

| 属性名   | 说明               | 类型                                                    | 默认值    |
| :------- | :----------------- | :------------------------------------------------------ | :-------- |
| size     | 尺寸               | `'large'`/`'default'`/`'small'`                         | 'default' |
| type     | 类型               | `'primary'`/`'success'`/`'warning'`/`'danger'`/`'info'` | 'info'    |
| round    | 是否为圆角按钮     | `boolean`                                               | false     |
| disabled | 按钮是否为禁用状态 | `boolean`                                               | false     |

#### 插槽

| 插槽名  | 说明           |
| :------ | :------------- |
| default | 自定义默认内容 |

### Dialog对话框组件

1. 显示对话框时显示遮罩层
2. 对话框始终浮现在页面的最上层，不受绝对定位的影响

#### 属性

| 属性名                | 说明                                                         | 类型                                                         | 可选值 | 默认值 |
| :-------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :----- | :----- |
| model-value / v-model | 是否显示 Dialog                                              | `boolean`                                                    | —      | —      |
| title                 | Dialog 对话框 Dialog 的标题， 也可通过具名 slot 传入         | `string`                                                     | —      | —      |
| before-close          | 关闭前的回调，会暂停 Dialog 的关闭. 回调函数内执行 done 参数方法的时候才是真正关闭对话框的时候 | `Function`(done: () => void) => void (done是一个函数 用来关闭 Dialog) | —      | —      |
| draggable（Bonus）    | 为 Dialog 启用可拖拽功能                                     | `boolean`                                                    | —      | false  |
| lock-scroll（Bonus）  | 在 Dialog 出现时将 body 滚动锁定                             | `boolean`                                                    | —      | true   |

#### 插槽

| 插槽名  | 说明                                          |
| :------ | :-------------------------------------------- |
| default | Dialog 的内容                                 |
| header  | 对话框标题的内容；会替换属性传入的title部分。 |
| footer  | Dialog 按钮操作区的内容                       |

#### 事件

| 事件名 | 说明              | 参数 |
| :----- | :---------------- | :--- |
| open   | Dialog 打开的回调 | —    |
| close  | Dialog 关闭的回调 | —    |

### Checkbox多选框

1. `checkbox`存在受控和非受控状态，绑定值为`Boolean`（当绑定modelValue为受控状态，随modelValue变化而变化，不绑定为非受控状态，存在其内部逻辑控制变化
2. 存在`checkbox-group`组件，`checkbox-group`元素能把多个 checkbox 管理为一组，使用 `v-model` 绑定 `Array` 类型的变量。`checkbox-group`之间可能不是父子关系，因此请使用Provide和Inject进行跨组件传值，
3. `checkbox-group`可以使用 `min` 和 `max` 属性能够限制可以被勾选的项目的数量
4. `checkbox`的实际`disabled`状态取决于其本身的`disabled`属性和`checkbox-group`的`disabled`属性

#### Checkbox属性

| 属性名                | 说明                                                   | 类型      | 默认值 |
| :-------------------- | :----------------------------------------------------- | :-------- | :----- |
| model-value / v-model | 选中项绑定值                                           | `boolean` | —      |
| label                 | 选中状态的值（只有在`checkbox-group`时有效），选项标签 | `string`  | —      |
| checked               | 非受控状态下当前是否勾选                               | `boolean` | false  |
| disabled              | 是否禁用                                               | `boolean` | false  |

#### Checkbox事件

| 事件名 | 说明                     | 类型                              |
| :----- | :----------------------- | :-------------------------------- |
| change | 当绑定值变化时触发的事件 | `Function`(value: string) => void |

#### Checkbox插槽

| 插槽名  | 说明                                      |
| :------ | :---------------------------------------- |
| default | 自定义默认内容，不存在时使用label属性的值 |

#### CheckboxGroup属性

| 属性名                | 说明                           | 类型      | 默认值 |
| :-------------------- | :----------------------------- | :-------- | :----- |
| model-value / v-model | 绑定值                         | string[]  | []     |
| disabled              | 是否禁用                       | `boolean` | false  |
| min                   | 可被勾选的 checkbox 的最小数量 | `number`  | —      |
| max                   | 可被勾选的 checkbox 的最大数量 | `number`  | —      |

#### CheckboxGroup事件

| 事件名 | 说明                     | 类型                                |
| :----- | :----------------------- | :---------------------------------- |
| change | 当绑定值变化时触发的事件 | `Function`(value: string[]) => void |

#### CheckboxGroup插槽

| 插槽名  | 说明           | 子标签   |
| :------ | :------------- | :------- |
| default | 自定义默认内容 | Checkbox |

### Pagination 分页

1. 分页分为受控状态和非受控状态
2. 编写`prev`, `pager`, `next`, `jumper`, `total`五个组件，他们的功能分别是上一页，页码列表，下一页，跳页元素，总条目数，显示顺序按照上述进行排列，相互之间具有联动功能，`pager`和`total`可以直接使用ElementPlus的`Select`和`Input`组件，方便组件编写
3. 总页数过大时，Pagination 应该能折叠多余的页码按钮。 通过 `pager-count` 属性可以设置最大页码按钮数

#### 属性

| 属性名                              | 说明                                                         | 类型             | 默认值                    |
| :---------------------------------- | :----------------------------------------------------------- | :--------------- | :------------------------ |
| page-size / v-model:page-size       | 每页显示条目个数                                             | `number`         | —                         |
| total                               | 总条目数                                                     | `number`         | —                         |
| page-count                          | 总页数， `total` 和 `page-count` 设置任意一个就可以达到显示页码的功能；如果要支持 `page-sizes` 的更改，则需要使用 `total` 属性 | `number`         | —                         |
| pager-count                         | 设置最大页码按钮数。 页码按钮的数量，当总页数超过该值时会折叠 | `number`（奇数） | 7                         |
| page-sizes                          | 每页显示个数选择器的选项设置                                 | `number[]`       | [10, 20, 30, 40, 50, 100] |
| current-page / v-model:current-page | 当前页数                                                     | `number`         | —                         |
| default-page-size                   | 非受控条件时，每页默认的条目个数                             | `number`         | 10                        |
| default-current-page                | 非受控条件时，当前页数的默认初始值                           | `number`         | 1                         |

### Bonus

1. 编写更多的基础组件
1. 使用TypeScript
1. Dialog对话框组件可拖拽
1. Dialog对话框组件可锁定滚动条
1. Checkbox多选框实现中间状态
1. Pagination分页监听实现对`prev`, `pager`, `next`, `jumper`, `total`位置的自定义分布
1. 将写完的组件打包发布之npm上

### 推荐大家在寒假阅读的书籍和文章

#### 前端方面

* Vue.js设计与实践（通俗易懂，强烈推荐）
* JavaScript高级程序设计（与下面一本看一本就够）
* JavaScript权威指南

#### 计算机相关（以下都是比较好懂的）

- 啊哈，算法（算法相关）
- 图解HTTP，图解 TCP/IP（计算机网络相关）

## 参考

- ElementPlus组件库源码 https://github.com/element-plus/element-plus
- Vitest文档 https://cn.vitest.dev/
- Vitest使用教程 https://juejin.cn/post/7190159077908381756

## 提示

- 对于一些组件无从下手的，可以先看看一些组件库的源码，进行学习
- 自定义的v-model双向绑定 https://cn.vuejs.org/guide/components/v-model.html
- 遮罩层组件和Dialog可以使用Vue内置的Teleport组件 https://cn.vuejs.org/guide/built-ins/teleport.html
- `checkbox-group`和`checkbox`之间可能不是父子关系，因此请使用Provide和Inject进行跨组件传值 https://cn.vuejs.org/api/options-composition.html