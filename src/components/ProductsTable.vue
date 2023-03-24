<template>
  <table class="table">
    <thead>
      <tr>
        <th scope="col">ID</th>
        <th scope="col">NAME</th>
        <th scope="col">DESCRIPTION</th>
        <th scope="col">PRICE</th>
        <th scope="col">QUANTITY</th>
        <th scope="col">ACTIONS</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="prod in products" :key="prod">
        <td>{{ prod.id }}</td>
        <td>{{ prod.name }}</td>
        <td>{{ prod.description }}</td>
        <td>{{ prod.price }}</td>
        <td>{{ prod.quantity }}</td>
        <td>
          <button class="btn btn-danger" @click="deleteProduct(prod.id)">
            Delete
          </button>
          <button class="btn btn-primary" @click="editProduct(prod.id)">
            Edit
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  props: ["products"],
  methods: {
    deleteProduct(id) {
      this.$emit("deleteProduct", id);
    },
    editProduct(id) {
      this.$emit("productEdit", id);
    },
  },
};
</script>

<style scoped></style>
