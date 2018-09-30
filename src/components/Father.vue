<style scoped lang='less'>
  .wrapper {
    width: 180px;
    height: 240px;
    padding: 24px;
    border: 1px solid #999;
    background-color: #eee;
    float: left;
    margin: 0 8px 8px 0;
    p {
      margin: 0;
    }
  }
</style>

<template>
  <div class="wrapper">
    fatherData: {{data}}
    <p><button @click="handleUpdateData">更新父组件数据</button></p>
    <p><button @click="$destroy()">销毁父组件</button></p>
    <component :is="child" :prop="data" />
  </div>
</template>

<script>
  import printByColor from "../utils/printByColor.js";
  const print = (text) => printByColor(text, 'red')

  export default {
    name: "Father",

    data() {
      return {
        data: 20,
      };
    },

    props: ['child'],

    methods: {
      handleUpdateData() {
        this.data = Math.random() * 100 | 0
      }
    },

    beforeCreate() {
      window.scope = this;
      print("----- father:beforeCreate -----");
    },

    created() {
      print("----- father:created -----");
    },

    beforeMount() {
      print("----- father:beforeMount -----");
    },

    mounted() {
      print("----- father:mounted -----");
    },

    beforeUpdate() {
      print("----- father:beforeUpdate -----");
    },

    updated() {
      print("----- father:updated -----");
    },

    beforeDestroy() {
      print("----- father:beforeDestroy -----");
    },

    destroyed() {
      print("----- father:destroyed -----");
    }
  };
</script>
