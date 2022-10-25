<template>
  <div class="my_bottom">
    <div class="ck">
      <input type="checkbox" v-model="isAll" />
      <span>全选</span>
    </div>

    <div class="total_box">
      <span>合计：</span>
      <span class="total_price"
        >￥ <span>{{ totalPrice }}</span></span
      >
    </div>
    <div class="bottom_right">
      <span class="bottom_right_total">结算({{ totalCount }})</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MyFooter',
  computed: {
    isAll: {
      get() {
        if (this.list.length === 0) {
          return false
        }

        return this.list.every((obj) => obj.done === true)
      },
      set(value) {
        this.list.forEach((obj) => {
          obj.done = value
        })
      },
    },
    total() {
      return this.list.length
    },
    totalCount() {
      let count = 0
      this.list.forEach((obj) => {
        if (obj.done) {
          count += obj.count
        }
      })
      return count
    },
    totalPrice() {
      let sum = 0
      this.list.forEach((obj) => {
        if (obj.done) {
          sum += obj.price * obj.count
        }
      })
      return sum
    },
  },
  props: ['list'],
}
</script>

<style>
.my_bottom {
  position: relative;
  margin-top: 5px;
  width: 100%;
  height: 40px;
  background-color: #fdfefe;
  float: left;
  border: 0.5px solid #d5d3d3;
  line-height: 40px;
  color: #24272a;
}

.my_bottom div {
  float: left;
}

.ck {
  width: 110px;
  height: 16px;
  padding: 0 10px;
  float: left;
}

.ck span {
  margin-left: 10px;
  font-size: 16px;
  line-height: 16px;
}

/* 合计盒子 */
.total_box {
  float: left;
  margin-left: 50px;
  width: 200px;
}

.total_price {
  color: #ff0000;
  font-weight: 800;
}

.bottom_right {
  margin-top: 5px;
  position: absolute;
  right: 15px;
  height: 30px;
  width: 90px;
  background-color: #197afe;
  border: 1px solid #197afe;
  border-radius: 15px;
  color: #fdfefe;
  text-align: center;
  line-height: 30px;
  cursor: pointer;
}

.bottom_right_total {
  padding: 0 10px;
}
</style>
