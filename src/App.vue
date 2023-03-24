<template>
  <div class="container">
    <h1>PRODUCTS CRUD</h1>
    <div class="row">
      <div class="col-4"><crud-form @formData="submitProduct" :productToEdit="productToEdit"></crud-form></div>
      <div class="col-8">
        <products-table
          
          :products="products"
          @deleteProduct="deleteProduct"
          @productEdit="editProduct"
        ></products-table>
      </div>
    </div>
  </div>
</template>

<script>
import CrudForm from "@/components/CrudForm.vue";
import ProductsTable from "@/components/ProductsTable.vue";
export default {
  name: "App",
  components: {
    CrudForm,
    ProductsTable,
  },
  data() {
    return {
      productToEdit:null,
      products: [
        {
          id: "1",
          name: "potato",
          description: "delicious potato",
          price: 20,
          quantity: 30,
        },
        {
          id: "2",
          name: "tomato",
          description: "delicious tomato",
          price: 15,
          quantity: 50,
        },
        {
          id: "3",
          name: "carrot",
          description: "delicious carrot",
          price: 10,
          quantity: 80,
        },
      ],
    };
  },
  methods: {
    submitProduct(data,type) {
      
      if(type==='New'){
        this.products.push(data);
      }else if(type==='Edit'){
        const indexToEdit = this.products.findIndex(p => p.id == this.productToEdit);
        this.products[indexToEdit].name=data.name;
        this.products[indexToEdit].price=data.price;
        this.products[indexToEdit].description=data.description;
        this.products[indexToEdit].quantity=data.quantity;
        this.productToEdit=null;
      }
    },
    editProduct(id){
      this.productToEdit=id;
    },
    deleteProduct(id){
      const prodId=this.products.findIndex((p)=>{p.id===id});
      this.products.splice(prodId,1);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
