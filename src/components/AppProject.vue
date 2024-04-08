<script>

export default {
    name: 'AppProject',
    props: ['title', 'content', 'slug', 'type', 'technologies', 'image'],

    components: {

    },
    data() {
        return {

        }
    },
    methods: {

    },
    mounted() {
        
    }
}
</script>

<template>
    <router-link :to="{name: 'single-project',  params: {slug: slug}}">
        <div class="card my-4" style="width: 40rem;">
            <img class="card-img-top" :src=' `http://localhost:8000/storage/${image}` ' alt="card_image">
            <div class="card-body my-4">
                <h4 class="card-title">{{title}}</h4>
                <p class="card-text">{{content}}</p>
                <p class="card-text"><strong>Tipologia:</strong> {{type}}</p>
                <p class="card-text" v-for="(element, index) in technologies" :key="element.id"><strong>Linguaggi/Framework:</strong> {{ element.name }}</p>
            </div>
        </div>
    </router-link>
</template>

<style>

</style>