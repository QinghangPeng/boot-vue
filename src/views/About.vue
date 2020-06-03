<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h2>{{msg}}</h2>
    <input type="text"
           v-model="msg" />
    <button @click="getMsg()">获取表单里面的数据</button>
    <button @click="setMsg()">设置表单里面的数据</button>

    <br>
    <br>
    <hr>
    <br>
    <br>

    <input type="text"
           ref="userinfo" />
    <button @click="getInputValue()">获取第二个表单里面的数据</button>
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
      msg: '你好啊'
    }
  },
  methods: { /** 放方法的地方 */
    getMsg () {
      alert(this.msg)
    },
    setMsg () {
      this.msg = '我是改变后的数据'
    },
    getInputValue () {
      console.log(this.$refs.userinfo)
      alert(this.$refs.userinfo.value)
    }
  }
}
</script>
