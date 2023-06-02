<script setup>
// Cheat Sheet: https://steve-fallet.notion.site/Vue-3-script-setup-Cheat-Sheet-b12192ceae244ecda65f771579ca02bc
import {reactive, ref} from 'vue'
import PageHeader from "@/components/PageHeader.vue";
import PageFooter from "@/components/PageFooter.vue";
import TroupeCarte from "@/components/TroupeCarte.vue";
import PageTopBarre from "@/components/PageTopBarre.vue";

// Datas statiques
const titre = 'Clash of Clans'
const description = 'Construire un village, former un clan et participer à' +
    ' des guerres de clans épiques !'
const site = 'https://supercell.com/en/games/clashofclans/'
// Datas réactive primitive avec une valeur simple
const totalOr = ref(20000)
// Datas réactive complexe avec plusieurs propriétés
const troupes = reactive([
           {
             id: 1,
             nom: 'Barbare',
             description: 'Ce guerrier intrépide compte sur ses muscles saillants et sa fière moustache pour semer le chaos dans les villages ennemis. Faites charger une horde de barbares et profitez du spectacle !',
             image: 'barbare.png',
             imageFond: 'barbare-bg.jpg',
             couleur: '#EC9B3B',
             niveau: 4,
             formation: 20,
             vitesse: 16,
             cout: 150
           },
           {
             id: 2,
             nom: 'Archer',
             description: 'Ces tireurs d\'élite préfèrent garder leurs distances, aussi bien sur le champs de bataille que dans la vie. Ils n\'aiment rien tant que de voir tomber la cible sur laquelle ils ont jeté leur dévolu.',
             image: 'archer.png',
             imageFond: 'archer-bg.jpg',
             couleur: '#EE5487',
             niveau: 5,
             formation: 25,
             vitesse: 24,
             cout: 300
           },
           {
             id: 3,
             nom: 'Géant',
             description: 'Ces grands gaillards semblent calmes de prime abord, mais ils se déchaîneront à la simple vue d\'une tourelle ou d\'un canon ! Lents mais résistants, ces guerriers sont faits pour encaisser les coups.',
             image: 'giant.png',
             imageFond: 'giant-bg.jpg',
             couleur: '#F6901A',
             niveau: 5,
             formation: 120,
             vitesse: 12,
             cout: 2250
           },
           {
             id: 4,
             nom: 'Gobelin',
             description: 'Ces petites créatures agaçantes ne pensent qu\'à une chose: le BUTIN ! Ils sont plus rapides qu\'un piège à ressort, et leur appétit pour les ressources est sans limite.',
             image: 'goblin.png',
             imageFond: 'goblin-bg.jpg',
             couleur: '#82BB30',
             niveau: 5,
             formation: 30,
             vitesse: 32,
             cout: 100
           },
           {
             id: 5,
             nom: 'Dragon',
             description: 'Les dragons sont connus à travers tout le territoire pour leur puissance sans égal. Cette terreur écailleuse du ciel ne montre aucune pitié ; et rien n\'échappe à son souffle mortel.',
             image: 'dragon.png',
             imageFond: 'dragon-bg.jpg',
             couleur: '#5F3A59',
             niveau: 2,
             formation: 720,
             vitesse: 16,
             cout: 12000
           }
         ])


// Méthodes
function formerTroupe(cout) {
  if(totalOr.value < cout) {
    alert("Vous n'avez pas assez d'or mon seigneur !")
    return
  }
  totalOr.value -= cout
}

</script>

<template>
  <div id="app">

  <!--    Ajouter le composant PageTopBarre.vue dans App.vue à la place de <div class="solde-or">
  et lui passer totalOr de App.vue via la propriété or.-->
  <!--    Ne pas oublier de mettre : devant or pour indiquer que vous passez
   une instruction JavaScript, et non une valeur statique.-->

    <PageTopBarre :or="totalOr" />


    <PageHeader :site="site" :description="description" :titre="titre"/>


    <main>
      <ul class="cartes">
        <li v-for="trp in troupes" :key="trp.id">
<!--          c'est ca commet mettre un composant avec une boucle for-->
<!--          apres ajoute : pour dir que cest du javascripte pour faire reference au-->
<!--          parametres qui sont dans le composant Troupe carte vue-->
          <TroupeCarte :or="totalOr"
                       :troupe="trp"
                       @former="formerTroupe"
          /><!--                       ajouter un evenemet avec cette methode @-->
        </li>
      </ul>
    </main>
  </div>
  <PageFooter :site="site"/>
</template>

<style scoped lang="sass">
///* https://sass-lang.com/guide */
//$primary: #800080
//$secondary: #fefefe
//
//h1
//  color: $primary
//  text-align: center
//
//ul
//  list-style: none
//  display: flex
//  flex-wrap: wrap
//  justify-content: center
//  li
//    color: $secondary
//    background-color: $primary
//    margin: 1rem
//    padding: 1rem
//    max-width: 200px

</style>