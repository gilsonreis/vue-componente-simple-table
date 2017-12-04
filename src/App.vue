<template>
  <div id="app">
    <simple-table :headers='headers'
                  :list="names"></simple-table>
  </div>
</template>

<script>
  import Vue from 'vue'
  import VueResource from 'vue-resource'
  import simpleTable from './SimpleTable.vue'

  Vue.use(VueResource)

export default {
  name: 'app',
  data() {
    return {
      names: [],
      headers: []
    }
  },
  components: {simpleTable},
  created() {
    this.getHeaders();
    this.getData();
  },
  methods: {
    getHeaders() {
      this.headers = ['Nome', 'Ano de Nasc.', 'Altura', 'Cor dos olhos']
    },
    getData() {
      this.$http.get('https://swapi.co/api/people/').then(response => {
        for(let item of response.body.results) {
          this.names.push({
            nome: item.name,
            nasc: item.birth_year,
            altura: item.height / 100,
            cor_olhos: item.eye_color
          });
        }
      });
    }
  }
}
</script>

