<template>
    <footer>
        <div>&copy;2022 Eduardo Mecchia</div>
    
        <div>
            <span>Built using Nuxt.js</span>
    
            <a href="https://nuxtjs.org/" target="_blank">
                <img src="nuxt.ico" alt="Icon of Nuxt.js framework" width="25" height="25">
            </a>

            <!-- Second instance of social media component -->
            <ul>
                <li>ROW OF SOCIAL MEDIA ICONS</li>
            </ul>
        </div>
    </footer>
</template>

<style lang="scss" scoped>
    footer {
        width: 100%;
        color: white;
        background: #2ca2d8;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        padding-top: 30px;
        padding-bottom: 30px;
    }
</style>
