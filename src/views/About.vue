<template>
  <div class="statisContent" v-loading="loading">
    <div class="chartNum">
      <h3 class="orderTitle">订单总量</h3>
      <div class="box-item">
        <li
          :class="{ 'number-item': !isNaN(item), 'mark-item': isNaN(item) }"
          v-for="(item, index) in orderNum"
          :key="index"
        >
          <span v-if="!isNaN(item)">
            <i ref="numberItem">0123456789</i>
          </span>
          <span class="comma" v-else>{{ item }}</span>
        </li>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loading: false,
      orderNum: ["0", "0", "0", "0", "0", "0", "0", "0"],
      count: 0,
      tag: 456,
    };
  },
  methods: {
    // 设置文字滚动
    setNumberTransform() {
      const numberItems = this.$refs.numberItem; // 拿到数字的ref，计算元素数量
      const numberArr = this.orderNum.filter((item) => !isNaN(item));
      // 结合CSS 对数字字符进行滚动,显示订单数量
      for (let index = 0; index < numberItems.length; index++) {
        const elem = numberItems[index];
        elem.style.transform = `translate(-50%, -${numberArr[index] * 10}%)`;
      }
    },
    // 处理总订单数字
    toOrderNum(num) {
      num = num.toString();
      // 把订单数变成字符串
      if (num.length < 8) {
        num = "0" + num; // 如未满八位数，添加"0"补位
        this.toOrderNum(num); // 递归添加"0"补位
      } else if (num.length === 8) {
        // 订单数中加入逗号
        //num = num.slice(0, 2) + "," + num.slice(2, 5) + "," + num.slice(5, 8);
        this.orderNum = num.split(""); // 将其便变成数据，渲染至滚动数组
      } else {
        // 订单总量数字超过八位显示异常
        this.$message.warning("订单总量数字过大，显示异常，请联系客服");
      }
    },
    increaseNumber(add) {
      let self = this;
      self.count = self.count + add;
      this.toOrderNum(self.count);
      this.$nextTick(() => {
        self.setNumberTransform(self.count);
      });
    },
    getRandomNumber(min, max) {
      return Math.floor(Math.random() * (max - min + 1) + min);
    },
  },
  mounted() {
    this.timer = setInterval(() => {
      this.increaseNumber(23);
    }, 3000);
  },
};
</script>

<style lang='scss'>
.statisContent {
  padding-top: 20px;
  background-color: #000;
  .number-item {
    width: 41px;
    height: 75px;
    background: #ccc;
    list-style: none;
    margin-right: 5px;
    background: rgba(250, 250, 250, 1);
    border-radius: 4px;
    border: 1px solid rgba(221, 221, 221, 1);
    display: inline-block;
    font-size: 60px;
    & > span {
      position: relative;
      display: inline-block;
      margin-right: 10px;
      width: 100%;
      height: 100%;
      writing-mode: vertical-rl;
      text-orientation: upright;
      overflow: hidden;
      & > i {
        font-style: normal;
        position: absolute;
        top: 7px;
        left: 50%;
        transform: translate(-50%, 0);
        transition: transform 1s ease-in-out;
        letter-spacing: 10px;
      }
    }
  }
  .number-item:last-child {
    margin-right: 0;
  }
  .comma {
    display: inline-block;
    color: #fff;
    font-size: 30px;
  }
  .mark-item {
    display: inline-block;
  }
}
</style>