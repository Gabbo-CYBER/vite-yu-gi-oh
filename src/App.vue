<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';
import { store } from './data/store';
import { archeType } from './data/store';

import axios from 'axios';


export default {
  components: {
    AppHeader,
    AppMain,
    AppFooter,


  },
  data() {
    return {
      store,
      archeType
    }
  },
  mounted() {
    axios.get(this.store.urlAPI).then(r => {
      this.store.cardElement = [];
      this.store.cardElement = r.data.data;
    })
    axios.get(this.archeType.urlAPI).then(a => {
      archeType.archeTypeList = a.data;
    })
  },
}
</script>

<template>
  <header>
    <AppTitle />
  </header>

  <main>
    <AppFilter />
    <AppMain />
    <!-- <span v-else>Sono in attesa di dati v-if="store.loading == false"</span> -->
  </main>

  <footer></footer>
</template>

<style scoped>
main {
  background-color: #C68636;
}
</style>
