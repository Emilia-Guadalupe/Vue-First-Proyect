<template>
    <Titulo texto="Ruta con parámetros" />
    <h3> {{articulo.title}} </h3>
    <p> {{articulo.id}} - {{articulo.body}} </p>
</template>

<script>
import Titulo from '../components/Titulo'
export default {
    components: {
        Titulo
    },
    data() {
        return {
            articulo: {}
        }
    },
    methods: {
        async consumirArticulo() {
            try {
                const data = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
                const objeto = await data.json()
                console.log(objeto)
                this.articulo = objeto
            } catch (error) {
                console.log('Hubo un error')
            }
        }
    },
    created(){
        this.consumirArticulo()
    }
}
</script>

<style>

</style>