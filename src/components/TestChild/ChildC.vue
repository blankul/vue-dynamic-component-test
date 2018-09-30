<style scoped lang='less'>
  .child-wrapper {
    width: 120px;
    height: 100px;
    padding: 24px;
    border: 1px solid #999;
    margin-top: 16px;
    background-color: rgb(220, 196, 248);
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
    <h3>ChildC</h3>
    childData: {{data}}
    prop: {{prop}}
    <button @click="handleUpdateData">更新子组件数据</button>
    <button @click="$destroy()">销毁子组件</button>
  </div>
</template>

<script>
  import printByColor from "../../utils/printByColor.js";

  export default {
    name: "ChildC",

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
      printByColor("----- childC:beforeCreate -----");
    },

    created() {
      printByColor("----- childC:created -----");
    },

    beforeMount() {
      printByColor("----- childC:beforeMount -----");
    },

    mounted() {
      printByColor("----- childC:mounted -----");
    },

    beforeUpdate() {
      printByColor("----- childC:beforeUpdate -----");
    },

    updated() {
      printByColor("----- childC:updated -----");
    },

    beforeDestroy() {
      printByColor("----- childC:beforeDestroy -----");
    },

    destroyed() {
      printByColor("----- childC:destroyed -----");
    }
  };
</script>

