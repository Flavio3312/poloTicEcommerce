<template>
    <div class="page-success">
        <div class="columns is-multiline">
            <div class="column is-12">
                <h1 class="title">Gracias!</h1>

                <p>Su pedido será procesado dentro de las 48 horas.</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Success',
    mounted() {
        document.title = 'Exito | Jaguarete'
    },
}
</script>
© 2021 FEP