<template>
  <q-page class="row items-center justify-evenly">
    <q-card class="q-pa-md shadow-10">
      <q-card-section>
        <div class="text-h4 text-bold">Login do Sistema</div>
      </q-card-section>

      <q-card-section class="q-pt-none">
        <q-input v-model="username" label="Usuário" class="q-mb-md" />
        <q-input
          v-model="password"
          :type="isPwdVisible ? 'text' : 'password'"
          label="Senha"
          class="q-mb-md"
        >
          <template #append>
            <q-icon
              :name="isPwdVisible ? 'visibility_off' : 'visibility'"
              class="cursor-pointer"
              @click="isPwdVisible = !isPwdVisible"
            />
          </template>
        </q-input>
        <q-btn label="Cadastrar" color="primary" class="full-width q-mb-md" @click="handleLogin" />
        <div class="text-subtitle2 text-center">
          Não possui conta?
          <a href="" class="text-bold" @click.prevent="goToRegister">Cadastre-se</a>
        </div>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { useRouter } from 'vue-router';

const username = ref('');
const password = ref('');
const isPwdVisible = ref(false);
const router = useRouter();

function handleLogin() {
  console.log('Login clicado', username.value, password.value);
}

function goToRegister() {
  router.push('/register').catch((err) => {
    console.error('Erro ao navegar:', err);
  });
}
</script>
