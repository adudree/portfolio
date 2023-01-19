<script setup lang="ts">
import texts from "@/json/texts.json"; 

const props = defineProps<{
    lang: string
}>();

const text : any = texts;

function getPdfUrl() {
    return new URL(`/docs/audrey-martin-cv-fr.pdf`, import.meta.url).href
}

</script>

<template>
    <div class="home-container">
        <div class="home-content">
            <img src="/img/profil.jpg" />
            <div class ="text">
                <h1>Audrey Martin</h1>
                <p>{{ text["home-description"][lang] }}</p>
                <a :href="getPdfUrl()" target="_blank">
                    <p class="button">{{ text["home-cv-btn"][lang] }}</p>
                </a>
            </div>
        </div>
    </div>
</template>

<style scoped>

h1 {
    text-shadow: var(--dark-grey) 1px 0 5px;
}

.home-container {
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.home-content {
    display: flex;
    width: 70vw;
    height: 40vh;
    padding: 30px;
}
.home-content img {
    width: 350px;
    height: 350px;
    object-fit:cover;
    border-radius: 50%;
    margin-right: 30px;
    z-index: -1;
}

.text {
    margin-bottom: 50px;
}
.home-content .text {
    height: auto;
    text-align: justify;
    padding-left: 40px;
}
.text p {
    min-width: 30vw; 
    max-width: 40vw;
    margin: auto;
}

.text .button {
    background-color: var(--color-important);
    color: var(--white);
    min-width:fit-content;
    max-width: fit-content;
    text-align: center;
    padding: 5px 15px;
    border-radius: 15px;
    margin: 30px 0;
    transition: 0.3s ease-in-out;
}

.button:hover {
    background-color: var(--darker-pink);
}

@media screen and (max-width: 1400px) {
    .home-content {
        padding:0;
        width: 90%;
        height: fit-content;
    }


    .home-content .text {
        padding-left: 0;
        height: fit-content;
    }

    .text p {
        margin: 0;
        max-width: fit-content;
        width: auto;
    }
}

@media screen and (max-width: 1140px) {
    .home-container {
        justify-content: flex-start;
    }
    .home-content {
        flex-direction: column;
        width: 70vw;
    }
    h1 {
        font-size: 9vw;
        text-shadow: var(--dark-grey) 1px 0 5px;
    }

    .home-content img {
        position: relative; 
        margin: 0;
        top:50px;
        width: 70vw;
        height: 35vw;
        object-fit:cover;
        object-position: center 30%;
        border-radius: 0;
        z-index: -1;
    }

}
</style>
