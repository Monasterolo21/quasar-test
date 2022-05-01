<template>
  <q-page class="flex flex-center">
    <q-row>
      <q-col>
        <p class="content">
          {{ currentFact }}
        </p>
      </q-col>
    </q-row>

    <q-row>
      <q-col>
        <q-btn @click="fetchFact()" label="Get Fact" color="primary" flat />
      </q-col>
    </q-row>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "IndexPage",

  data() {
    return {
      currentFact: "",
    };
  },

  methods: {
    async fetchFact() {
      const response = await fetch("https://catfact.ninja/fact");
      const data = await response.json();
      this.currentFact = data.fact;
    },
  },

  mounted() {
    this.fetchFact();
  },
});
</script>

<style scoped>
.content {
  font-size: 1.5em;
  padding: 2em;
}
</style>
