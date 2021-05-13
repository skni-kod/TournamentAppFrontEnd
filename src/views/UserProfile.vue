<template>
    <v-card height="500" class="overflow-hidden">
      <v-navigation-drawer
        v-model="drawer"
        color="rgb(27,47,87)"
        absolute
        dark
      >
        <v-list dense nav class="py-0">
          <v-list-item two-line :class="miniVariant && 'px-0'">
            <v-list-item-avatar>
              <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Frisibank.fr%2Fcache%2Fstickers%2Fd1973%2F197365-full.png&f=1&nofb=1" />
            </v-list-item-avatar>

            <v-list-item-content>
              <v-list-item-title>Imie Nazwisko</v-list-item-title>
              <v-list-item-subtitle>Klub?</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>

          <v-divider></v-divider>

          <v-list-item v-for="item in items" :key="item.title" link>
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
    </v-card>
</template>

<script>
import Vue from 'vue';
import { Component } from 'vue-property-decorator';

@Component
export default class Home extends Vue {
  data() {
    return {
        drawer:true,
        items:[
            {title:'Ogolne',icon:'mdi-view-dashboard'},
            {title:'Historia',icon:'mdi-view-dashboard'},
            {title:'Edycja',icon:'mdi-view-dashboard'},
        ]
    };
  }
}
</script>

<style>
</style>