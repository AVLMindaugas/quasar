<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-avatar class="q-mx-xl">
          <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg" />
        </q-avatar>
        <q-tabs v-model="tab">
          <q-tab name="page1" label="Page #1" />
          <q-tab name="page2" label="Page #2" />
          <q-tab name="page3" label="Page #3" />
        </q-tabs>
      </q-toolbar>
    </q-header>
    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const tab = ref('page1');
</script>
