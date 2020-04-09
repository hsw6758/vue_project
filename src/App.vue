<template>
  <div>
    <h1>必修以下课程</h1>
    <ul>
      <li v-for="(item,index) in goods" :key="index">
        {{index}} -- {{item.cource}} -- {{item.price}}
        <button @click="addgood(index)">添加到购物车</button>
      </li>
    </ul>
    <table border="1">
      <tr>
        <td>课程名称</td>
        <td>课程单价</td>
        <td>课程总价</td>
        <td>购买个数</td>
      </tr>
      <tr v-for="(item,index) in cart" :key="index">
        <td>{{item.cource}}</td>
        <td>{{item.price}}</td>
        <td>{{item.price * item.count}}</td>
        <td>{{item.count}}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      goods: [
        { cource: "高级JS", price: 18 },
        { cource: "vue全家桶", price: 18 },
        { cource: "react全家桶", price: 18 },
        { cource: "nodeJS", price: 18 }
      ],
      cart: []
    };
  },
  components: {},
  methods: {
    addgood(i) {
      var arr = [1000, 2, 2, 3, 4, 5, 5, 6, 7, 7, 899, 899, 0, 8, 6, 3, 4, 56, 2];
      var arr2 = arr.filter((x, index) => arr.indexOf(x) === index);
      console.log(arr2);

      let item = this.goods[i];
      let good = this.cart.find(v => v.cource == item.cource);
      console.log(good);
      if (good) {
        good.count += 1;
      } else {
        this.cart.push({ ...item, count: 1 });
      }
      console.log(this.cart);
    }
  }
};
</script>

<style>
</style>
