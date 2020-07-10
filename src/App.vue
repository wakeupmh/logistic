<template>
    <v-app>
        <v-content>
            <transition name="slide-fade" mode="out-in">
                <router-view class="mb-5 pb-5" />
            </transition>
        </v-content>
    </v-app>
</template>

<script>
import "./style/index.css";

export default {};
</script>
