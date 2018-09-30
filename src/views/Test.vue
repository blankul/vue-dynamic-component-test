<style>
  .add-btn {
    margin: 16px 8px;
  }
</style>


<template>
  <div>
    <Button class="add-btn" @click="add">add</Button>
    <div>
      <Father 
        v-for="item in list"
        :key="item.id"
        :child="item.child"
      />
    </div>
  </div>
</template>

<script>
  import Father from "../components/Father.vue";
  import ChildA from "../components/TestChild/ChildA.vue";
  import ChildB from "../components/TestChild/ChildB.vue";
  import ChildC from "../components/TestChild/ChildC.vue";

  export default {
    name: "Test",

    components: { Father },

    data() {
      return {
        list: [],
        childArr: [ChildA, ChildB, ChildC]
      };
    },

    methods: {
      getChild() {
        const child = this.childArr[(Math.random() * this.childArr.length) | 0];
        return {
          id: +new Date(),
          child
        };
      },

      add() {
        this.list.push(this.getChild());
      }
    },

    created() {
      window.scope = this;
      this.add();
    }
  };
</script>
