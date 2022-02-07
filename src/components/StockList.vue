<template>
  <div>
    <table class="table">
      <thead class="table-striped" >
        <tr>
          <th>Stock name</th>
          <th>Price</th>
          <th>Previous Price</th>
        </tr>
      </thead>
      <tbody>
      <tr v-for="stock in stocks" :key="stock.id">
        <td>{{ stock.name }}</td>
        <td
          :class="{
            down: stock.price < stock.previousPrice,
            up: stock.price > stock.previousPrice,
            same: stock.price == stock.previousPrice
          }"
        >
          {{ stock.currency }} {{ stock.price }}
        </td>
        <td>{{ stock.previousPrice }}</td>
      </tr>
      </tbody>
    </table>
    <button @click="updatePrice" class="btn btn-primary">Update</button>
  </div>
</template>
        
    
<script>
export default {
  name: "StockList",
  data() {
    return {
      stocks: [
        {
          id: 1,
          name: "BMW",
          price: 61.05,
          previousPrice: 0,
          currency: "EUR",
        },
        {
          id: 2,
          name: "Caterpillar",
          price: 146.49,
          previousPrice: 0,
          currency: "USD",
        },
        {
          id: 3,
          name: "AMD",
          price: 76.5,
          previousPrice: 0,
          currency: "USD",
        },
        {
          id: 4,
          name: "Gazprom",
          price: 4.583,
          previousPrice: 0,
          currency: "USD",
        },
      ],
    };
  },
  methods: {
    updatePrice() {
      this.stocks.forEach((stock) => {
        stock.previousPrice = stock.price;
        stock.price += (Math.random() - 0.5) * 2;
        if (stock.price < 0) stock.price = 0;
      });
    },
  },
  mounted() {
    setInterval(() => this.updatePrice(), 1000);
  },
};
</script>

<style>
.up {
  color: green;
}

.down {
  color: red;
}
.same {
  color: black;
}
</style>