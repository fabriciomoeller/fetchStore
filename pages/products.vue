<template>
    <div v-if="pending">
        <p>Loading...</p>

    </div>
    <div v-else>
        <button 
            class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
            @click="refresh"
        >
            Refresh
        </button>
    </div>
    <div  class=" grid grid-cols-5 gap-4">
        <div 
            v-for="product in products"
            class="flex flex-col shadow-lg bg-white p-6 rounded-md"
        >
            <img 
                :src="product.image" 
                :alt="product.title" 
                class="w-[75px] h-auto self-center"
            >
            <h2 class="text-black mt-auto text-sm">
                {{ product.title }}
            </h2>
        </div>

    </div>
</template>

<script setup>

    const { 
        pending, 
        data: products,
        refresh
    } = useFetch(
        'https://fakestoreapi.com/products/',
        {
            lazy: true,
            transform: (products) => {
                return products.map((product) => ({
                    id: product.id,
                    title: product.title,
                    image: product.image
                }))
        
            },
        
        }
    );

</script>