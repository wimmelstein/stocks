<template>
  <div class="card">
    <div class="card-header">{{ stock.name }}</div>
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
      <!-- <input class="form-control-md" type="text" v-model="amount" id="amount" />
        <button class="btn btn-outline-dark" @click="purchaseStock">Buy</button> -->
      <form class="d-flex justify-content-center"  >
        <div class="col-auto">
          <input
            type="text"
            class="form-control"
            id="amount"
            placeholder="amount"
            v-model="amount"
          />
        </div>
        <div class="col-auto">
          <button type="submit" class="btn btn-warning mb-3" @click="purchaseStock">
            Purchase
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "StockItem",
  props: {
    stock: Object,
  },
  data() {
    return {
      amount: "",
    };
  },
  methods: {
    purchaseStock(e) {
      e.preventDefault();
      const item = {
        stock: this.stock,
        amount: this.amount.valueOf,
      };

      this.$emit("purchase-stock", item);

      this.amount = "";
    },
  },
};
</script>

<style>
.up {
  color: green;
  font-size: 50px;
}
.down {
  color: red;
  font-size: 50px;
}
</style>