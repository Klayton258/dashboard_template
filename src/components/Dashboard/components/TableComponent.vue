<template>

<div class="main-table">
    <table class="table">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">Name</th>
      <th scope="col">Quantity</th>
      <th scope="col">Price</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="product in products" :key="product.id">
      <th scope="row">{{product.id}}</th>
      <td>{{product.product_name}}</td>
      <td>{{product.quantity}}</td>
      <td>{{product.price}}</td>
    </tr>
  </tbody>
</table>
</div>

</template>

<script>
name: "TableComponent"

export default {

props:{
    products: Array
}

}
</script>

<style lang="scss" scoped>

</style>