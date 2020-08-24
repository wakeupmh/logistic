<template>
    <div class="home pt-4 mt-4 px-2">
        <v-row>
            <v-col
                class="col-12 d-flex text-center justify-center flex-wrap flex-column"
            >
                <h1>
                    Bem Vindo ao Gerenciador de Logística
                </h1>
            </v-col>
        </v-row>
        <v-row>
            <v-col class="col-12 d-flex text-center justify-center">
                <v-img src="@/assets/home.svg" max-width="400" />
            </v-col>
        </v-row>
        <v-row>
            <v-col v-if="!mobile"> </v-col>
            <v-col class="text-center">
                <validation-observer ref="observer" v-slot="{ passes }">
                    <validation-provider
                        name="E-mail"
                        :rules="{ required: true, email: true }"
                        v-slot="validationContext"
                    >
                        <v-text-field
                            filled
                            label="E-mail"
                            v-model="email"
                            :state="getValidationState(validationContext)"
                            class="d-flex justify-content-center mb-3"
                            :error-messages="validationContext.errors[0]"
                            required
                        />
                    </validation-provider>
                    <validation-provider
                        name="Senha "
                        :rules="{ required: true, min: 6 }"
                        v-slot="validationContext"
                    >
                        <v-text-field
                            filled
                            label="Senha"
                            type="password"
                            v-model="password"
                            :state="getValidationState(validationContext)"
                            class="d-flex justify-content-center mb-3"
                            :error-messages="validationContext.errors[0]"
                            required
                        />
                    </validation-provider>
                    <v-btn
                        outlined
                        class="mr-2 primary mb-4"
                        dark
                        @click.stop.prevent="passes(login)"
                        width="100%"
                    >
                        Entrar
                    </v-btn>
                    <a
                        style="text-decoration:underline;cursor: pointer"
                        class="mt-4"
                        @click="$router.push({ name: 'signup' })"
                    >
                        Criar conta
                    </a>
                </validation-observer>
            </v-col>
            <v-col v-if="!mobile"> </v-col>
        </v-row>
    </div>
</template>

<script>
import { isMobile } from "@/services";
export default {
    name: "Home",
    data() {
        return {
            email: null,
            password: null,
            mobile: false
        };
    },
    methods: {
        getValidationState({ dirty, validated, valid = null }) {
            return dirty || validated ? valid : null;
        },
        login() {
            this.$router.push({ name: "dashboard" });
        }
    },
    mounted() {
        this.mobile = isMobile();
    }
};
</script>
