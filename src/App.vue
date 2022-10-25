<template>
  <div class="container">
    <MyHeader></MyHeader>
    <MyList :list="list" @subCount="subCount" @addCount="addCount"></MyList>
    <MyFooter :list="list"></MyFooter>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader'
import MyFooter from './components/MyFooter'
import MyList from './components/MyList'

export default {
  name: 'App',
  data() {
    return {
      list: JSON.parse(localStorage.getItem('goodsList')) || [],
    }
  },
  methods: {
    subCount(id) {
      this.list.forEach((obj) => {
        if (obj.id === id && obj.count >= 1) {
          obj.count--
        }
      })
    },
    addCount(id) {
      this.list.forEach((obj) => {
        if (obj.id === id) {
          obj.count++
        }
      })
    },
  },
  watch: {
    list: {
      deep: true,
      handler() {
        localStorage.setItem('goodsList', JSON.stringify(this.list))
      },
    },
  },
  components: {
    MyHeader,
    MyFooter,
    MyList,
  },
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

li {
  list-style: none;
}

/* 总盒子 */
.container {
  margin: 0 auto;
  width: 500px;
  background-color: #ddd;
}
</style>
