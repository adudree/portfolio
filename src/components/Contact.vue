<script setup lang="ts">
import texts from "@/json/texts.json"; 

const props = defineProps<{
    lang: string
}>();

const text : any = texts;

</script>

<template>
    <div class="cartel">
        <div class="texts">

            <h2>{{ text["contact-title"][lang] }}</h2>
            <div class="infos-container">
                <div>
                    <img class="icon" src="https://svgsilh.com/svg/2098873.svg">
                    <p>Audrey Martin</p>
                </div>
                <div>
                    <img class="icon" src="https://svgsilh.com/svg/309739.svg">
                    <p>Toulouse (31)</p>
                </div>
                <div>
                    <img class="icon" src="https://www.svgrepo.com/show/2784/mail.svg">
                    <a href="mailto:contact@audrey-martin.fr"><p>contact@audrey-martin.fr</p></a>
                </div>
            </div>
            <div class="icons">
                <a target="_blank" href="https://www.linkedin.com/in/audrey-martin-b64952175/">
                    <img class="icon" src="@/assets/svg/linkedin.svg">
                </a>
                <a target="_blank" href="https://github.com/adudree">
                <img class="icon" src="https://upload.wikimedia.org/wikipedia/commons/9/91/Octicons-mark-github.svg">
                </a>
            </div>
        </div>
        <img src="@/assets/svg/contact.svg" class="img"/>
    </div>
</template>

<style scoped>
.cartel {
    background-color: var(--white);
    width: 70vw;
    margin: auto;
    height: 45vw;
    display: flex;
    justify-content: space-between;
    max-width: 1050px;
    max-height: 675px;
    padding: 20px;
}

.texts {
    padding: 40px 20px;
    display: flex;
    flex-flow: column;
    justify-content: space-between;
}

.infos-container {
    display: flex;
    flex-direction: column;
    height: 60%;
    justify-content: space-evenly;
    padding-left: 10px;
}
.infos-container * {
    display: flex;
    align-items: center;
    padding-right: 15px;
}

h2 {
    color: var(--color-important);
    font-size: 4rem;
}

p {
    color: var(--dark-green);
    font-size: 1.8rem;
}
.icon {
    width: 50px;
    height: 50px;
    margin: 10px;
}
.img {
    width: 50%;
}

@media screen and (max-width: 1440px) {
    .img {
        display: none;
    }
    .cartel {
        text-align: center;
        height: auto;
        max-height: none;
    }
    .texts {
        margin: auto;
    }
    .infos-container {
        margin: 20px 0;
        font-size: 1rem;
    }
}

@media screen and (max-width: 720px) {
    .cartel {
        margin-bottom: 50px;
    }
    .infos-container div {
        flex-direction: column;
        margin-top: 20px;
    }

    .infos-container * {
        padding-right: 0;
    }

    h2 {
        font-size: 2.5rem;
    }
    p {
        font-size: 1.3rem;
    }
}
</style>
