<template>
    <v-app>
        <Navbar />
        <v-main>
            <transition name="slide-fade" mode="out-in">
                <router-view class="mb-5 pb-5" />
            </transition>
        </v-main>
    </v-app>
</template>

<script>
import "./style/index.css";
import Navbar from "@/components/Navbar.vue";

export default {
    components: {
        Navbar
    }
};
</script>
