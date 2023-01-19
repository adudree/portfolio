<script setup lang="ts">
import { ref } from 'vue';

interface traduction {
    [key: string]: string
}

const props = defineProps<{
    id: number, 
    title: traduction, 
    miniature?: string,
    lang: string
}>();

const emit = defineEmits<{
  (e: 'openProject', id: number): void
}>();

function selectProject() {
    emit('openProject', props.id); 
}

function getImgName() {
    return props.miniature ? props.miniature : "default.png";
}

</script>

<template>
    <div class="miniature" @click="selectProject">
    <img :src="`./img/mini/${getImgName()}`" /> 
    <div class="infos">
        <p>
            {{ title[lang] }}
        </p>
    </div>   
    </div>
</template>

<style scoped>
.miniature {
    width: 20vw; 
    height: 20vw; 
    margin: 10px;
    padding: 0;
    position: relative;
}

.infos {
    color: rgba(0,0,0,0); 
    background-color: rgba(200,200,200,0); 
    width:100%;
    height: 100%;
    z-index: 10;
    transition: 0.3s;
}

.infos p {
    padding: 15px;
    font-size: 2rem;
}

.miniature:hover .infos {
    color: var(--color-text); 
    background-color: var(--transparent-pink) ; 
    cursor: pointer;
}
.miniature img {
    position: absolute;
    z-index: -1;
    width: 100%;
    height: 100%;
    object-fit: cover;
    
}

@media screen and (max-width: 1600px) {
    .miniature {
        width: 25vw; 
        height: 25vw;
    }
}

@media screen and (max-width: 1000px) {
    .miniature {
        width: 35vw; 
        height: 35vw;
    }
}
@media screen and (max-width: 760px) {
    .miniature {
        width: 70vw; 
        height: 70vw;
    }
}
</style>
