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

            <v-list-item-avatar
                tile
                size="80"
            >
                <v-img :src="getImgUrl(img)" />
            </v-list-item-avatar>
        </v-list-item>

        <v-card-actions v-if="actions">
            <v-btn
                text
                style="color:#333"
                v-for="(action, i) in actions"
                :key="i"
                @click="$router.push({ name: action.routeName })"
            >
                {{ action.title }}
            </v-btn>
        </v-card-actions>
    </v-card>
</template>
<script>
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
        getImgUrl(fileName) {
            return require(`../assets/${fileName}`);
        }
    }
}
</script>
