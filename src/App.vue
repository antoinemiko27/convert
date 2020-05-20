<template>
  <div class="conv">

    <div class="">
      <div class="">

        <input @keydown.enter="unitechoisie()" type="text" v-model="unite">
        <button @click="unitechoisie()" type="button" name="button">depart unit</button>
      </div>
      <div v-if="base != ''" class="">
        <input @keydown.enter="translationwork()" type="text" v-model="translation" placeholder="name/ratio">
        <button @click="translationwork()" type="button">conversion goal</button>
      </div>
    </div>





    <div v-if="base != '' && units.length != 0" class="">
      <input @keydown.enter="calculate" type="text" name="" v-model="nombre">


      <button @click="conversion()" type="button" name="submit">calculate</button>
    </div>
   <div v-if="resultat" class="resultat">
     {{resultat}} {{fetch}}
   </div>

  </div>
</template>

<script>
export default {
  data() {
    return {
      nombre: '',
      unite: '',
      translation: '',
      base: '',
      units: [],
      rate: [],
      fetch: '',
      resultat: ''
    }
  },


  methods: {




    conversion() {
      this.resultat = this.nombre * this.rate[this.units.indexOf(this.fetch)]
    },




    unitechoisie() {
      this.base = this.unite
    },





    translationwork() {
      if (this.translation.split('/')[1]) {
        this.units.push(this.translation.split('/')[0])
        this.rate.push(this.translation.split('/')[1])
        this.fetch = this.translation.split('/')[0]
      }
    }
  }
}



</script>



<style>
.conv {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 200px;
}
</style>
