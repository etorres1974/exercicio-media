<template>
  <v-form>
    <v-container>
        <v-row>
            <v-col> 
                <v-text-field v-model="pessoa.idade1" label="idade1"/>
            </v-col>
            <v-col>
                <v-text-field  v-model="pessoa.idade2" label="idade2"/>
            </v-col>
            <v-col>
                <v-btn @click="calcular">Calc</v-btn>
                {{resultado}}
            </v-col>
        </v-row>
    </v-container>
  </v-form>
</template>
<script>
import axios from "axios"
export default {
    data(){
        return{
            pessoa: {},
            resultado: ""
        }
    },
    methods:{
        calcular(){
            axios.post("http://localhost:3000/media", this.pessoa).then( (response) =>{
                this.resultado = response.data.media
            }).catch(error => {
                window.alert(error)
            })
        }
        
    },
    
}
</script>