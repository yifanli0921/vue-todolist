# vue-todolist

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run all tests
npm test
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
#Todolist tasking
拆卡原则（INVEST）
1、Independent：避免故事之间的依赖
2、Negotiable：只提供适量信息，对细节可以探讨
3、Valuable:以价值为导向
4、Estimatable：可以估算出对应的点数，对开发进度进行估算
5、Small:便于估算也便于交付
6、Testable： 必须有明确的完成标准，以判断是否满足用户期望

基本功能：
1、添加功能：在输入框中输入内容后按enter键或点击输入框之外的区域，将内容添加到下面的列表中，增加校验功能，如果输入为空则不添加
2、动态计算未完成任务总数,并显示在页面上
3、删除功能：点击item对应的删除按钮，可以将对应的item删除
4、修改功能：通过双击已经添加的item list，进行重新编辑，按enter键或者输入框外的区域即可完成编辑进行保存
5、如果重新编辑后为空，则仍保留原来的item内容
6、查找功能：添加三种状态管理，分别为总数量，已经完成的数量以及未完成的数量并动态计算item的数量，并将具体的item显示在列表上
7、添加clear delete按钮，可以将状态为completed状态的items一键删除；同时增加check all按钮，可以将所有item状态切换为completed状态
