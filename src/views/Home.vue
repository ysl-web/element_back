<template>
  <div class="home">
    <div class="bor bor-hover">click me</div>
    <div class="bor gradient">click me</div>
    <div class="bor outline">click me</div>
    <div>测试</div>
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
  methods: {},
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

:root {
  --borderColor: #03a9f3;
}

.bor {
  width: 240px;
  padding: 24px 0;
  box-sizing: border-box;
  text-align: center;
}

.bor + .bor {
  margin-top: 30px;
}

.bor-hover {
  position: relative;
  border: 1px solid #03a9f3;

  &::before,
  &::after {
    content: "";
    position: absolute;
    width: 20px;
    height: 20px;
    transition: 0.3s ease-in-out;
  }

  &::before {
    top: -5px;
    left: -5px;
    border-top: 1px solid var(--borderColor);
    border-left: 1px solid var(--borderColor);
  }

  &::after {
    right: -5px;
    bottom: -5px;
    border-bottom: 1px solid var(--borderColor);
    border-right: 1px solid var(--borderColor);
  }

  &:hover::before,
  &:hover::after {
    width: calc(100% + 9px);
    height: calc(100% + 9px);
  }
}

.gradient {
  background: linear-gradient(90deg, #333 50%, transparent 0) repeat-x,
    linear-gradient(90deg, #333 50%, transparent 0) repeat-x,
    linear-gradient(0deg, #333 50%, transparent 0) repeat-y,
    linear-gradient(0deg, #333 50%, transparent 0) repeat-y;
  background-size: 4px 1px, 4px 1px, 1px 4px, 1px 4px;
  background-position: 0 0, 0 100%, 0 0, 100% 0;
  cursor: pointer;

  &:hover {
    animation: linearGradientMove 0.3s infinite linear;
  }
}

.outline {
  // border: 1px solid #333;
  outline: 1px solid #333;
  outline-offset: -1px;
  transition: all 0.3s linear;
  cursor: pointer;

  &:hover {
    // border: 1px solid transparent;
    outline: 1px solid transparent;
    background: linear-gradient(90deg, #333 50%, transparent 0) repeat-x,
      linear-gradient(90deg, #333 50%, transparent 0) repeat-x,
      linear-gradient(0deg, #333 50%, transparent 0) repeat-y,
      linear-gradient(0deg, #333 50%, transparent 0) repeat-y;
    background-size: 4px 1px, 4px 1px, 1px 4px, 1px 4px;
    background-position: 0 0, 0 100%, 0 0, 100% 0;
    animation: linearGradientMove 0.3s infinite linear;
  }
}

@keyframes linearGradientMove {
  100% {
    background-position: 4px 0, -4px 100%, 0 -4px, 100% 4px;
  }
}
</style>
