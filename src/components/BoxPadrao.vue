<template>
<div class="box has-text-weight-bold">
    <slot></slot>
</div>

</template>

<script>
export default{
    name: 'BoxPadrao',
}

</script>

<style scoped>  
.box {
    padding: 1.5rem;
    margin: 1.5rem;
    background: #FAF0CA;
}
</style>