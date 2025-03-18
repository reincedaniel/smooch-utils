<template>
  <q-page class="q-pa-md flex flex-center column">
    <q-card class="q-pa-md shadow-2 rounded-borders" style="width: 90%; max-width: 600px;">
      <q-card-section>
      <div class="text-h6 text-bold color-smooch">Token Generator</div>
      <div class="text-caption text-bold color-smooch q-ml-xs">- Fill in all the fields</div>
      </q-card-section>

      <q-card-section>
      <q-input v-model="userId" label="APP ID *" type="text" filled dense :rules="[val => !!val || 'APP ID is required']" />
      <q-input v-model="keyId" label="Key ID *" type="text" filled dense class="q-mt-md" :rules="[val => !!val || 'Key ID is required']" />
      <q-input v-model="secret" label="Secret *" type="text" filled dense class="q-mt-md" :rules="[val => !!val || 'Secret is required']" />
      <q-btn @click="generateToken" class="bg-smooch text-white q-mt-md full-width" :disable="!userId || !keyId || !secret">Generate Token</q-btn>
      </q-card-section>

      <q-card-section v-if="token">
      <q-banner dense class="bg-grey-2 q-pa-md">
        <div class="text-subtitle2 q-mb-xs">Generated Token:</div>
        <q-input v-model="token" readonly filled type="textarea" autogrow />
        <q-btn flat color="secondary" label="Copy" class="q-mt-sm" @click="copyToken" />
      </q-banner>
      </q-card-section>

      <q-card-section>
      <q-btn flat color="yellow-8" label="Instructions" @click="showInstructions">
        <q-icon name="help" />
      </q-btn>
      </q-card-section>
    </q-card>

    <q-dialog v-model="instructionsDialog" maximized>
      <q-card>
        <q-card-section>
          <div class="text-h6">Instructions</div>
        </q-card-section>
        <div class="row text-body1 q-ma-md">
          <div class="row">
            <img src="/setting.png" alt="Instructions" class="col-6" />
          <div class="q-ml-md col">
        <div class="text-subtitle2 text-bold">How to Use:</div>
        <ul class="q-mt-sm">
          <li>1- <b class="text-bold">APP ID</b>.</li>
          <li>2- <b class="text-bold">Create new API Key</b> button to create your keys.</li>
          <li>3- <b class="text-bold">ID</b> (Key ID).</li>
          <li>4- <b class="text-bold">Secret</b>.</li>


        </ul>
          </div>
          </div>

        </div>
        <q-card-actions align="right">
          <q-btn icon="close"  label="Close" class="bg-smooch text-white" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'
import { SignJWT } from 'jose'

const secret = ref('')
const keyId = ref('')
const userId = ref('')
const token = ref('')
const instructionsDialog = ref(false)
const showInstructions = () => instructionsDialog.value = !instructionsDialog.value
async function generateToken() {
  try {
    const encoder = new TextEncoder()
    const secretKey = encoder.encode(secret.value)

    const jwt = await new SignJWT({ scope: 'app' })
      .setProtectedHeader({ alg: 'HS256', typ: 'JWT', kid: keyId.value })
      .sign(secretKey)

    token.value = jwt
  } catch (err) {
    console.error(err)
    token.value = 'Error generating token! Please check the data.'
  }
}

function copyToken() {
  navigator.clipboard.writeText(token.value)
}
</script>

<style scoped>
.rounded-borders {
  border-radius: 12px;
}
</style>
