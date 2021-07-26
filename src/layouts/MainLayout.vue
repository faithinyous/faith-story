<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
<!--        <q-btn-->
<!--          flat-->
<!--          dense-->
<!--          round-->
<!--          icon="menu"-->
<!--          aria-label="Menu"-->
<!--          @click="toggleLeftDrawer"-->
<!--        />-->

        <q-toolbar-title class='row'>
          <div v-for='item in topMenu' :key='item' class='q-mx-md text-bold'>
            <q-btn flat size='lg' @click='pushToPage(item)'>
              {{item.title}}
            </q-btn>
          </div>
        </q-toolbar-title>


        <div class='text-secondary text-h4 text-bold' style='text-shadow:2px 2px #ce8123'>Apiporn Simapornchai </div>
      </q-toolbar>
    </q-header>

<!--    <q-drawer-->
<!--      v-model="leftDrawerOpen"-->
<!--      show-if-above-->
<!--      bordered-->
<!--      class="bg-grey-1"-->
<!--    >-->
<!--      <q-list>-->
<!--        <q-item-label-->
<!--          header-->
<!--          class="text-grey-8"-->
<!--        >-->
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
import EssentialLink from 'components/EssentialLink.vue'

import { Vue, Options } from 'vue-class-component'
interface MenuData{
  title: string,
  caption: string,
  link: string,
  newPage?: boolean|false
}
@Options({
  components: { EssentialLink }
})
export default class MainLayout extends Vue {
   topMenu = [
    {
      title: 'Home',
      caption: 'Home',
      link: '/'
    },
    {
      title: 'Info',
      caption: 'Info',
      link: '/info'
    },
    {
      title: 'Bio',
      caption: 'Bio',
      link: '/bio'
    },
    {
      title: 'LinkedIn',
      caption: 'LinkedIn',
      link: '/',
      newPage:true
    },
    {
      title: 'Contact',
      caption: 'Contact',
      link: '/contact'
    }
  ] as MenuData[]
  leftDrawerOpen = false;
  pushToPage(data:MenuData){
    if(data.newPage){

    }
    else{
      console.log(data.link,'data.link');
      this.$router.push({ path: data.link})
    }
  }
  toggleLeftDrawer () {
    this.leftDrawerOpen = !this.leftDrawerOpen
  }
}
</script>
