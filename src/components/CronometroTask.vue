<script>
export default {
    name: 'CronometroTask',
    props: {
        tempoEmSegundos: {
            type: Number,
            required: true,
            default: 0,
        },
    },
    computed: {
        tempoDecorrido() {
            return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11, 8);
        }
    },
}
</script>

<template>
    <section>
        <strong>{{ tempoDecorrido }}</strong>
    </section>
</template>