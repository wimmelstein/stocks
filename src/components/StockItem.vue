<template>
  <div class="card">
        <div class="card-body">
          <div class="card-header stock" >{{ stock.name }}</div>
          <span
            :class="{
              down: stock.price < stock.previousPrice,
              up: stock.price > stock.previousPrice,
            }"
            >{{ stock.currency }} {{ stock.price.toFixed(4) }}</span
          >
        </div>
      </div>
</template>

<script>
export default {
    name: 'StockItem',
    props: {
        stock: Object
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