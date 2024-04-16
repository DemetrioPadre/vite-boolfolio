<script>

import axios from 'axios';
import { api } from '../store';

import ProjectCard from '../components/ProjectCard.vue';

export default {
    data() {
        return {
            title: "Il mio Progett",
            project: null
        };
    },
    components: { ProjectCard },

    created() {
        const projectTitle = this.$route.params.title;
        axios.get(api.baserUrl + `project/${projectTitle}`).then((response) => {
            this.project = response.data;
        });
    },

};
</script>

<template>
    <div class="row">
        <project-card :project="project" :isDetail="true" />
    </div>



</template>


<style lang="scss">
@import '/src/scss/general.scss';
</style>