<template>
    <div v-if="pending">
        <p>Loading...</p>

    </div>
    <div v-else class=" grid grid-cols-5 gap-4">
        <div 
           
            class="flex flex-col shadow-lg bg-white p-6 rounded-md"
        >
    
            <img 
                :src="products.image" 
                :alt="products.title" 
                class="w-[75px] h-auto self-center"
            >
            <h2 class="text-black mt-auto text-sm">
                {{ products.title }}
            </h2>
        </div>

    </div>
</template>

<script setup>

    /*const { pending, data: products } = useFetch(
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
    );*/

    const { pending, data: products } = useFetch(
        'https://fakestoreapi.com/products/1',
        {
            lazy: true,
            pick: ['id', 'title', 'image'],
        
        }
    );

</script>