<template>
    <header>
        <h2>{{ text }}</h2>
    
        <Divider />
    </header>
</template>

<script>
    export default {
        props: {
            text: {
                type: String,
                required: true
            }
        }
    }
</script>

<style lang="scss" scoped>
    header {
        margin-bottom: 50px;
        
        h2 {
            text-align: center;
            font-weight: bold;
            font-size: 40px;
        }
    }
</style>