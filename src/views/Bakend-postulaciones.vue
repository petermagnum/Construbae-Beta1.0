<template>
<div>
    <NavBakend/>
  <v-container>
    <br /><br /><br />
    <h1 class="my-5">Backend postulacioness</h1>
    <v-row class="justify-center pt-8 pb-8">
   
    </v-row>

    <table class="table">
      <thead>
        <tr>
          <th scope="col">Rut</th>
          <th scope="col">Nombre</th>
          <th scope="col">e-mail</th>
          <th scope="col">Acción</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in arrayFormularios" :key="item.id">
          <th scope="row">{{ item.rut }}</th>
          <td>{{ item.nombre }}</td>
          <td>{{ item.mail }}</td>
          <td>
            <router-link
              class="btn btn-warning ml-2 btn-sm"
              :to="{
                name: 'Info-postulaciones',
                params: {
                  rut: item.rut,
                },
              }"
            >
              Ver Info
            </router-link>
             <button
                class="btn btn-danger btn-sm ml-2"
                @click="Eliminar(item.rut)"
              >
                Eliminar
              </button>
          </td>
        </tr>
      </tbody>
    </table>
  </v-container>
  </div>
</template>

<script>
import NavBakend from "../components/Nav-bakend.vue";
export default {
  components: {
    NavBakend,
  },
  data() {
    return {
      arrayFormularios: [],
    };
  },
  computed: {},
  methods: {
    async cargarLocalStorage() {
    
      try {
        const res = await fetch(
          "https://webproyect-27e28-default-rtdb.firebaseio.com/formulario.json"
        );
        const dataDB = await res.json();

        for (let id in dataDB) {
          this.arrayFormularios.push(dataDB[id]);
        }
      } catch (error) {
        console.log(error);
      }
    },
    async Eliminar(id) {
      try {
        const res = await fetch(
          `https://webproyect-27e28-default-rtdb.firebaseio.com/cotizacion/${id}.json`,
          { method: "DELETE" }
        );
        const dataDB = await res.json();
        this.arrayFormularios = this.arrayFormularios.filter(
          (item) => item.rut !== id
        );
      } catch (error) {
        console.log(error);
      }
    },
  },
  created(){
    this.cargarLocalStorage();
  }
};
</script>
