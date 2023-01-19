<script setup lang="ts">
import { computed, ref } from 'vue';
import translation from '../json/texts.json'; 

interface traduction {
    [key: string]: string
}

interface project {
    "title": traduction, 
    "description": traduction, 
    "partners": traduction,
    "tags": string[], 
    "tools": traduction, 
    "link": traduction, 
    "year": string,
    "img-mini": string, 
    "img-ban": string
}

const props = defineProps<{
    lang: string,
    infos: project
}>();

const text : any = translation;

// image
function getImgName() {
    return props.infos['img-ban'] ? props.infos['img-ban'] : "default.jpg";
}
const desc = computed(() => props.infos.description[props.lang] );

</script>

<template>
        <div class="one-project">
            <div class="infos">
                <img :src="`./img/banner/${getImgName()}`" />
                <h2>{{ infos.title[lang] }}</h2>
                <h3>{{ infos.year }} - {{ infos.partners[lang] }}</h3>
                <p id="desc" v-html="desc"></p>
                <p><span class="underline">{{ text['project-tools'][lang] }}</span> {{ infos.tools[lang] }} </p>
                <p><a target=”_blank” :href="infos.link.url" class="underline">{{ infos.link[lang] }}</a></p>
            </div>
        </div>
</template>

<style scoped>

.one-project {
    width: 80vw;
    height: 90vh;
    background-color: var(--white);
    position: absolute;
    top: 5vh;
    left: 10vw;
    transition: 0.4s ease-in-out;
    overflow-y: scroll;
    z-index: 10;
}

.infos {
    height: fit-content;
    padding: 0 35px 35px;
    color: var(--dark-green);
    position: relative;
}

.infos p {
    line-height: 1.6rem;
    margin-top: 10px;
}

h2 {
    text-shadow: var(--white) 1px 0 5px;
    position: relative;
    z-index: 10;
    text-align: right;
    font-weight: bold;
    line-height:10vw;
}

h3 {
    /* line-height: 1.6rem; */
    font-weight: 800;
    font-size: 1.6rem;
    text-align: right;
    position: relative;
}

.infos img {
    position: relative;
    top:55px;
    z-index: 0;
    width: 100%;
    height: 50vw;
    max-height: 70vh;
    object-fit: cover;
}

.underline {
    text-decoration: underline;
}

</style>

<style>
.synopsis {
    font-style: italic;
}

#desc p {
    margin-top: 10px;
}

</style>