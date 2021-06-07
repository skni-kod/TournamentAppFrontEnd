<template>
  <v-card tile>
    <v-tabs
      v-model="x"
      background-color="secondary"
      centered
      dark
      class="rounded-sm"
      icons-and-text
    >
      <v-tab v-for="(item, id) in items" :key="id">
        <div class="d-none d-sm-flex">{{ item.tab }}</div>
        <v-icon>{{ item.icon }}</v-icon>
      </v-tab>
    </v-tabs>

    <v-tabs-items v-model="x">
      <v-tab-item v-for="(itemtab, index) in items" :key="index">
        <v-data-table
          :headers="itemtab.headers"
          :items="itemtab.positions"
          item-key="name"
          show-expand
          single-expand
          :items-per-page="10"
          class="elevation-1 rounded-sm"
        >
          <template v-slot:expanded-item="{ headers, item }">
            <td :colspan="headers.length">
              <v-row>
                <v-col class="my-auto">
                  {{ item.info }}
                </v-col>
                <v-col cols="auto" class="my-auto" v-if="itemtab.tab === 'Turnieje'">
                  <v-btn href="/tournamentInfo"
                    >Więcej o Turnieju</v-btn
                  >
                </v-col>
              </v-row>
            </td>
          </template>
        </v-data-table>
      </v-tab-item>
    </v-tabs-items>
  </v-card>
</template>

<script>
import Vue from 'vue';
import { Component } from 'vue-property-decorator';

@Component
export default class HomeTabs extends Vue {
  data() {
    return {
      x: null,
      items: [
        {
          tab: 'Turnieje',
          icon: 'mdi-tournament',
          headers: [
            { text: 'Nazwa', value: 'name', class: 'primary white--text' },
            {
              text: 'Data rozpoczęcia',
              value: 'date',
              class: 'primary white--text',
            },
            { text: 'Typ gry', value: 'type', class: 'primary white--text' },
            { text: 'Kraj', value: 'country', class: 'primary white--text' },
            {
              text: '',
              value: 'data-table-expand',
              class: 'primary white--text',
            },
          ],
          positions: [
            {
              name: 'OWC - Osu world cup',
              date: '15.05.2021',
              type: 'szybka',
              country: 'Polska',
              info: 'Tomek, dawaj streama z Osu!',
            },
            {
              name: 'Przestancie palowac pls',
              date: '23.05.2021',
              type: 'speedrun',
              country: 'Mielec',
              info: 'Nie ma żadnych dowodów na to, że Oskar wiedział o pałowaniu w kole.',
            },
          ],
        },
        {
          tab: 'Kluby',
          icon: 'mdi-account-group-outline',
          headers: [
            {
              text: 'Nazwa klubu',
              value: 'name',
              class: 'primary white--text',
            },
            { text: 'Kraj', value: 'country', class: 'primary white--text' },
            {
              text: '',
              value: 'data-table-expand',
              class: 'primary white--text',
            },
          ],
          positions: [
            {
              name: 'Pałownicy Oskara',
              country: 'Polska',
              info: 'Czy wiedziałeś, że Oskar nie przyszedł na spotkanie projektu i nie poniósł za to żadnych konsekwencji? Jeśli Ty też chcesz wymierzyć mu sprawiedliwość to dołącz do naszego zespołu.',
            },
            {
              name: 'Kocham Matematykę Dyskretną',
              country: 'Mielec',
              info: 'Jeśli istnieje tylko 1 minimalny zbiór totalnie dominujący to jest on podzbiorem każdego zbioru totalnie dominującego',
            },
          ],
        },
      ],
    };
  }
}
</script>
