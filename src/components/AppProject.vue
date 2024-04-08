<script>

export default {
    name: 'AppProject',
    props: ['title', 'content', 'slug', 'type', 'technologies'],

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
        <div class="card my-5" style="width: 40rem;">
            <img class="card-img-top" src="" alt="Card image cap">
            <div class="card-body">
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