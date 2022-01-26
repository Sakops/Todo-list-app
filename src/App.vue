<template>
  <div id="app">
    <todo />
  </div>
</template>

<script lang="tsx">
import { Component, Vue } from "vue-property-decorator";
import todo from "@/components/Todo.vue";

@Component({
  components: {
    todo,
  },
})
export default class App extends Vue {}
</script>

<style>

</style>
