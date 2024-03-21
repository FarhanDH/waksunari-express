<template>
    <MainLayout>
        <div id="IndexPage" class="mt-4 max-w-[1200px] mx-auto px-2">
            <div
                class="grid xl:grid-cols-6 lg:grid-cols-5 md:grid-cols-4 sm:grid-cols-3 grid-cols-2 gap-4"
            >
                <div v-if="products" v-for="product in products" :key="product">
                    <!-- {{ product }} -->
                    <ProductComponent :product="product" />
                </div>
            </div>
        </div>
    </MainLayout>
</template>

<script setup lang="ts">
import ProductComponent from '../components/ProductComponent.vue';
import MainLayout from '../layouts/MainLayouts.vue';

const products = [
    {
        id: 1,
        title: 'Product 1',
        description: 'Ini deskripsi',
        url: 'https://picsum.photos/id/1/300/300',
        price: 100000,
    },
    {
        id: 2,
        title: 'Product 1',
        description: 'Ini deskripsi',
        url: 'https://picsum.photos/id/1/300/300',
        price: 100000,
    },
    {
        id: 3,
        title: 'Product 1',
        description: 'Ini deskripsi',
        url: 'https://picsum.photos/id/1/300/300',
        price: 100000,
    },
    {
        id: 4,
        title: 'Product 1',
        description: 'Ini deskripsi',
        url: 'https://picsum.photos/id/1/300/300',
        price: 100000,
    },
    {
        id: 5,
        title: 'Product 1',
        description: 'Ini deskripsi',
        url: 'https://picsum.photos/id/1/300/300',
        price: 100000,
    },
    {
        id: 6,
        title: 'Product 1',
        description: 'Ini deskripsi',
        url: 'https://picsum.photos/id/1/300/300',
        price: 100000,
    },
    {
        id: 7,
        title: 'Product 1',
        description: 'Ini deskripsi',
        url: 'https://picsum.photos/id/1/300/300',
        price: 100000,
    },
    {
        id: 8,
        title: 'Product 1',
        description: 'Ini deskripsi',
        url: 'https://picsum.photos/id/1/300/300',
        price: 100000,
    },
];
</script>
