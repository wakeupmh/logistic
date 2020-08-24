<template>
    <div>
        <v-row>
            <v-row>
                <v-col class="col-12 d-flex text-center justify-center">
                    <v-img
                        :src="renderImg(detail.cover.img)"
                        :max-width="mobile ? '200' : '350'"
                    />
                </v-col>
                <v-col
                    class="col-12 d-flex text-center justify-center flex-column"
                >
                    <h2>{{ detail.cover.title }}</h2>
                    <h4>{{ detail.cover.subtitle }}</h4>
                </v-col>
            </v-row>
        </v-row>
        <v-row>
            <v-col v-if="!mobile"> </v-col>
            <v-col>
                <v-expansion-panels focusable>
                    <v-expansion-panel
                        v-for="(list, i) in detail.list"
                        :key="i"
                    >
                        <v-expansion-panel-header>
                            {{ list.title }}
                        </v-expansion-panel-header>
                        <v-expansion-panel-content>
                            <v-row
                                v-for="(additionalData,
                                i) in mountAdditionalData(list.additionalData)"
                                :key="i"
                            >
                                <v-col>
                                    <strong>
                                        {{ additionalData.title }}
                                    </strong>
                                </v-col>
                                <v-col> {{ additionalData.value }} </v-col>
                            </v-row>
                        </v-expansion-panel-content>
                    </v-expansion-panel>
                </v-expansion-panels>
            </v-col>
            <v-col v-if="!mobile"> </v-col>
        </v-row>
    </div>
</template>
<script>
import { isMobile, getImgUrl } from "@/services";

export default {
    data() {
        return {
            mobile: false,
            pedido: {
                cover: {
                    img: "orders.svg",
                    title: "Pedidos",
                    subtitle: "Visualize todos os seus pedidos"
                },
                list: [
                    {
                        title: "Assaí - NF 27762",
                        status: "AG CONFIRMAÇÃO DE AGENDA",
                        additionalData: {
                            dataCarga: {
                                title: "Data da carga",
                                value: "10-fev-20"
                            },
                            dataEntrada: {
                                title: "Data Entrada",
                                value: "10-fev-20"
                            },
                            horario: {
                                title: "Horário",
                                value: "09:05"
                            },
                            pallets: {
                                title: "Pallets",
                                value: 24
                            },
                            agendaGarden: {
                                title: "Agenda Garden",
                                value: "10731 - 11043"
                            },
                            transportadora: {
                                title: "Transportadora",
                                value: "Silogis"
                            },
                            produto: {
                                title: "Produto",
                                value: "Cx 34 Lts"
                            },
                            quantidade: {
                                title: "Quantidade | TT",
                                value: 720
                            },
                            palletNaCarreta: {
                                title: "PalletNaCarreta",
                                value: 24
                            },
                            unidadePallet: {
                                title: "Unidade Pallet",
                                value: 30
                            },
                            flag: {
                                title: "Flag",
                                value: "11/2/2020"
                            }
                        }
                    }
                ]
            },
            expedicao: {
                cover: {
                    img: "expedition.svg",
                    title: "Expedições",
                    subtitle: "Visualize todas suas expedições"
                },
                list: [
                    {
                        title: "Assaí - NF 27762",
                        status: "AG CONFIRMAÇÃO DE AGENDA",
                        additionalData: {
                            dataCarga: {
                                title: "Data da carga",
                                value: "10-fev-20"
                            },
                            dataEntrada: {
                                title: "Data Entrada",
                                value: "10-fev-20"
                            },
                            horario: {
                                title: "Horário",
                                value: "09:05"
                            },
                            pallets: {
                                title: "Pallets",
                                value: 24
                            },
                            agendaGarden: {
                                title: "Agenda Garden",
                                value: "10731 - 11043"
                            },
                            transportadora: {
                                title: "Transportadora",
                                value: "Silogis"
                            },
                            produto: {
                                title: "Produto",
                                value: "Cx 34 Lts"
                            },
                            quantidade: {
                                title: "Quantidade | TT",
                                value: 720
                            },
                            palletNaCarreta: {
                                title: "PalletNaCarreta",
                                value: 24
                            },
                            unidadePallet: {
                                title: "Unidade Pallet",
                                value: 30
                            },
                            flag: {
                                title: "Flag",
                                value: "11/2/2020"
                            }
                        }
                    }
                ]
            },
            analise: {
                cover: {
                    img: "analysis.svg",
                    title: "Análises",
                    subtitle: "Visualize suas análises"
                },
                list: [
                    {
                        title: "Assaí - NF 27762",
                        status: "AG CONFIRMAÇÃO DE AGENDA",
                        additionalData: {
                            dataCarga: {
                                title: "Data da carga",
                                value: "10-fev-20"
                            },
                            dataEntrada: {
                                title: "Data Entrada",
                                value: "10-fev-20"
                            },
                            horario: {
                                title: "Horário",
                                value: "09:05"
                            },
                            pallets: {
                                title: "Pallets",
                                value: 24
                            },
                            agendaGarden: {
                                title: "Agenda Garden",
                                value: "10731 - 11043"
                            },
                            transportadora: {
                                title: "Transportadora",
                                value: "Silogis"
                            },
                            produto: {
                                title: "Produto",
                                value: "Cx 34 Lts"
                            },
                            quantidade: {
                                title: "Quantidade | TT",
                                value: 720
                            },
                            palletNaCarreta: {
                                title: "PalletNaCarreta",
                                value: 24
                            },
                            unidadePallet: {
                                title: "Unidade Pallet",
                                value: 30
                            },
                            flag: {
                                title: "Flag",
                                value: "11/2/2020"
                            }
                        }
                    }
                ]
            },
            detail: null
        };
    },
    mounted() {
        this.mobile = isMobile();
        this.detail = this[this.$route.query.tipo];
    },
    methods: {
        renderImg(img) {
            return getImgUrl(img);
        },
        mountAdditionalData(obj) {
            return Object.keys(obj).map(item => obj[item]);
        }
    }
};
</script>
