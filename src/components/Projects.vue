<script setup lang="ts">
import ProjectMiniature from './ProjectMiniature.vue';
import ProjectInfos from './ProjectInfos.vue';
import { ref } from 'vue';
import allProjects from '../json/projects.json';

const props = defineProps<{
    lang: string
}>();

const isClosed = ref<boolean>(true); 
const selectedProject = ref<number>(0);
function onOpenProject(idProject: number) {
    selectedProject.value = idProject;
    isClosed.value = false;
}

const divProject= ref(null)


function close() {
    if (isClosed.value === false) isClosed.value = true;
}
</script>

<template>
    <div class="projects-list">
        <ProjectMiniature v-for="(item, key) in allProjects" 
        :id="key" 
        :title="allProjects[key].title" 
        :miniature="allProjects[key]['img-mini']" 
        :lang="lang" 
        @open-project="onOpenProject"
        />
    </div>
        <ProjectInfos 
        ref="divProject" 
        :class="{closed: isClosed}"
        :lang="lang" 
        :infos="allProjects[selectedProject]"
        />
        <div :class="{container: !isClosed}" @click="close">
    </div>
</template>

<style scoped>

.projects-list {
    display: flex;
    flex-flow: wrap;
    padding: 0;
    overflow-y: scroll;
    max-width: 85vw;
    margin: auto;
    padding-bottom: 50px;
}

.container {
    position: absolute;
    z-index: 1;
    width: 100vw; 
    height: 100vh;
    transition: 0.5s ease-in-out;
    background: var(--transparent-grey);
}

.closed {
    left:-100vw;
}

@media screen and (max-width: 760px) {
    .projects-list {
        max-width: min-content;
    }

}

</style>
