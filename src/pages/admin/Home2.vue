<!-- <template>
  <q-page class="flex flex-center">
    <Qalendar 
      :events="events" 
      :config="config"
    />
  </q-page>
</template>

<script>
import { defineComponent } from 'vue';
import { Qalendar } from "qalendar";

export default defineComponent({
  name: 'AdminCalendar',
  components: {
      Qalendar,
  },

  data() {
      return {
          events: [
              // ...
              {
                title: "Advanced algebra",
                with: "Chandler Bing",
                time: { start: "2022-11-28 12:00", end: "2022-10-10 13:35" },
                color: "yellow",
                isEditable: true,
                id: "753944708f0f",
                description: "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Asperiores assumenda corporis doloremque et expedita molestias necessitatibus quam quas temporibus veritatis. Deserunt excepturi illum nobis perferendis praesentium repudiandae saepe sapiente voluptatem!"
              },
              {
                title: "Ralph on holiday",
                with: "Rachel Greene",
                time: { start: "2022-11-29 08:00", end: "2022-10-10 10:00"},
                colorScheme: 'sports',
                isEditable: false,
                id: "5602b6f589fc",
                description: "asd"
              },
              {
                title: "asd",
                with: "aasde",
                time: { start: "2022-11-30 10:00", end: "2022-10-10 11:00"},
                isEditable: true,
                id: "5602b6f589fc",
                description: "asd"
              }
              // ...
          ],
          config: {
              // defaultMode: "month",
              style: {
                  colorSchemes: {
                      meetings: {
                          color: 'red',
                          backgroundColor: '#131313',
                      },
                      sports: {
                          color: '#fff',
                          backgroundColor: 'red',
                      }
                  }
              }
          },
      };
  },
})
</script>

<style>
@import '/node_modules/qalendar/dist/style.css';
</style> -->