<template>
    <div class="px-5 pt-5">
        <v-row>
            <v-col class="col-12 d-flex text-center justify-center">
                <v-img
                    src="@/assets/dashboard.svg"
                    :max-width="mobile ? '200' : '350'"
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
import { isMobile } from "@/services";

export default {
    data() {
        return {
            mobile: false,
            callToActions: [
                {
                    title: "Pedidos",
                    description:
                        "Visualize seus pedidos, e os detalhes de cada um.",
                    img: "icons/order.svg",
                    actions: [
                        {
                            title: "Visualizar todos",
                            routeName: "list",
                            query: "pedido"
                        },
                        {
                            title: "Adicionar novo",
                            routeName: "insert",
                            query: "pedido",
                            color: "#673ab7"
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
                            routeName: "list",
                            query: "expedicao"
                        },
                        {
                            title: "Adicionar nova",
                            routeName: "insert",
                            query: "expedicao",
                            color: "#673ab7"
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
                            routeName: "list",
                            query: "analise"
                        },
                        {
                            title: "Adicionar nova",
                            routeName: "insert",
                            query: "analise",
                            color: "#673ab7"
                        }
                    ]
                }
            ]
        };
    },
    components: {
        CallToActionCard
    },
    mounted() {
        this.mobile = isMobile();
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
