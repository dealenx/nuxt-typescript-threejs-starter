<template>
  <section>
    <h1 class="header">Nuxt TypeScript Starter</h1>
    <Scene ></Scene>
  </section>
</template>

<script lang="ts">
import {
  Component,
  Vue
} from "nuxt-property-decorator"
import { State } from "vuex-class"
import Scene from "~/components/Scene.vue"

@Component({
  components: {
    Scene
  }
})
export default class extends Vue {
  //@State people
}
</script>
<style scoped>
.header {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana,
    sans-serif;
}

.cards {
  display: flex;
  flex-wrap: wrap;
}
</style>