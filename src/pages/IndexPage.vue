<template>
  <q-page class="q-pa-lg bg-grey-2">
    <div class="text-h4 q-mb-md">Page #1</div>
    <q-card flat bordered class="full-width full-height">
      <q-card-section>
        <div class="row q-col-gutter-md q-mb-lg">
          <template v-for="i in 8" :key="i">
            <q-select
              class="col-3"
              v-model="model"
              :options="options"
              :label="`Select #${i}`"
            />
          </template>
        </div>
        <q-table title="Table" :rows="rows" :columns="columns" row-key="name">
          <template v-slot:body-cell-column-7="props">
            <q-td :props="props">
              <q-toggle v-model="toggleModel" />
            </q-td>
          </template>
          <template v-slot:body-cell-column-5="props">
            <q-td :props="props">
              <q-icon name="check" color="green" />
            </q-td>
          </template>
          <template v-slot:body-cell-column-3="props">
            <q-td :props="props">
              <q-chip v-for="i in 5" :key="i" size="sm">{{
                `Tag ${i}`
              }}</q-chip>
            </q-td>
          </template>
        </q-table>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script setup lang="ts">
import { QTableColumn } from 'quasar';
import { ref } from 'vue';

const model = ref();
const toggleModel = ref(true);
const options = [
  'Option #1',
  'Option #1',
  'Option #1',
  'Option #1',
  'Option #1',
];
const columns = ref<QTableColumn[]>([]);
const rows = ref<Record<string, unknown>[]>([]);

for (let i = 1; i <= 8; i++) {
  columns.value.push({
    name: `column-${i}`,
    align: 'left',
    label: `Column #${i}`,
    field: `column-${i}`,
    sortable: true,
  });
}

for (let i = 1; i <= 100; i++) {
  const rowData: Record<string, unknown> = {};
  for (let c = 1; c <= 10; c++) {
    rowData[`column-${c}`] = `Col: #${c} Row: #${i}`;
  }
  rows.value.push(rowData);
}
</script>
