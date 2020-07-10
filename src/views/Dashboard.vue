<template>
    <div class="px-5 pt-5">
        <v-row>
            <v-col class="col-12 d-flex text-center justify-center">
                <v-img
                    src="@/assets/dashboard.svg"
                    :max-width="isMobile() ? '200' : '350'"
                />
            </v-col>
            <v-col class="col-12 d-flex text-center justify-center flex-column">
                <h2>Dashboard</h2>
                <h4>Acompanhe seus pedidos, análises e expedições</h4>
            </v-col>
        </v-row>
        <v-row>
            <v-col v-for="(callToAction, i) in callToActions" :key="i">
                <CallToActionCard
                    :title="callToAction.title"
                    :description="callToAction.description"
                    :img="callToAction.img"
                    :actions="callToAction.actions"
                />
            </v-col>
        </v-row>
    </div>
</template>
<script>
import CallToActionCard from "@/components/CallToActionCard.vue";

export default {
    data() {
        return {
            callToActions: [
                {
                    title: "Pedidos",
                    description:
                        "Visualize seus pedidos, e os detalhes de cada um.",
                    img: "icons/order.svg",
                    actions: [
                        {
                            title: "Visualizar todos",
                            routeName: ""
                        },
                        {
                            title: "Adicionar novo",
                            routeName: "",
                            color: "#"
                        }
                    ]
                },
                {
                    title: "Expedições",
                    description:
                        "Visualize suas expedições, gerencie o andamento.",
                    img: "icons/mover-truck.svg",
                    actions: [
                        {
                            title: "Visualizar todas",
                            routeName: ""
                        },
                        {
                            title: "Adicionar nova",
                            routeName: "",
                            color: "#"
                        }
                    ]
                },
                {
                    title: "Análises",
                    description:
                        "Visualize suas Análises, entenda como esta seu processo.",
                    img: "icons/buy.svg",
                    actions: [
                        {
                            title: "Visualizar todas",
                            routeName: ""
                        },
                        {
                            title: "Adicionar nova",
                            routeName: "",
                            color: "#"
                        }
                    ]
                }
            ]
        };
    },
    components: {
        CallToActionCard
    },
    methods: {
        isMobile() {
            if (
                /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(
                    navigator.userAgent
                )
            ) {
                return true;
            }
            return false;
        }
    }
};
</script>
<style>
.logout {
    text-decoration: underline;
    cursor: pointer;
    color: #444 !important;
}
.logout:hover {
    color: rgb(204, 44, 79) !important;
}
</style>
