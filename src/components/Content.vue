<template>
  <div>
    <h1>内容页</h1>
    <h2>{{ title }}</h2>
    <button @click="randomTitle()">改变Title</button>
    <button @click="destoryVm()">摧毁实例</button>
  </div>
</template>

<script>
export default {
  name: "Content",
  data() {
    return {
      title: "Hello World",
    };
  },
  methods: {
    randomTitle() {
      this.title =
        "Hello" +
        ["China", "World", "Universe"][Math.floor(Math.random() * 2.999)];
    },

    destoryVm() {
      this.$destroy();
    },
  },
  beforeCreate() {
    console.log("before create");
  },
  created() {
    console.log("created");
  },
  beforeMount() {
    console.log("before mount");
  },
  mounted() {
    console.log("mounted");
  },
  beforeUpdate() {
    console.log("before update");
  },
  updated() {
    console.log("updated");
  },
  beforeDestroy() {
    console.log("before destory");
  },
  destroyed() {
    console.log("destoryed");
  },

  /**
   * 侦测变化的两种方式：
   * Object.defineProperty
   * ES6的Proxy
   */
  defineReactive(data, key, val) {
    Object.defineProperty(data, key, {
      enumerable:true,
      configurable:true,
      get:function() {
        return val
      },

      set: function(newVal) {
        if(val === newVal) {
          return
        }
        val = newVal
      }

    })
  },
};
</script>

<!--作用域-->
<style scoped>
</style>
