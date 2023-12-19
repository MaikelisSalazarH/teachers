<template>
    <section>
        <h3>Añadir</h3>
        <div><label>Nombre:</label> <input type="text" v-model="teacher.teacherName" /></div>
        <div><label>Apellido:</label> <input type="text" v-model="teacher.lastname" /></div>
        <div><label>Rut:</label> <input type="text" v-model="teacher.rut"/></div>
        <div><label>Asignatuas:</label> <input type="text" v-model="suject"/> <button @click="handleSujects()">Agregar</button></div>
        <div>
            <ul>
                <li v-for="(item , index) in teacher.sujects" :key="index">{{ item }}</li>
            </ul>
        </div>
        <input type="checkbox" v-model="teacher.doc"/> Documentacion
        <button @click="handleAddTeacher">Agregar </button>
    </section>
        <h3>Listado</h3>
        <table>
            <tr>
                <th>Nombre</th>
                <th>Apellido</th>
                <th>Rut</th>
                <th>Asignaturas</th>
                <th>Documentacion</th>
            </tr>
            <tr v-for="item in teachers" :key="item.rut">
                <th>{{ item.teacherName }}</th>
                <th>{{ item.lastname }}</th>
                <th>{{ item.rut }}</th>
                <th>
                    <ul>
                        <li v-for="(elem, index) in item.sujects" :key="index">{{ elem }}</li>
                    </ul>
                </th>
                <th v-if="item.doc">Entregada</th>
                <th v-else>No entregada</th>
            </tr>
        </table>
    <section>

    </section>
</template>
  



  <script lang="ts" setup>
    import { Ref, ref } from 'vue'
 
    // Costruccion con TS 
    interface ITeacher{
        teacherName: string,
        lastname: string, 
        rut: string,
        sujects: Array<string>,
        doc: boolean
        }
      
 
    // Construccion con JS puro sin  :Ref<ITeacher>
    let teacher:Ref<ITeacher> = ref({
        teacherName: '',
        lastname: '', 
        rut: '',
        sujects: [ ],
        doc: false
    }) 

    // Guardar los datos de los profesores en un array *Con JS* let teachers = ref([]) con un array sin nada 
    let teachers:Ref<Array<ITeacher>> = ref([])
    
    let suject:Ref<string> = ref('')
    
    const handleSujects = () => {
        teacher.value.sujects.push(suject.value)
        suject.value = ""
    }

    const handleAddTeacher = () => {
        teachers.value.push({
            teacherName: teacher.value.teacherName,
            lastname: teacher.value.lastname ,
            rut: teacher.value.rut,
            sujects:  teacher.value.sujects , 
            doc:  teacher.value.doc, 
        })


    }

  </script>
  
  <style scoped>
  
  </style>