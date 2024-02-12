<template>
  <div class="form-container">
    <h1>Din profil</h1>

    <form @submit.prevent="submitForm">
      <label>
        <p v-if="showName">
          Namn
        </p>
        <input v-model="user.name" required placeholder="Namn" @focus="showName = true" @blur="showName = false">
      </label>

      <label>
        <p v-if="showBirthyear">
          Födelseår
        </p>
        <p>
          <input type="number" v-model="user.age" required placeholder="1985" @focus="showBirthyear = true" @blur="showBirthyear = false">
        </p>
      </label>

      <label>
        Kön:
        <select v-model="user.gender">
          <option value="male">Man</option>
          <option value="female">Kvinna</option>
          <option value="cat">Katt</option>
          <option value="other">Övrigt</option>
        </select>
      </label>

      <label>
        <p v-if="showLocation">
        Plats
      </p>
      <input v-model="user.location" required placeholder="Plats" @focus="showLocation = true" @blur="showLocation = false">
      </label>

      <label>
        <p v-if="showOccupation">
        Yrke
      </p>
      <input v-model="user.occupation" required placeholder="Yrke" @focus="showOccupation = true" @blur="showOccupation = false">
      </label>

      <button type="submit">Submit</button>
    </form>

    <div v-if="submitted">
      <h2>User Information:</h2>
      <p><strong>Name:</strong> {{ user.name }}</p>
      <p><strong>Age:</strong> {{ user.age }}</p>
      <p><strong>Gender:</strong> {{ user.gender }}</p>
      <p><strong>Location:</strong> {{ user.location }}</p>
      <p><strong>Occupation:</strong> {{ user.occupation }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showBirthyear: false,
      showName: false,
      showLocation: false,
      showOccupation: false,
      user: {
        name: '',
        age: 1985,
        gender: 'male',
        location: '',
        occupation: ''
      },
      submitted: false
    };
  },
  methods: {
    async submitForm() {
      let headersList = {
        "Accept": "*/*",
      }

      let bodyContent = new FormData();
      bodyContent.append("name", this.user.name);
      bodyContent.append("gender", this.user.gender);
      bodyContent.append("age", this.user.age);
      bodyContent.append("location", this.user.location);
      bodyContent.append("occupation", this.user.occupation);

      let response = await fetch("http://localhost:3030/users", {
        method: "POST",
        body: bodyContent,
        headers: headersList
      });

      let data = await response.text();
      console.log(data);
    }
  }
};
</script>

<style scoped>
.form-container {
  margin: 1.5rem;
  padding: 1.5rem;
  background-color: white;
  max-width: 60ch;
  border-radius: 8px;
}

label {
  display: block;
  margin: 1rem;
  padding: 1rem;
  color: black;
}

input {
  border: 0;
  border-bottom: 1px solid rgb(191, 191, 191);
}

input:focus {
  outline: none;
}

h1 {
  color: black;
}

button {
  background-color: rgba(216, 225, 243, 0.489);
  border-radius: 8px;
  border-style: hidden;
}

button:hover {
  background-color: rgba(245, 245, 255, 0.657);
}
</style>