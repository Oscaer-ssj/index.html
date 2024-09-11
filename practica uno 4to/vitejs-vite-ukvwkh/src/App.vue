<script lang="ts">
import { defineComponent, ref } from 'vue'
import inputphone from './components/inputphone.vue';

export default defineComponent({
  setup() {
    return {
      name: ref(""),
      errorName: ref(false),
      lastName: ref(""),
      errorLastName: ref(false),
      year: ref(""),
      errorYear: ref(false),
      phone: ("8714351456"),
      errorPhone: ref(false),
      address: ref(""),
      errorAddress: ref(false),
      email: ref(""),
      errorEmail: ref(false),
      users: ref([])
    }
  },
  methods: {
    validateData() {
      let isValid = true

      if (this.name === "") {
        isValid = false
        this.errorName = true
      }

      if (this.lastName === "") {
        isValid = false
        this.errorLastName = true
      }

      if (this.year === "") {
        isValid = false
        this.errorYear = true
      }

      if (this.phone === "") {
        isValid = false
        this.errorPhone = true
      }

      if (this.address === "") {
        isValid = false
        this.errorAddress = true
      }

      if (this.email === "") {
        isValid = false
        this.errorEmail = true
      }

      return isValid
    },
    register() {
      const isValid = this.validateData()

      if (isValid) {
        console.log(this.name, this.lastName, this.year, this.phone, this.address, this.email)
        console.log("Registrado")
        this.users.push({
          name: this.name,
          lastName: this.lastName,
          year: this.year,
          phone: this.phone,
          address: this.address,
          email: this.email
        })
        this.clear()
        console.log(this.users)
      }
    },
    clear() {
      this.name = ""
      this.errorName = false
      this.lastName = ""
      this.errorLastName = false
      this.year = ""
      this.errorYear = false
      this.phone = ""
      this.errorPhone = false
      this.address = ""
      this.errorAddress = false
      this.email = ""
      this.errorEmail = false
    }
  }
})
</script>


<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <div class="card">
          <div class="card-body">
            <h3 class="card-title">Registrarse</h3>
            <hr class="hr">
            <label for="name">Nombre</label>
            <input type="text" class="form-control" v-model="name">
            <span v-if="errorName" class="text-danger">campo necesario</span>
            <label for="lastName">Apellidos</label>
            <input type="text" class="form-control" v-model="lastName">
            <span v-if="errorLastName" class="text-danger">campo necesario</span>
            <label for="year">Fecha de nacimiento</label>
            <input type="text" class="form-control" v-model="year">
            <span v-if="errorYear" class="text-danger">campo necesario</span>
            <label for="phone">Teléfono</label>
           <input type="text" class="form-control" v-model="phone">
            <span v-if="errorPhone" class="text-danger">campo necesario</span>
            <label for="address">Dirección</label>
            <input type="text" class="form-control" v-model="address">
            <span v-if="errorAddress" class="text-danger">campo necesario</span>
            <label for="email">Correo electronico</label>
            <input type="text" class="form-control" v-model="email">
            <span v-if="errorEmail" class="text-danger">campo necesario</span>
            <hr class="hr">
            <button type="button" class="btn btn-primary" @click="register">Registrar usuario</button>
          </div>
        </div>
      </div>
      <div class="col">
        <h3>Lista de usuarios</h3>
        <table>
          <thead>
            <tr>
              <th>Nombre</th>
              <th>Apellidos</th>
              <th>Fecha de nacimiento</th>
              <th>Teléfono</th>
              <th>Dirección</th>
              <th>Correo electronico</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="user in users" :key="user">
              <td>{{ user.name }}</td>
              <td>{{ user.lastName }}</td>
              <td>{{ user.year }}</td>
              <td>{{ user.phone }}</td>
              <td>{{ user.address }}</td>
              <td>{{ user.email }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<style >
.container {
  width: 100%;
  margin-bottom:  10px ;
  padding: 10px;

}
.card {
  padding: 10px;
  border: 1px solid #51ff00;
  border-radius: 10px;
  margin-bottom: 10px;

}
.text-danger {
  color: red;
}
.card-body {
  padding: 2rex;
  margin-bottom: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.card-title {
  margin-bottom: 10px;
}
.hr {
  margin-top: 10px;
  margin-bottom: 10px;
}
button{
  background-color: #43ce02; 
  color: white; 
  padding: 10px 20px;
  border: 1px solid #43ce02;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.30s ease; 
  
}

button:hover {
  background-color: transparent; 
}

th {
  padding: 10px;
  text-align: center;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  transition: background-color 0.30s ease;
  transition: color 0.30s ease;
}

th:hover {
  background-color: #f5f5f5;
  color:rgb(0, 0, 0)

}
td {
  margin-bottom: 10px;
  border: 1px solid #ccc;
  transition: color 0.30s ease;
 transition: background-color 0.30s ease;
}
td:hover{
  background-color: white;
  color:rgb(0, 0, 0)
 

}
</style>