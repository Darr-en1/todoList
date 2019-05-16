<!--template底下只能有一个根元素-->
<template>
  <div>
    <div>TodoList
      <input class="item" v-model="inputValue"/>
      <button @click="handleSubmit">提交</button>
    </div>

    <ul>
      <!--v-bind:content="" 等价:content=""       v-bind 来动态传递 prop -->
      <todo-item
        v-for="(item,index) in list"
        :key="index"
        :content="item"
        @delete_one="handleDelete"
      >{
      </todo-item>
    </ul>
  </div>

</template>

<script>
  import TodoItem from './components/TodoItem'

  export default {
    components: {
      'todo-item': TodoItem
    },
    // 一个组件的 data 选项必须是一个函数,因此data 需要接受一个函数而不是对象
    data: function () { //ES6语法可以简写成 data(){}
      return {
        inputValue: '',
        list: []
      }
    },
    methods: {
      handleSubmit() {
        this.list.push(this.inputValue);
        this.inputValue = ''
      },
      handleDelete(index) {
        this.list.splice(index, 1)
      }
    }
  }
</script>

<style>

</style>
