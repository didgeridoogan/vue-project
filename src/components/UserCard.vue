<script lang="ts" setup>
import { ref } from 'vue';

const props = defineProps(["name", "age", "gender", "location", "occupation", "img_path"]);

</script>

<template>
    <div class="user-card">
        <div class="avatar-panel">
            <img :src="img_path" :alt="img_path" width="120" />
        </div>
        <div class="user-facts-panel">
            <ul>
                <li>Namn: <span>{{ name }}</span> </li>
                <li>Födelseår: <span>{{ age }}</span> </li>
                <li>Kön: <span>{{ gender }}</span> </li>
                <li>Plats: <span>{{ location }}</span></li>
                <li>Yrke: <span>{{ occupation }}</span> </li>
            </ul>
        </div>
    </div>
</template>

<style scoped>
.user-card {
    display: grid;
    grid-auto-flow: column;
    background-color: rgb(255, 255, 255);
    color: black;
    padding: 1rem;
    border-radius: 8px;
    box-shadow: 4px 4px 8px rgb(74, 74, 74, 0.5);
    width: 100%;
    max-width: 250px;
    height: 300px;
    align-items: center;
}

.user-facts-panel ul {
    list-style: none;
}

li {
    font-weight: bolder;
}
</style>