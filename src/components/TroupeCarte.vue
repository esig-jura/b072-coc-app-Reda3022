<script setup>
defineProps({
  troupe: {
    type: Object,
    required: true
  },
  or: {
    type: Number,
    required: true
  }
})
// Evénements
const emit = defineEmits(["former"]);
function formerTroupe(cout) {
  emit("former", cout);
}
</script>

<template>
  <article>
    <header :style="`background: url('img/${troupe.imageFond}')`">
      <img :src="'img/' + troupe.image" :alt="troupe.nom" />
    </header>

    <div class="level" :style="`color: ${troupe.couleur}`">Niveau {{ troupe.niveau }}</div>

    <h2 class="name">{{ troupe.nom }}</h2>

    <button
        :style="`background-color: ${troupe.couleur}`"
        @click="formerTroupe(troupe.cout)"
        :disabled="or < troupe.cout"
    >
      Former
      <img src="/img/piece-or.png" alt="Former" />
    </button>

    <p class="description">
      {{ troupe.description }}
    </p>

    <footer>
      <div class="training" :style="`background-color: ${troupe.couleur}`">
        <div v-if="troupe.formation > 60">
          {{ Math.round(troupe.formation / 60) }}<sup>min </sup>
        </div>
        <div v-else>{{ troupe.formation }}<sup>sec</sup></div>
        <div>Formation</div>
      </div>

      <div class="speed" :style="`background-color: ${troupe.couleur}`">
        <div>{{ troupe.vitesse }}</div>
        <div>Vitesse</div>
      </div>

      <div class="cost" :style="`background-color: ${troupe.couleur}`">
        <div>{{ troupe.cout }}</div>
        <div>Coût</div>
      </div>
    </footer>
  </article>
</template>

<style scoped lang="scss">
article header {
  position: relative;
  height: 230px;
  padding: 0;
  margin-bottom: 35px;
  border-top-left-radius: 14px;
  border-top-right-radius: 14px;
  text-align: center;
}

article header img {
  width: 400px;
  position: absolute;
  top: -65px;
  left: -70px;
}

/*** Contenu ***/
article .level {
  text-transform: uppercase;
  font-size: 12px;
  font-weight: 700;
  margin-bottom: 3px;
}

article h2 {
  font-size: 26px;
  color: black;
  font-weight: 900;
  margin-bottom: 5px;
}

article button {
  color: white;
  background: #9E9E9E;
  margin: 20px 0 0;
  padding: .75em 1.5em;
}

article p.description {
  padding: 20px;
  margin-bottom: 100px;
}

/*** Footer ***/
article footer {
  position: absolute;
  width: 100%;
  bottom: 0;
  color: white;
  font-weight: 700;
  border-bottom-left-radius: 14px;
  border-bottom-right-radius: 14px;
  overflow: hidden;
}

article footer > div {
  width: calc(100% / 3);
  float: left;
  padding: 20px 15px;
}

article footer sup {
  position: absolute;
  bottom: 4px;
  font-size: 45%;
  margin-left: 2px;
}

article footer > div > div:first-child {
  position: relative;
  font-size: 24px;
  margin-bottom: 10px;
}

article footer > div > div:first-child + div {
  text-transform: uppercase;
  font-weight: 400;
  font-size: 12px;
}

article footer > div {
  border-right: 1px solid rgba(0, 0, 0, .1);
}

article footer > div:last-child {
  border-right: none;
}

</style>