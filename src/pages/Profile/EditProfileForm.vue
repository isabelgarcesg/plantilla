<!-- eslint-disable vue/no-mutating-props -->
<template>
  <card v-on:submit.prevent="agregarRegistro">
    <h5 slot="header" class="title">Crear Usuario</h5>
    <div class="row">
      <!-- <div class="col-md-5 pr-md-1"> -->
        <!-- <base-input
          label="Company (disabled)"
          placeholder="Company"
          v-model="model.company"
          disabled
        >
        </base-input> -->
      <!-- </div>"col-md-3 px-md-1" -->
      <div class="col-md-6 pr-md-1">
        <base-input
          label="Nombre Completo"
          placeholder="Nombre Completo"
          v-model="model.username"
        >
        </base-input>
      </div>
      <div class="col-md-6 pl-md-1">
        <base-input
          label="Documento identidad"
          placeholder="ID"
        >
        </base-input>
      </div>
    </div>
    <div class="row">
      <div class="col-md-6 pr-md-1">
        <base-input
          label="Teléfono"
          v-model="model.firstName"
          placeholder="Teléfono"
        >
        </base-input>
      </div>
      <div class="col-md-6 pl-md-1">
        <base-input
          label="Contraseña"
          type="password"
          v-model="model.lastName"
          placeholder=" "
        >
        </base-input>
      </div>
    </div>
    <div class="row">
      <div class="col-md-12">
        <base-input
          label="Position"
          v-model="model.address"
          placeholder="Position"
        >
        </base-input>
      </div>
    </div>
    <!-- <div class="row">
      <div class="col-md-4 pr-md-1">
        <base-input label="City" v-model="model.city" placeholder="City">
        </base-input>
      </div>
      <div class="col-md-4 px-md-1">
        <base-input
          label="Country"
          v-model="model.country"
          placeholder="Country"
        >
        </base-input>
      </div>
      <div class="col-md-4 pl-md-1">
        <base-input label="Postal Code" placeholder="ZIP Code"> </base-input>
      </div>
    </div> -->
    <!-- <div class="row">
      <div class="col-md-8">
        <base-input>
          <label>About Me</label>
          <textarea
            rows="4"
            cols="80"
            class="form-control"
            placeholder="Here can be your description"
            v-model="model.about"
          >
          </textarea>
        </base-input>
      </div> -->
    <!-- </div> -->
    <base-button slot="footer" type="submit" fill>Guardar</base-button>
  </card>
</template>
<script>
export default {
  props: {
    model: {
      type: Object,
      default: () => {
        return {};
      }
    }
  },
  data(){
        return{
            paciente:{}
        }
    },
    methods:{
        agregarRegistro(){
            console.log(this.paciente)//
            let datosEnviar={doc:this.paciente.doc, name:this.paciente.name, lastname:this.paciente.lastname} //como lo llamé en el campo se lo asigno a la instancia, es un arreglo json, clave valor
           //'http://localhost/api/?insertar=1'
            fetch('http://localhost/api/?insertar=1', {
                method:"POST", //usa el metodo post en la URL dada y decodifique el json
                body:JSON.stringify(datosEnviar)
            }) //es la URL, la saco de POSTMAN
            //se usan los varbos pata insertar (post)
            .then(respuesta=>respuesta.json) //promesa o respuesta
            .then((datosRespuesta=>{
                console.log(datosRespuesta)
                window.location.href='listar'//Redirecciona a la URL de listar
            }))
        }
    }
};
</script>
<style></style>
