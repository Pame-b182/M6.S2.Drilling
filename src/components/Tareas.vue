<template>
<div class="m-3 p-3 text-center">
    <h1> Lista de Tareas</h1>
    <div class="input-group m-3">
        <!-- v-model: permite capturar lo que el usuario escribe en el input -->
        <input v-model="tarea" type="text" class="form-control" placeholder="Ingrese Tarea" aria-label="Recipient's username" aria-describedby="button-addon2">
        <!-- @click: evento click que se gatilla al presionar el botón y ejecuta el método "agregarTarea" -->
        <button @click="agregarTarea" class="btn btn-outline-secondary" type="button" id="btnIngresar">Agregar</button>
    </div>
    <div>
        <!-- v-for: tarea -> esta tarea vive dentro de v-for, no corresponde al definido en "data" -->
        <ul v-for="(tarea, index) in tareas" :key="index">
            <!-- Evento click que se gatilla al presionar el boton eliminar y ejecuta el método "eliminar tarea", se puede utilizar index porque estamos dentro de v-for -->
            <li class="text-start">{{tarea}} 
                <button @click="eliminarTarea(index)" type="button" class="btn btn-danger btn-sm mx-3">Eliminar</button>
                <button @click="editarTarea(index)" type="button" class="btn btn-warning btn-sm">Editar</button>
            </li>
        </ul>
    </div>
</div>
</template>

<script>
export default {
    name: 'component-tareas',
    // props: {},
    data: function(){
        return {
            //Array vacío en donde se guardarán las tareas agregadas a través del input
            tareas: [],
            //Se declara la variable tarea como vacía, esta después cambiará con los inputs
            tarea:'',
        }
    },
    // computed: {},
    methods: {
        //Método que utiliza push() para agregar la tarea al array tareas.
        agregarTarea(){
            this.tareas.push(this.tarea),
            this.tarea=''
        },
        //Método que utiliza splice() para eliminar una tarea de acuerdo a su indice.
        //Tiene como argumento de entrada "index"
        eliminarTarea(index){
            this.tareas.splice(index, 1)
        },
        //Método que utiliza splice() para eliminar la tarea y al mismo tiempo agregar la nueva.
        editarTarea(index){
            //Se guarda en let la tarea editada y se edita a través de prompt
            let tareaEditada = prompt('Editar tarea', this.tareas[index])
            //Se elimina la tarea y se reemplaza por la tarea editada.
            this.tareas.splice(index, 1, tareaEditada)
        }
    }
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>

<style scoped>
    
</style>