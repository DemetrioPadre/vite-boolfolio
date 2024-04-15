<script>

import axios from 'axios';
import { api } from '../store';

import ProjectCard from '../components/ProjectCard.vue';

export default {
    data() {
        return {
            project: null
        };
    },
    components: { ProjectCard },

    created() {
        const projectSlug = this.$route.params.slug;
        axios.get(api.baserUrl + `project/${projectSlug}`).then((response) => {
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