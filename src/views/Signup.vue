<template>
    <div class="home pt-4 mt-4 px-2">
        <v-row>
            <v-col
                class="col-12 d-flex text-center justify-center flex-wrap flex-column"
            >
                <h1>
                    Cadastre sua empresa
                </h1>
            </v-col>
        </v-row>
        <v-row>
            <v-col class="col-12 d-flex text-center justify-center">
                <v-img src="@/assets/new.svg" max-width="400" />
            </v-col>
        </v-row>
        <v-row>
            <v-col v-if="!isMobile()"> </v-col>
            <v-col class="text-center">
                <validation-observer ref="observer" v-slot="{ passes }">
                    <validation-provider
                        name="E-mail"
                        :rules="{ required: true }"
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
                        :rules="{ required: true }"
                        v-slot="validationContext"
                    >
                        <v-text-field
                            filled
                            label="Senha"
                            v-model="email"
                            :state="getValidationState(validationContext)"
                            class="d-flex justify-content-center mb-3"
                            :error-messages="validationContext.errors[0]"
                            required
                        />
                    </validation-provider>
                    <validation-provider
                        name="Nome fantasia"
                        :rules="{ required: true }"
                        v-slot="validationContext"
                    >
                        <v-text-field
                            filled
                            label="Nome fantasia"
                            v-model="name"
                            :state="getValidationState(validationContext)"
                            class="d-flex justify-content-center mb-3"
                            :error-messages="validationContext.errors[0]"
                            required
                        />
                    </validation-provider>
                    <validation-provider
                        name="CNPJ"
                        :rules="{ required: true }"
                        v-slot="validationContext"
                    >
                        <v-text-field
                            filled
                            label="CNPJ"
                            v-model="cnpj"
                            :state="getValidationState(validationContext)"
                            class="d-flex justify-content-center mb-3"
                            :error-messages="validationContext.errors[0]"
                            required
                        />
                    </validation-provider>
                    <validation-provider
                        name="Responsável"
                        :rules="{ required: true }"
                        v-slot="validationContext"
                    >
                        <v-text-field
                            filled
                            label="Responsável"
                            v-model="responsible"
                            :state="getValidationState(validationContext)"
                            class="d-flex justify-content-center mb-3"
                            :error-messages="validationContext.errors[0]"
                            required
                        />
                    </validation-provider>
                    <validation-provider
                        name="Telefone"
                        :rules="{ required: true }"
                        v-slot="validationContext"
                    >
                        <v-text-field
                            filled
                            label="Telefone"
                            v-model="phone"
                            :state="getValidationState(validationContext)"
                            class="d-flex justify-content-center mb-3"
                            :error-messages="validationContext.errors[0]"
                            required
                        />
                    </validation-provider>
                    <validation-provider
                        name="Endereço"
                        :rules="{ required: true }"
                        v-slot="validationContext"
                    >
                        <v-text-field
                            filled
                            label="Endereço"
                            v-model="address"
                            :state="getValidationState(validationContext)"
                            class="d-flex justify-content-center mb-3"
                            :error-messages="validationContext.errors[0]"
                            required
                        />
                    </validation-provider>
                    <validation-provider
                        name="Número"
                        :rules="{ required: true }"
                        v-slot="validationContext"
                    >
                        <v-text-field
                            filled
                            label="Número"
                            type="number"
                            v-model="number"
                            :state="getValidationState(validationContext)"
                            class="d-flex justify-content-center mb-3"
                            :error-messages="validationContext.errors[0]"
                            required
                        />
                    </validation-provider>
                    <validation-provider
                        name="Cidade"
                        :rules="{ required: true }"
                        v-slot="validationContext"
                    >
                        <v-text-field
                            filled
                            label="Cidade"
                            v-model="city"
                            :state="getValidationState(validationContext)"
                            class="d-flex justify-content-center mb-3"
                            :error-messages="validationContext.errors[0]"
                            required
                        />
                    </validation-provider>
                    <validation-provider
                        name="UF"
                        :rules="{ required: true, min: 2, max: 2 }"
                        v-slot="validationContext"
                    >
                        <v-text-field
                            filled
                            label="UF"
                            v-model="uf"
                            :state="getValidationState(validationContext)"
                            class="d-flex justify-content-center mb-3"
                            :error-messages="validationContext.errors[0]"
                            required
                        />
                    </validation-provider>
                    <v-btn
                        outlined
                        class="mr-2 primary mb-2"
                        dark
                        @click.stop.prevent="passes(forward)"
                        width="100%"
                    >
                        Criar
                    </v-btn>
                    <v-btn
                        outlined
                        class="mr-2"
                        width="100%"
                        @click="$router.push({ name: 'home' })"
                    >
                        Cancelar
                    </v-btn>
                </validation-observer>
            </v-col>
            <v-col v-if="!isMobile()"> </v-col>
        </v-row>
    </div>
</template>

<script>
export default {
    name: "Signup",
    data() {
        return {
            email: null,
            password: null,
            name: null, 
            cnpj: null,
            phone: null,
            responsible: null,
            address: null,
            number: null,
            city: null,
            uf: null
        };
    },
    methods: {
        getValidationState({ dirty, validated, valid = null }) {
            return dirty || validated ? valid : null;
        },
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
