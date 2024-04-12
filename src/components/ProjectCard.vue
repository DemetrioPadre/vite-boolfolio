<script>
export default {
    props: {
        project: Object
    },
    computed: {
        abstract() {
            const content = this.project.content;
            return content.lenght > 20 ? content.substring(0, 20) + '...' : content;
        }
    }
};
</script>
<template>

    <div class="col">
        <div class="card h-100 mb-5">
            <img v-if="project.image" :src="project.image" class="card-img-top">
            <div class="card-body">
                <span :style="'background-color:' + project.type.color" class=" badge mt-2 mb-4">{{
                project.type.label }}</span>
                <p class=" card-text">{{ project.id }}</p>
                <h5 class="card-title">{{ project.title }}</h5>
                <p class="card-text">{{ abstract }}</p>
                <a href="#" class="btn btn-primary">Go somewhere</a>
            </div>
            <div class="card-footer">
                <span :style="'background-color:' + technology.color" class=" badge me-3"
                    v-for=" technology in project.technologies">{{ technology.label }}</span>
            </div>
        </div>
    </div>



</template>
<style lang="scss"></style>