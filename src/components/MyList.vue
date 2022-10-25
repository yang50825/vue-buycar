<template>
  <div class="center_box">
    <div class="context_box" v-for="goods in list" :key="goods.id">
      <div class="ck">
        <input type="checkbox" v-model="goods.done" />
      </div>
      <div class="img">
        <img :src="goods.picture" />
      </div>
      <div class="right">
        <p class="title">
          <span class="right_title">
            {{ goods.title }}
          </span>
        </p>
        <p class="countBtn">
          <span class="right_title">
            <font color="red">￥{{ goods.price }}</font>
          </span>
          <button class="btn" @click="subCount(goods.id)">-</button>
          <span class="price">{{ goods.count }}</span>
          <button class="btn" @click="addCount(goods.id)">+</button>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MyList',
  methods: {
    subCount(id) {
      this.$emit('subCount', id)
    },
    addCount(id) {
      this.$emit('addCount', id)
    },
  },
  props: ['list'],
}
</script>

<style scoped>
.center_box {
  width: 500px;
  background-color: blanchedalmond;
}
.context_box {
  width: 500px;
  height: 170px;
  background-color: #fdfefe;
  padding: 10px 0;
  border: 1px solid #d5d3d3;
}
.ck {
  margin-right: 10px;
  width: 20px;
  height: 150px;
  float: left;
  line-height: 150px;
  padding: 0 10px;
}
.img {
  float: left;
  width: 150px;
  height: 150px;
}

.img img {
  width: 100%;
  height: 100%;
  border-radius: 12px;
}
.right {
  float: left;
  width: 300px;
  height: 150px;
  margin-left: 10px;
  /* background-color: yellow; */
}
.btn {
  margin: 0 10px;
  width: 40px;
  height: 30px;
  background-color: rgb(244, 245, 247);
  border-radius: 5px;
  border: 0;
  cursor: pointer;
}
.right_title {
  margin-right: 60px;
  color: #24272a;
  font-size: 20px;
  font-weight: 600;
}

.countBtn {
  float: right;
}
.title {
  margin-bottom: 20px;
}

.price {
  display: inline-block;
  width: 50px;
  height: 40px;
  border: 2px solid rgb(236, 238, 241);
  border-radius: 5px;
  text-align: center;
  line-height: 40px;
}
</style>
