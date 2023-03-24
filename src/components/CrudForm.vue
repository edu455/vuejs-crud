<template>
  <form @submit.prevent="submitForm">
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
    <button type="submit" class="btn btn-primary">Submit</button>
  </form>
</template>

<script>
export default {
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
      this.$emit("formData", {
        id: new Date().getTime().toString(),
        name: this.name,
        description: this.description,
        price: this.price,
        quantity: this.quantity,
      });
      this.id='';
      this.name='';
      this.description='';
      this.price=null;
      this.quantity=null;
    },
  },
};
</script>

<style lang="scss" scoped></style>
