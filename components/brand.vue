<template>
    <div class="brand">
        <a :href="brand.website" target="_blank">
            <b-img 
                fluid 
                :src="require('~/assets/images/brands/' + brand.image)" 
                :alt="'Brand image for ' + brand.name"```
                rounded="true"
                thumbnail
                width="500"
                center
            ></b-img>
        </a>

        <div class="brand__title">
            <b>Title:&nbsp;</b> <span>{{ brand.name }}</span>
        </div>

        <div>
            <b>Description:&nbsp;</b> <span>{{ brand.description }}</span>
        </div>

        <div>
            <b>Link:&nbsp;</b> <a :href="brand.website" target="_blank">Click here</a>
        </div>
        
        <b>GitHub repository:&nbsp;</b> <a :href="brand.repository" target="_blank">Click here</a>
    </div>
</template>

<script>
    import Brand from './models/Brand';

    export default {
        name: 'Brand',

        props: {
            brand: {
                type: Brand,
                required: true
            }
        }
    }
</script>

<style lang="scss" scoped>
    .brand {
        margin-bottom: 50px;
        background-color: #b9efff;
        opacity: 0.5;
        border-radius: 5px;
        padding: 30px;
        max-width: 350px;
        color: black;

        ul {
            list-style: none;
            padding: 0;
        }
    
        &__title {
            margin-top: 30px;
        }
    }
</style>