<template>
    <div
        id="MenuOverlay"
        class="fixed z-50 bottom-0 h-full w-full bg-white px-3"
    >
        <div class="flex items-center justify-between py-5">
            <nuxt-link to="/" @click="userStore.isMenuOverlay = false">
                <img width="170" src="/food-extreme.png" />
            </nuxt-link>

            <button
                @click="userStore.isMenuOverlay = false"
                class="rounded-full p-1 hover:bg-gray-200"
            >
                <Icon name="mdi:close" size="30" />
            </button>
        </div>

        <div class="flex items-center justify-between pt-5">
            <ul class="w-full">
                <li
                    @click="goTo('orders')"
                    class="relative flex items-center justify-between py-2.5 border-b px-3 hover:bg-gray-100 cursor-pointer"
                >
                    <div class="flex items-center text-[20px] font-semibold">
                        <Icon name="ph:pen-light" size="33" />
                        <span class="pl-4">Pesanan Saya</span>
                    </div>
                </li>

                <li
                    @click="goTo('shoppingcart')"
                    class="relative flex items-center justify-between py-2.5 border-b px-3 hover:bg-gray-100 cursor-pointer"
                >
                    <div class="flex items-center text-[20px] font-semibold">
                        <Icon name="ph:shopping-cart-simple-light" size="33" />
                        <span class="pl-4">Keranjang</span>
                    </div>
                    <div
                        class="flex items-center justify-center bg-[#FF4646] h-[35px] min-w-[35px] text-lg text-white rounded-full"
                    >
                        {{ userStore.cart.length }}
                    </div>
                </li>

                <li
                    v-if="user"
                    @click="signOut()"
                    class="relative flex items-center justify-between py-2.5 border-b px-3 hover:bg-gray-100 cursor-pointer"
                >
                    <div class="flex items-center text-[20px] font-semibold">
                        <Icon name="ph:sign-out-light" size="33" />
                        <span class="pl-4">Sign out</span>
                    </div>
                </li>

                <li
                    v-else
                    @click="signIn()"
                    class="relative flex items-center justify-between py-2.5 border-b px-3 hover:bg-gray-100 cursor-pointer"
                >
                    <div class="flex items-center text-[20px] font-semibold">
                        <Icon name="ph:sign-in-light" size="33" />
                        <span class="pl-4">Sign in / Register</span>
                    </div>
                </li>
            </ul>
        </div>
    </div>
</template>

<script setup>
import { useUserStore } from '../stores/user';
const userStore = useUserStore();

const client = useSupabaseClient();
const user = useSupabaseUser();

/**
 * Function to navigate to a specified URL after hiding the menu overlay.
 *
 * @param {string} url - The URL to navigate to
 * @return {string} The URL that was navigated to
 */
const goTo = (url) => {
    userStore.isMenuOverlay = false;
    return navigateTo(`/${url}`);
};

/**
 * Signs out the user and navigates to the home page.
 *
 * @return {Promise<void>} A promise that resolves when the user is signed out and navigated to the home page.
 */
const signOut = () => {
    client.auth.signOut();
    userStore.isMenuOverlay = false;
    return navigateTo('/');
};

/**
 * Sign in the user and navigate to the authentication page.
 *
 * @return {Promise} A promise that resolves when the navigation is complete.
 */
const signIn = () => {
    userStore.isMenuOverlay = false;
    return navigateTo('/auth');
};
</script>
