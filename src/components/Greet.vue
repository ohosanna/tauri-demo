<script setup lang="ts">
import { ref } from "vue";
import { invoke } from "@tauri-apps/api/tauri";
import { Command } from '@tauri-apps/api/shell';

const greetMsg = ref("");
const name = ref("");

async function greet() {
  // Learn more about Tauri commands at https://tauri.app/v1/guides/features/command
  greetMsg.value = await invoke("greet", { name: name.value });
}
async function sidecar() {
  const command = Command.sidecar('binaries/hello', [
    '-u',
    name.value
  ])
  const output = await command.execute()
  greetMsg.value = output.stdout.trim()
}
</script>

<template>
  <div class="card">
    <input id="greet-input" v-model="name" placeholder="Enter a name..." />
    <button type="button" @click="greet()">Greet</button>
    <button type="button" @click="sidecar()">Hello</button>
  </div>

  <p>{{ greetMsg }}</p>
</template>
