<template>
  <form @submit.prevent="submitForm">
    <h3 v-if="productToEdit">EDIT PRODUCT: {{ productToEdit }}</h3>
    <div class="mb-3">
      <label class="form-label">NAME</label>
      <input type="text" class="form-control" v-model="name" />
    </div>
    <div class="mb-3">
      <label class="form-label">PRICE</label>
      <input type="number" class="form-control" v-model="price" />
    </div>
    <div class="mb-3">
      <label class="form-label">DESCRIPTION</label>
      <input type="text" class="form-control" v-model="description" />
    </div>
    <div class="mb-3">
      <label class="form-label">QUANTITY</label>
      <input class="form-control" type="number" v-model="quantity" />
    </div>
    <button type="submit" class="btn btn-primary">
      {{ productToEdit ? "Edit" : "Submit" }}
    </button>
  </form>
</template>

<script>
export default {
  props: ["productToEdit"],
  data() {
    return {
      name: "",
      price: null,
      description: "",
      quantity: null,
    };
  },
  methods: {
    submitForm() {
      let type = this.productToEdit ? "Edit" : "New";
      this.$emit("formData", {
        id: new Date().getTime().toString(),
        name: this.name,
        description: this.description,
        price: this.price,
        quantity: this.quantity,
      },type);
      this.id = "";
      this.name = "";
      this.description = "";
      this.price = null;
      this.quantity = null;
    },
  },
};
</script>

<style lang="scss" scoped></style>
