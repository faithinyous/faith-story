<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <div>data</div>
        <!--        <q-btn-->
        <!--          flat-->
        <!--          dense-->
        <!--          round-->
        <!--          icon="menu"-->
        <!--          aria-label="Menu"-->
        <!--          @click="toggleLeftDrawer"-->
        <!--        />-->

        <q-toolbar-title class="row">
          <div v-for="item in linksList" :key="item" class="q-mx-md text-bold">
            <q-btn flat size="lg" @click="pushToPage(item)">
              {{ item.title }}
            </q-btn>
          </div>
        </q-toolbar-title>

        <!--        <div>Quasar v{{ $q.version }}</div>-->
      </q-toolbar>
    </q-header>

    <!--    <q-drawer v-model="leftDrawerOpen" show-if-above bordered class="bg-grey-1">-->
    <!--      <q-list>-->
    <!--        <q-item-label header class="text-grey-8">-->
    <!--          Essential Links-->
    <!--        </q-item-label>-->

    <!--        <EssentialLink-->
    <!--          v-for="link in essentialLinks"-->
    <!--          :key="link.title"-->
    <!--          v-bind="link"-->
    <!--        />-->
    <!--      </q-list>-->
    <!--    </q-drawer>-->

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script lang="ts">
import EssentialLink from 'components/EssentialLink.vue';

import { Vue, Options } from 'vue-class-component';
interface MenuData {
  title: string;
  caption: string;
  link: string;
  newPage?: boolean | false;
}
@Options({
  components: { EssentialLink },
})
export default class MainLayout extends Vue {
  leftDrawerOpen = false;

  linksList = [
    {
      title: 'Home',
      caption: 'Home',
      link: '/',
    },
    {
      title: 'Info',
      caption: 'Info',
      link: '/info',
    },
    {
      title: 'Bio',
      caption: 'Bio',
      link: '/bio',
    },
    {
      title: 'LinkedIn',
      caption: 'LinkedIn',
      link: 'https://www.linkedin.com/in/faithinyou/',
      newPage: true,
    },
    {
      title: 'Contact',
      caption: 'Contact',
      link: '/contact',
    },
  ] as MenuData[];

  toggleLeftDrawer() {
    this.leftDrawerOpen = !this.leftDrawerOpen;
  }
  async pushToPage(data: MenuData) {
    if (data.newPage) {
      window.open(data.link, '_blank');
    } else {
      console.log(data.link, 'data.link');
      await this.$router.push({ path: data.link });
    }
  }
}
</script>
