<template>
    <v-card class="mx-auto" max-width="99%" outlined elevation="5">
        <v-list-item three-line>
            <v-list-item-content>
                <v-list-item-title class="headline mb-1">
                    {{ title }}
                </v-list-item-title>
                <v-list-item-subtitle>
                    {{ description }}
                </v-list-item-subtitle>
            </v-list-item-content>

            <v-list-item-avatar tile size="80">
                <v-img :src="renderImg(img)" />
            </v-list-item-avatar>
        </v-list-item>

        <v-card-actions v-if="actions">
            <v-btn
                text
                style="color:#333"
                v-for="(action, i) in actions"
                :key="i"
                @click="
                    $router.push({
                        name: action.routeName,
                        query: { tipo: action.query }
                    })
                "
                :style="`color:${action.color ? action.color : '#444'};`"
            >
                {{ action.title }}
            </v-btn>
        </v-card-actions>
    </v-card>
</template>
<script>
import { getImgUrl } from "@/services";

export default {
    props: {
        title: {
            type: String,
            required: true
        },
        description: {
            type: String,
            required: true
        },
        img: {
            type: String,
            required: true
        },
        actions: {
            type: Array
        }
    },
    methods: {
        renderImg(img) {
            return getImgUrl(img);
        }
    }
};
</script>
