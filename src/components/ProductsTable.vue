<template>
    <table class="table">
        <thead>
          <tr>
            <th scope="col">ID</th>
            <th scope="col">NAME</th>
            <th scope="col">DESCRIPTION</th>
            <th scope="col">PRICE</th>
            <th scope="col">QUANTITY</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="prod in products" :key="prod">
            <td>{{ prod.id }}</td>
            <td>{{prod.name}}</td>
            <td>{{prod.description}}</td>
            <td>{{prod.price}}</td>
            <td>{{prod.quantity}}</td>
          </tr>
        </tbody>
      </table>
</template>

<script>
    export default {
        props:['products']
    }
</script>

<style  scoped>

</style>