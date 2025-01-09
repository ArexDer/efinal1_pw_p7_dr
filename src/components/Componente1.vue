

<template>
  <div class="container">
    <div class="formulario">
        <div class="foto">
            <p>Fotografia</p>
            <img :src="fotografiaD" alt="">
        </div>

        <div class="campos">

        <p>Titulo </p>
        <p class="dato">{{ tituloD }}</p>

        <p>Nombre</p>
        <p class="dato">{{ nombreD }}</p>

        <p>Apellido</p>
        <p class="dato">{{ apellidoD }}</p>

        <p>Email</p>
        <p class="dato">{{ emailD }}</p>

        <p>Pais</p>
        <p class="dato">{{ countryD }}</p>

        <div class="botonera">
         
        <button @click="buscarCandidato">Buscar</button>

        <button @click="agregarPersona">Agregar</button>

    </div>


    <!--ESTO LUEGO PASARLO AL COMPONENTE2-->

    
    </div>
    <table>
        <thead>
            <tr>
                <th>Titulo</th>
                <th>Nombre</th>
                <th>Apellido</th>
                <th>Email</th>
                <th>Pais</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>FF</td>
                <td>Juan</td>
                <td>Perez</td>
                <td>juan.perez@asdsa.com</td>
                <td>Argentina</td>
            </tr>
            <tr>
                <td>Sra.</td>
                <td>Maria</td>
                <td>Gomez</td>
                <td>maria.gomez@ssdf.com</td>
                <td>Chile</td>
            </tr>
        </tbody>
    </table>

    </div>
   
  </div>

</template>

<script>
export default {
    data(){
        return{
            tituloD: "",
            fotografiaD: "",
            nombreD:"",
            apellidoD:"",
            emailD:"",
            countryD:"",

        }
    },
    props:{
        
        persona:{
            type:Object,
            default:{
                titulo:"Fotografia ",
                fotografia:"Titulo e ",
                nombre:"Nombre ",
                apellido:"Apellido ",
                email:"email X ",
                country:"country Y "
            }
        },
        fotografia:{
            type:String,
            default:"Fotografia Candidato"
        },

        titulo:{
            type:String,
            default:"Titulo De candidato"
        },
        nombre:{
            type:String,
            default:"Nombre Candidato"
        },
        apellido:{
            type:String,
            default:"Apellido Candidato"
        },
        atributoX:{
            type:String,
            default:"Atributo X Cnadidato"
        },
        atributoY:{
            type:String,
            default:"Atributo Y Candidato"
        }
    },

    methods:{
       async buscarCandidato(){
        for (let index = 0; index < 1; index++) {
            const data = await fetch(`https://randomuser.me/api/`).then(response =>response.json());
            console.log("SE ENTRO AL METODO DE LA API");
            console.log(data);
            console.log(data.results[0].name.first);
            console.log(data.results[0].name.last);

            this.fotografiaD= data.results[0].picture.large;
            this.tituloD = data.results[0].name.title;
            this.nombreD= data.results[0].name.first;
            this.apellidoD= data.results[0].name.last;
            this.emailD= data.results[0].email;
            this.countryD= data.results[0].location.country;

        }
        },
        agregarPersona(){
            console.log("SE AGREGO UNA PERSONA");
            this.persona.titulo = this.tituloD;
            this.persona.fotografia = this.fotografiaD;
            this.persona.nombre = this.nombreD;
            this.persona.apellido = this.apellidoD;
            this.persona.email = this.emailD;
            this.persona.country = this.countryD;

        }
       

    }

}
</script>

<style>

.container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    height: 100vh;
    background-color: #f1f1f1;
}


.botonera{
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 20px;
    space-between: 20px;
}
.formulario{
    display: flex;
    flex-direction: column;
    padding: 10px;
    justify-content: left;
    align-content: left;

    border: 1px solid black;
}
.foto{
    display: grid;
    
}
.dato{
    background: white;
    border: 1px solid green;
}
button{
    background: green;
    color: white;
    border: none;
    padding: 10px;
    margin: 10px;
    cursor: pointer;
}





</style>