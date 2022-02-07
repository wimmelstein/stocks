<template>
  <div class="title">Stock list</div>
  <div class="row">
    <!-- Individual stocks -->
    <div class="col-md-2 mt-2" v-for="stock in stocks" :key="stock.name">
      <StockItem :stock=stock />
    </div>
    <!-- End of individual stocks -->
  </div>
</template>

<script>
import StockItem from './StockItem.vue'
export default {
  name: "StockList",
  data() {
    return {
      stocks: [
        { name: "BMW", price: 61.05, previousPrice: 0, currency: "€" },
        { name: "Caterpillar", price: 146.49, previousPrice: 0, currency: "$" },
        { name: "AMD", price: 76.5, previousPrice: 0, currency: "$" },
        { name: "Gazprom", price: 4.583, previousPrice: 0, currency: "$" },
      ],
      portfolio: [],
    };
  },
  components: {
    StockItem
  },  methods: {
    updatePrices() {
      this.stocks.forEach((stock) => {
        stock.previousPrice = stock.price;
        stock.price += (Math.random() - 0.5) * 2;
        if (stock.price < 0) {
          stock.price = 0;
        }
      });
    },
  },  
  mounted() {
    setInterval(() => {
      this.updatePrices();
    }, 1000);
  },
};
</script>

<style scoped>
.up {
  color: green;
}
.down {
  color: red;
}

.title {
  font-size: 100px;
}
</style>