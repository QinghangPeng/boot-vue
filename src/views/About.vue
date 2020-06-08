/* eslint-disable vue/require-v-for-key */
<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h2>{{msg}}</h2>
    <!-- 双向数据绑定MVVM -->
    <h3>双向数据绑定MVVM</h3>
    <input type="text" v-model="msg" />
    <button @click="getMsg()">获取表单里面的数据</button>
    <button @click="setMsg()">设置表单里面的数据</button>

    <br>
    <br>
    <hr>

    <!-- 利用ref获取dom节点 -->
    <h3>利用ref获取dom节点</h3>
    <input type="text" ref="userinfo" />
    <button @click="getInputValue()">获取第二个表单里面的数据</button>
    <br>
    <br>
    <hr>

    <!-- vue事件结合双向数据绑定实现todolist -->
    <h3>vue事件结合双向数据绑定实现todolist</h3>
    <input type="text" v-model='todo' />
    <button @click="doAdd()">+增加</button>
    <br>
    <br>
    <h2>进行中</h2>
    <ul>
      <li v-for="(item,key) in list" :key="item" v-show="!item.checked">
        <input type="checkbox" v-model="item.checked">{{item.title}}  ---------  <button @click="removeData(key)">删除</button>
      </li>
    </ul>
    <br>
    <h2>已完成</h2>
    <ul>
      <li v-for="(item,key) in list" :key="item" v-show="item.checked">
        <input type="checkbox" v-model="item.checked">{{item.title}}  ---------  <button @click="removeData(key)">删除</button>
      </li>
    </ul>
  </div>
</template>

<script>
  /**
   *  横线以上:
   *  双向数据绑定 MVVM vue就是一个MVVM的框架
   *  M model
   *  V view
   *  MVVM: model改变会影响视图view,view视图改变反过来影响model
   *  双向数据绑定必须在表单里面使用
   *
   *  横线以下:
   *  利用ref获取dom节点
   */
  export default {
    data () { /** 业务逻辑里面定义的数据 */
      return {
        msg: '你好啊',
        todo: '',
        list: []
      }
    },
    methods: { /** 放方法的地方 */
      getMsg () {
        alert(this.msg)
      },
      setMsg () {
        this.msg = '我是改变后的数据'
      },
      // ref获取dom中的值
      getInputValue () {
        console.log(this.$refs.userinfo)
        alert(this.$refs.userinfo.value)
      },
      // 增加list中的值
      /**
         * 1.获取文本框输入的值
         * 2.把文本框的值push到list里面
        */
      doAdd () {
       this.list.push({
         title: this.todo,
         checked: false
       })
       this.todo = ''
      },
      // 删除list中的值
      removeData (data) {
        debugger
        this.list.splice(data, 1)
      }
    }
  }
</script>
