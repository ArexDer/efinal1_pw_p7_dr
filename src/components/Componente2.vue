
<template>
  <div class="container">
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
                <td>Sr.</td>
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
</template>

<script>
import Componente1 from './Componente1.vue';
export default {
    components:{
        Componente1
    }

}
</script>

<style>

</style>