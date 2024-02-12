<script lang="ts" setup>
import { ref } from 'vue'
import UserGrid from "../components/UserGrid.vue"

let genderFilter = ref("Alla");
</script>

<template>
    <select v-model="genderFilter">
        <option value="Alla">Alla</option>
        <option value="Kvinna">Kvinna</option>
        <option value="Man">Man</option>
        <option value="Katt">Katt</option>
        <option value="Övrigt">Övrigt</option>
    </select>

    <UserGrid :gender="genderFilter" />
</template>

<style scoped>

select {
    color: black;
}

</style>