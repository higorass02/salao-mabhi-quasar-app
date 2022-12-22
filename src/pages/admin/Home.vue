<template>
  <q-page class="flex flex-center">
    <q-calendar-day
      ref="calendar"
      v-model="date"
      animated
    ></q-calendar-day>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue';
import { QCalendarDay } from '@quasar/quasar-ui-qcalendar/dist/QCalendarDay.esm.js'

export default defineComponent({
  name: 'AdminCalendar',
  components: {
    QCalendarDay
  },
  setup: {
    data () {
      return {
        date: '',
        version: QCalendar.version
      };
    },
    methods: {
      calendarNext () {
        this.$refs.calendar.next()
      },

      calendarPrev () {
        this.$refs.calendar.prev()
      }
    }
  }
})
</script>
<style src="@quasar/quasar-ui-qcalendar/dist/QCalendarDay.min.css"></style>