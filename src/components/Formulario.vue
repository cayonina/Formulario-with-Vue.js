<template>
  <div class="container">
    <form>
      <div class="row">
        <div class="col-xs12 col-sm-8 col-md-6">
          <h1>Formulario de Contacto</h1>
          <hr>
          <div class="form-group">
            <label for="nombre">Nombre:</label>
            <input type="text" class="form-control" id="nombre" v-model="datosPersona.nombre">
          </div>
          <div class="form-group">
            <label for="email">E-mail:</label>
            <input type="text" class="form-control" id="email" v-model="datosPersona.email">
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-xs12 col-sm-8 col-md-6">
           <label for="mensaje">Mensaje</label><br>
           <textarea id="mensaje" cols="60" rows="5" v-model="mensaje"></textarea>
        </div>
      </div>
 

    <div class="row">
      <div class="col-xs12 col-sm-8 col-md-6">
          <div class="form-group">
            <label for="enviaremail">
              <input type="checkbox" id="enviaremail" value="enviar email" v-model="opcionMail">Enviar E-mail
            </label>&nbsp;&nbsp;
            <label for="enviarcopia">
              <input type="checkbox" id="enviarcopia" value="enviar copia" v-model="opcionMail">Enviar una copia
            </label>
          </div>
      </div>
    </div>
  
    <div class="row">
      <div class="col-xs12 col-sm-8 col-md-6">
          <div class="form-group">
            <label for="masculino">
              <input type="radio" id="masculino" value="Masculino" v-model="genero">Masculino
            </label>&nbsp;&nbsp;
            <label for="femenino">
              <input type="radio" id="femenino" value="Femenino" v-model="genero">Femenino
            </label>
          </div>
      </div>
    </div>

     <div class="row">
      <div class="col-xs12 col-sm-8 col-md-6">
            <label for="horario">Horario</label>
            <select id="horario" class="form-control" v-model="horario">
              <option v-for="item in datosHorario" :key="item" :selected="item== 'Mañana'">{{ item }}</option>
            </select>
      </div>
    </div>

    <div class="row">
      <div class="col-xs12 col-sm-8 col-md-6"><br>
      <!-- el .prevent es para que no refresque la pagina -->
        <button class="btn btn-primary" @click.prevent="enviar">Enviar Datos</button>
      </div>
    </div>
 </form>
    <div class="row" v-if="enviado">
      <div class="col-xs12 col-sm-8 col-md-6">
        <div class="panel panel-default">
          <div class="panel-heading">
            <h3>Datos Ingresados</h3>
          </div>
          <div class="panel-body">
            <p>Nombre: {{ datosPersona.nombre }}</p>
            <p>Email: {{ datosPersona.email }}</p>
            <p style="white-space:pre">Mensaje:<br> {{ mensaje }}</p>
            <p>Opcion de envio:
              <ul>
                <li v-for="item in opcionMail" :key="item"> {{ item }}</li>
              </ul>
            </p>
            <p>Genero: {{genero}}</p>
            <p>Horario: {{horario}}</p>
          </div>
        </div>

      </div>
    </div>
  </div>
    
</template>

<script>
export default {
  name: 'Formulario',
  data(){
    return{
      datosPersona:{
        nombre: '',
        email: ''
      },
      mensaje:'Test Mensaje',
      opcionMail:[],
      genero:'',
      horario:'Mañana',
      datosHorario:['Mañana','Tarde','Noche'],
      enviado: false
    }
  },
  methods:{
    enviar(){
      this.enviado=true;
    }
  }
  
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
