<template>
  <div class="home">
    <div class="a" @click="a">
      <div class="b" @click.stop="b"></div>
    </div>
    <a href="https://www.baidu.com" @click.prevent="c" target="_blank">测试</a>
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from '@/components/HelloWorld.vue'
export default {
  name: "Home",
  components: {},
  data() {
    return {};
  },
  methods: {
    a() {
      alert("a");
    },
    b() {
      alert("b");
    },
    c() {
      alert("c");
    }
  }
};
</script>

<style lang="scss">
.a {
  position: relative;
  width: 100px;
  height: 100px;
  background: red;
  .b {
    position: relative;
    width: 50px;
    height: 50px;
    background: blue;
  }
}
</style>
