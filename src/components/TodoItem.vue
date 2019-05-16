<template>
  <li class="item" @click="handleDelete">{{content}}</li>
</template>

<script>
export default {
  props: ['content', 'key'],
  methods: {
    handleDelete() {
      this.$emit('delete_one', this.key)  //和父组件通信，定义一个事件并带上参数
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .item{
    color: red;
  }
</style>
