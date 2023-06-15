<template>
    <div class="container header-top">
        {{ title }}
    </div>
</template>

<script>

export default {
    name: 'ListHeader',
    data (){
        return {
            title: 'Todo list'
        }
    }
}

</script>

<style scoped>
    .header-top {
        top: 0;
        color: #61DAFB;
        background: #2D2D2D;
    }

</style>