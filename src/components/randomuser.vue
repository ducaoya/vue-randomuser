<template>
    <div>
        <img :src="picture" :alt="`${firstName}${lastName}`" :class="gender">
        <h3>{{firstName}} {{lastName}}</h3>
        <h3>Email: {{email}}</h3>
        <h3>phone: {{phone}}</h3>
        <h3>age: {{age}}</h3>
        <h3>location: {{location}}</h3>
        <button :class="gender" @click="getUser()">Random User</button>
    </div>
</template>

<script>
export default {
    name:'RandomUser',
    data(){
    return {
      firstName: 'John',
      lastName: 'Doe',
      email: 'john@gmail.com',
      phone: '0000-1234567',
      age: '28',
      location: 'Germany Saarland Olfen Beethovenstraße 8496',
      gender: 'male',
      picture: 'https://randomuser.me/api/portraits/men/10.jpg',
      }
    },
    methods:{
        async getUser(){
            const res = await fetch("https://randomuser.me/api")
            const {results} = await res.json()
            
            this.firstName=results[0].name.first
            this.lastName=results[0].name.lastName
            this.email=results[0].email
            this.phone=results[0].phone
            this.age=results[0].dob.age
            this.location=results[0].location.country+'-'+results[0].location.state+'-'+results[0].location.city+'-'+results[0].location.street.name+'-'+results[0].location.street.number
            this.gender=results[0].gender
            this.picture=results[0].picture.large
        }
    }
}
</script>

<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html,
body {
  font-family: Arial, Helvetica, sans-serif;
}

#app {
  width: 400px;
  height: 100vh;
  margin: auto;
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

h1,
h3 {
  margin-bottom: 1rem;
  font-weight: normal;
}

img {
  border-radius: 50%;
  border: 5px #333 solid;
  margin-bottom: 1rem;
}

.male {
  border-color: steelblue;
  background-color: steelblue;
}

.female {
  border-color: pink;
  background-color: pink;
  color: #333;
}

button {
  cursor: pointer;
  display: inline-block;
  background: #333;
  color: white;
  font-size: 18px;
  border: 0;
  padding: 1rem 1.5rem;
}

button:focus {
  outline: none;
}

button:hover {
  transform: scale(0.98);
}

</style>
