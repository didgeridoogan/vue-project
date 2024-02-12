<template>
    <div class="user-grid">
        <div v-for="(user, index) in users" :key="index">
            <UserCard class="the-card" v-if="user.gender == props.gender || props.gender == 'Alla'" :name="user.name"
                :age="user.age" :gender="user.gender" :location="user.location" :occupation="user.occupation"
                :img_path="user.img_path" />
            <div v-if="user.gender === props.gender || props.gender === 'Alla'">
                <button>Gilla</button>
                <button>Skicka meddelande</button>
                <button>Blocka</button>
            </div>
        </div>
    </div>
</template>
  
<script setup lang="ts">
import { ref, onBeforeMount } from 'vue';
import UserCard from './UserCard.vue';

const props = defineProps(["gender"]);

onBeforeMount(async () => {
    let response = await fetch("http://localhost:3030/users");
    users.value = await response.json();
});

let users = ref([
    {
        name: "Gappy",
        age: 19,
        gender: "Man",
        location: "N/A",
        occupation: "Sailor",
        img_path: "/src/assets/gappy.jpeg"
    },
]);
</script>
  
<style scoped>
.user-grid {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
}

.the-card {
    margin: 1rem;
}

button {
    color: black;
    background-color: white;
    padding: 1vh;
    border-radius: 1vh;
    box-shadow: 2px 2px 4px rgb(74, 74, 74, 0.5);
    border-color: gray;
    border-style: hidden;
}

button:hover {
  background-color: rgba(245, 245, 255, 0.657);
}

</style>
  