<template>
    <div class="card text-center">
        <div class="text-center">
            <img v-bind:src="'/public/images/' + product.image" alt="Product image" /> 
        </div>
        <div class="card-body"> 
           <h5 class="card-title">{{product.name}}</h5> 
           <p class="card-text"><b>${{product.price}}</b></p> 
           <div class="products-bottom-content text-center">
               <p>{{product.desc}}</p>
                <button 
                class="btn mt-3"
                :class="inCartQuantity ? 'addtocartbtn' :  'addtocartbtn'"
                @click="addToCart(product.id)"
                :disabled="!inCartQuantity">
                {{inCartQuantity ? "Add to Cart" : "Out of stock"}}
                </button>
           </div>
        </div> 
   </div>
</template>

<script>
    export default{
        props: ["product"],
        computed: {
            inCartQuantity() {
                return this.product.quantity;
            }
        },
        methods: {
            addToCart(id){
                this.$store.dispatch("addToCart", id);
            }
        }
    }
</script>