<script>
import { RouterLink } from 'vue-router';


export default {
    name: 'AppHeader',
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
    <nav class="navbar navbar-expand-lg bg-body-tertiary">
        <div class="container-fluid">
            <a class="navbar-brand fw-bold" href="#">PierFolio</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                    <li class="nav-item">
                        <router-link :to="{name:'home'}" class="nav-link">Home</router-link>
                    </li>
                    <li>
                        <router-link :to="{name:'projects'}" class="nav-link">Projects</router-link>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<style>

</style>