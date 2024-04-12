<script>
import { api, store } from '../store';
import axios from 'axios';
export default {
    data() {
        return {
            store
        };
    },
    created() {
        axios.get(api.baserUrl + 'project').then((response) => {
            store.projects = response.data.data;
        });
    }

};
</script>
<template>

    <div class="row row-cols-4 g-3">
        <div class="col" v-for="project in store.projects">
            <div class="card h-100 mb-5">
                <img v-if="project.image" :src="project.image" class="card-img-top">
                <div class="card-body">
                    <p class="card-text">{{ project.id }}</p>
                    <h5 class="card-title">{{ project.title }}</h5>
                    <p class="card-text">{{ project.content }}</p>
                    <a href="#" class="btn btn-primary">Go somewhere</a>
                </div>
            </div>
        </div>
    </div>

</template>
<style lang="scss"></style>