<template>
  <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
    <q-card class="fit">
      <q-card-section class="text-h6 q-pb-none">
        <q-item>
          <q-item-section avatar class="">
            <q-icon color="blue" name="access_time" style="font-size: 2em;"/>
          </q-item-section>

          <q-item-section>
            <div class="text-h6">Agendamento de Clientes</div>
          </q-item-section>
        </q-item>
      </q-card-section>
    </q-card>
    <q-card class="row">
      <q-input filled borderless dense debounce="300" class="q-pa-md q-gutter-sm col-lg-6 col-md-6 col-sm-12 col-xs-6" label="Nome do Cliente" />
      <div class="q-pa-md q-gutter-sm">
        <q-btn push color="grey-4" text-color="primary" glossy>
          <div class="row items-center no-wrap">
            <q-icon left name="person_search" />
            <div class="text-center">
              Pesquisar Cliente
            </div>
          </div>
        </q-btn>
      </div>
    </q-card>
    <div class="q-pa-md">
      <q-card class="fit">
        <q-table
          title="Listagem de Clientes"
          :rows="rows"
          :columns="columns"
          row-key="name"
          selection="multiple"
          :filter="filter"
          grid
          hide-header
        >
          <template v-slot:top-right>
            <q-input borderless dense debounce="300" v-model="filter" placeholder="Search">
              <template v-slot:append>
                <q-icon name="search" />
              </template>
            </q-input>
          </template>
          
          <template v-slot:item="props">
          <div
            class="q-pa-xs col-xs-12 col-sm-6 col-md-4 col-lg-3 grid-style-transition"
            :style="props.selected ? 'transform: scale(0.95);' : ''"
          >
            <q-card :class="props.selected ? 'bg-grey-2' : ''">
              <q-separator />
              <q-list dense>
                <q-item v-for="col in props.cols.filter(col => col.name !== 'desc')" :key="col.name">
                  <q-item-section>
                    <q-item-label>{{ col.label }}</q-item-label>
                  </q-item-section>
                  <q-item-section side>
                    <q-item-label caption>
                      <q-item-label v-if="col.name == 'name'">{{ col.value }}</q-item-label>
                      <q-item-label v-if="col.name == 'scheduling_enable'">{{ col.value }}</q-item-label>
                      <q-item-label v-if="col.name == 'next_scheduling'">{{ col.value }}</q-item-label>
                      <q-btn v-if="col.name == 'shecduling'">{{ col.value }}</q-btn>
                    </q-item-label>
                  </q-item-section>
                </q-item>
              </q-list>
            </q-card>
          </div>
        </template>
        </q-table>
      </q-card>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  name: 'Scheduling',
  components: { },
  setup(){
    const filter = ref();
    return {
      filter
    }
  },
  data() {
    function padTo2Digits(num) {
      return num.toString().padStart(2, '0');
    }

    function formatDate(date) {
      return [
        padTo2Digits(date.getDate()),
        padTo2Digits(date.getMonth() + 1),
        date.getFullYear(),
      ].join('/');
    }
    const rows = [
        {
        name: 'Cliente 1',
        scheduling_enable: "Sim",
        next_scheduling: formatDate(new Date()),
        shecduling: true,
        carbs: 24,
        protein: 4.0,
        sodium: 87,
        calcium: '14%',
        iron: '1%'
      },
      {
        name: 'Cliente 2',
        scheduling_enable: "Não",
        next_scheduling: null,
        shecduling: true,
        carbs: 37,
        protein: 4.3,
        sodium: 129,
        calcium: '8%',
        iron: '1%'
      },
    ];
    const columns = [
      {
        name: 'name',
        required: true,
        label: 'Nome do Cliente',
        align: 'center',
        field: row => row.name,
        format: val => `${val}`,
        sortable: true
      },
      { name: 'scheduling_enable', align: 'center', label: 'Agendamento ativo', field: 'scheduling_enable', sortable: true },
      { name: 'shecduling', label: 'Agendar', field: 'shecduling', sortable: false },
      { name: 'next_scheduling', label: 'Próxcimo Agendamento', field: 'next_scheduling' },
      { name: 'protein', label: 'Protein (g)', field: 'protein' },
      { name: 'sodium', label: 'Sodium (mg)', field: 'sodium' },
      { name: 'calcium', label: 'Calcium (%)', field: 'calcium', sortable: true, sort: (a, b) => parseInt(a, 10) - parseInt(b, 10) },
      { name: 'iron', label: 'Iron (%)', field: 'iron', sortable: true, sort: (a, b) => parseInt(a, 10) - parseInt(b, 10) }
    ]
    return { columns, rows }
  }
};
</script>

<style>
  /* .inputText{
    margin: 10px;
  } */
</style>
