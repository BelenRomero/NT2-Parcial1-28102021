<template>

    <section class="src-componentes-ingreso">
    <div class="jumbotron">
      <h2>Ingreso de Gastos</h2>
      <hr>

      <vue-form :state="formstate" @submit.prevent="enviar()">
        
        <!-- Campo nombre -->
        <validate tag="div">
          <label for="nombre">Nombre</label>
          <input type="text" id="nombre" v-model="formData.nombre" required name="nombre" autocomplete="off" class="form-control" />
  
          <field-messages name="nombre" show="$dirty">
            <div slot="required" class="alert alert-danger mt-1">Este campo es obligatorio</div>
          </field-messages>
        </validate>
        <br>





        <!-- Campo descripcion -->
        <validate tag="div">
          <label for="descripcion">Descripcion</label>
          <input type="text" id="descripcion" v-model="formData.descripcion" required name="descripcion" autocomplete="off" class="form-control" />
    
          <field-messages name="descripcion" show="$dirty">
            <div slot="required" class="alert alert-danger mt-1">Este campo es obligatorio</div>
          </field-messages>
        </validate>
        <br>
        
        <!-- Campo importe -->
        <validate tag="div">
          <label for="importe">Importe</label>
          <input type="number" id="importe" v-model.number="formData.importe" required name="importe" autocomplete="off" class="form-control" />
    
          <field-messages name="importe" show="$dirty">
            <div slot="required" class="alert alert-danger mt-1">Este campo es obligatorio</div>
          </field-messages>
        </validate>
        <br>

      <button class="btn btn-success my-3" :disabled="formstate.$invalid" type="submit">Enviar</button>  
      </vue-form>
      <br>
      <hr>

      <!-- Tabla para representar los datos ingresados -->
      <h2>Detalle de Gastos</h2>
      <br>

      <!-- <pre>{{ gastos }}</pre> -->

      <div v-if="gastos.length" class="table-responsive">
        <table class="table">
          <tr>
            <th>Nombre</th>
            <th>Descripcion</th>
            <th>Importe</th>
            <th>Fecha</th>
            <th>Total</th>
          </tr>
          <tr v-for="(gasto,index) in gastos" :key="index" :style="{color: analizarSaldo(gasto).color }">
            <td>{{ gasto.nombre }}</td>
            <td>{{ gasto.descripcion }}</td>
            <td>{{ gasto.importe }}</td>
            <td>{{ gasto.fecha }}</td>
            <td>{{ analizarSaldo(gasto).valor }}</td>
          </tr>
        </table>
      </div>
      <h3 v-else class="alert alert-info">No hay gastos ingresados</h3>

    </div>
  </section>

</template>


<script>
  export default  {
    name: 'src-componentes-ingreso',
    props: [],
    mounted () {

    },
    data () {
      return {
        formstate : {},
        formData : this.getInitialData(),
        gastos : []
      }
    },
    methods: {
      getInitialData() {
        return {
          nombre : null,
          descripcion: null,
          importe: null,
        }
      },
      enviar() {
        let gasto = {...this.formData}
        gasto.fecha = new Date().toLocaleString()

        console.log(gasto)
        this.gastos.push(gasto)

        this.formData = this.getInitialData()
        this.formstate._reset()

      },
      analizarSaldo(gasto) {
        let tot = gasto.importe
        let color = '#064'
        if(tot > 1000 && tot <= 5000)
          color = '#040'
        if(tot > 5000) 
          color = '#031'
        return {
          valor : tot,
          color
        }
      }
    },
    computed: {
    }
}

</script>


<style scoped lang="css">
  .scr-componentes-ingreso {

  }


  .jumbotron {
    background-color: lightgray;
    color: black;
  }

</style>
