<script>
import axios from 'axios';
import { api, store } from './store';
import AppHeader from './components/AppHeader.vue';

export default {
  data() {
    return {
      store,
      title: "BOOLFOLIO FRONTEND",



    };
  },

  components: {
    AppHeader
  },
  created() {
    axios.get(api.baserUrl + 'project').then((response) => {
      store.projects = response.data.data;
    });
  }
};
</script>

<template>
  <app-header :title="title" />


  <div class="container mt-5">
    <h1>{{ title }}</h1>


    <div v-for="project in store.projects">
      <ul>
        <li><strong>ID:</strong>{{ project.id }}</li>
        <li>
          <strong>Title:</strong>{{ project.title }}
        </li>
        <li> <strong>Contenuto:</strong>{{ project.content }}
        </li>
      </ul>
    </div>
  </div>



</template>


<style lang="scss">
@import '/src/scss/general.scss';
</style>