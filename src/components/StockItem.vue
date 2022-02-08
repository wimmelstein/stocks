<template>
  <div class="card">
    <div class="card-header stock">{{ stock.name }}</div>
    <div class="card-body">
      <span
        :class="{
          down: stock.price < stock.previousPrice,
          up: stock.price > stock.previousPrice,
        }"
        >{{ stock.currency }} {{ stock.price.toFixed(4) }}</span
      >
    </div>
    <div class="card-footer">
      <input type="text" v-model="amount" />
      <button @click="purchaseStock" class="btn btn-primary">Buy</button>
    </div>
  </div>
</template>

<script>
export default {
    name: 'StockItem',
    props: {
        stock: Object,
    }, 
    data() { return {
        amount: 0
    }
},
methods: {
  purchaseStock(e) {
    e.preventDefault();
    const purchase = {
      'stock': this.stock,
      'amount': this.amount.valueOf
    }

    this.$emit('purchase-stock', purchase)

    this.amount = ''
  }
}

}
</script>

<style scoped>
.up {
  font-size: 50px;
  color: green;
}
.down {
  font-size: 50px;
  color: red;
}

.stock {
  text-align: center;
  padding: 40px 0px;
  font-size: 30px;
  font-weight: bold;
}
.price {
  font-size: 50px;
}
</style>