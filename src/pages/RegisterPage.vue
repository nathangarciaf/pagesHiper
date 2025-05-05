<template>
  <q-page class="row items-center justify-evenly">
    <q-card class="q-pa-md shadow-10">
      <q-card-section>
        <div class="text-h4 text-bold">Cadastro de Usuários</div>
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
              v-if="password.length > 0"
              :name="isPwdVisible ? 'visibility_off' : 'visibility'"
              class="cursor-pointer"
              @click="isPwdVisible = !isPwdVisible"
            />
          </template>
        </q-input>

        <q-input
          v-model="confirmPassword"
          :type="isPwdVisible ? 'text' : 'password'"
          label="Confirmar Senha"
          class="q-mb-md"
        >
          <template #append>
            <q-icon
              v-if="confirmPassword.length > 0"
              :name="isPwdVisible ? 'visibility_off' : 'visibility'"
              class="cursor-pointer"
              @click="isPwdVisible = !isPwdVisible"
            />
          </template>
        </q-input>

        <q-btn
          label="Cadastrar"
          color="primary"
          class="full-width q-mb-md"
          @click="handleRegister"
        />

        <div class="text-subtitle2 text-center">
          Já possui conta?
          <a href="" class="text-bold" @click.prevent="goToLogin">Entrar</a>
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
const confirmPassword = ref('');
const isPwdVisible = ref(false);
const router = useRouter();

function handleRegister() {
  if (password.value === confirmPassword.value) {
    console.log('válido');
  } else {
    console.log('inválido');
  }
}

function goToLogin() {
  router.push('/').catch((err) => {
    console.error('Erro ao navegar:', err);
  });
}
</script>
