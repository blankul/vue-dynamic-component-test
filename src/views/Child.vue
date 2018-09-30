<style scoped lang='less'>
  .child-wrapper {
    width: 120px;
    height: 100px;
    padding: 24px;
    border: 1px solid #999;
    margin: 8px auto;
  }
</style>

<template>
  <div class="child-wrapper">
    childData: {{data}}
    prop: {{prop}}
    <button @click="handleUpdateData">更新子组件数据</button>
    <button @click="$destroy()">销毁子组件</button>
  </div>
</template>

<script>
  import printByColor from "../utils/printByColor.js";

  export default {
    name: "Child",

    data() {
      return {
        data: 10
      };
    },

    props: ['prop'],
    
    methods: {
      handleUpdateData() {
        this.data = Math.random() * 100 | 0
      }
    },

    beforeCreate() {
      window.child = this;
      printByColor("----- child:beforeCreate -----");
    },

    created() {
      printByColor("----- child:created -----");
    },

    beforeMount() {
      printByColor("----- child:beforeMount -----");
    },

    mounted() {
      printByColor("----- child:mounted -----");
    },

    beforeUpdate() {
      printByColor("----- child:beforeUpdate -----");
    },

    updated() {
      printByColor("----- child:updated -----");
    },

    beforeDestroy() {
      printByColor("----- child:beforeDestroy -----");
    },

    destroyed() {
      printByColor("----- child:destroyed -----");
    }
  };
</script>

