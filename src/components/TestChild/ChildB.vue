<style scoped lang='less'>
  .child-wrapper {
    width: 120px;
    height: 100px;
    padding: 24px;
    border: 1px solid #999;
    margin-top: 16px;
    background-color: #c4f8e2;
    h3 {
      text-align: center;
      margin: 0;
      font-style: italic;
      margin-bottom: 8px;
    }
  }
</style>

<template>
  <div class="child-wrapper">
    <h3>ChildB</h3>
    childData: {{data}}
    prop: {{prop}}
    <button @click="handleUpdateData">更新子组件数据</button>
    <button @click="$destroy()">销毁子组件</button>
  </div>
</template>

<script>
  import printByColor from "../../utils/printByColor.js";

  export default {
    name: "ChildB",

    data() {
      return {
        data: 10
      };
    },

    props: ["prop"],

    methods: {
      handleUpdateData() {
        this.data = (Math.random() * 100) | 0;
      }
    },

    beforeCreate() {
      window.child = this;
      printByColor("----- childB:beforeCreate -----");
    },

    created() {
      printByColor("----- childB:created -----");
    },

    beforeMount() {
      printByColor("----- childB:beforeMount -----");
    },

    mounted() {
      printByColor("----- childB:mounted -----");
    },

    beforeUpdate() {
      printByColor("----- childB:beforeUpdate -----");
    },

    updated() {
      printByColor("----- childB:updated -----");
    },

    beforeDestroy() {
      printByColor("----- childB:beforeDestroy -----");
    },

    destroyed() {
      printByColor("----- childB:destroyed -----");
    }
  };
</script>

