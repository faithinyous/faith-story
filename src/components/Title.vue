<template>
  <div class='text-h2 text-secondary' >
    <b> {{title}}</b>
  </div>
</template>

<script lang="ts">
import { Vue, prop } from 'vue-class-component'
class Props {
  readonly title!: string;
}
export default class TitleComponent extends Vue.with(Props) {

}
</script>
