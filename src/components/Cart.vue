<template>
<div>
    <ul class="list-group my-5">
        <div class="list-group-item">
            <h3 class="text-center">Your Cart</h3>
        </div>

        <li class="list-group-item" v-for="item in items" :key="item.id">
         {{item.title}} - ${{item.price}}
         <button class="btn badge badge-danger float-right" @click="$emit('remove-from-cart', item)">Remove From Cart</button>
        </li>
    </ul>

    <div class="card p-3 mt-5">
     <h3 class="text-center"> Total: ${{total}}</h3>
    </div>

    <button :disabled="items.length === 0" @click="$emit('pay-now')" class="btn btn-warning btn-sm form-control mt-3"><b>Pay Now</b></button>
</div>

</template>

<script>
export default{

props: ['items'],

computed: {

    total(){

        return this.items.reduce((acc, item) => acc + Number(item.price), 0)

    }
}
}
</script>