<template>
  <div class="p-2">
    <h1 class="text-4xl text-center font-serif p-5 font-bold hero">
      Mythic Game Master Tool
    </h1>
    <div class="flex flex-wrap">
      <boutton
        v-for="bt in btList"
        :key="bt.id"
        :bt-name="bt.name"
        @click="tirage(bt.proba)"
      />
    </div>
    <div
      class="text-2xl text-center bg-gray-300 p-2 font-black"
      :class="{
        'bg-green-300': reponse == 'OUI',
        'text-green-600': reponse == 'OUI',
        'bg-red-300': reponse == 'NON',
        'text-red-600': reponse == 'NON',
      }"
    >
      {{ reponse }}
    </div>
    <div class="font-mono font-thin p-2 bg-yellow-50">
      <p v-for="(log, idx) in logTirage" :key="idx">{{ log }}</p>
    </div>
  </div>
</template>

<script>
import Boutton from "./components/Boutton.vue";
export default {
  name: "App",
  data() {
    return {
      btList: [
        { proba: 99, id: "IM", name: "Impossible" },
        { proba: 85, id: "QI", name: "Quasi Impossible" },
        { proba: 70, id: "I", name: "Improbable" },
        { proba: 60, id: "PP", name: "Peu probable" },
        { proba: 50, id: "50", name: "50/50" },
        { proba: 40, id: "AP", name: "Assez probable" },
        { proba: 30, id: "P", name: "Probable" },
        { proba: 20, id: "QS", name: "Quasi sûr" },
        { proba: 10, id: "S", name: "Sûr" },
      ],
      reponse: "",
      logTirage: [],
    };
  },
  components: { Boutton },
  methods: {
    tirage(proba) {
      this.reponse = "";
      let tirage = Math.floor(Math.random() * 100);
      this.reponse = "NON";
      if (tirage >= proba) {
        this.reponse = "OUI";
      }
      this.logTirage.unshift(
        `proba: ${proba}, tirage: ${tirage}, reponse: ${this.reponse}`
      );
    },
  },
};
</script>

<style>
@tailwind base;
@tailwind components;
@tailwind utilities;
.hero {
  background-color: #dfdbe5;
  background-image: url("assets/topography.svg");
}
</style>
