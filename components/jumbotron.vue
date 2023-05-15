<template>
    <div class="jumbotron">
        <h1 class="jumbotron__heading slide-in-from-left">
            Hey! I'm Eduardo, a
            <strong class="gradient-text">full stack web developer</strong>.<br/>
            I use a VERY meticolous approach and the latest best practices in software engineering to create fast, accessible and intuitive web apps.<br/>
            My fortes are, undoubtedly, debugging and reverse engineering.
        </h1>

        <b-button
            @click="scrollToElement('about')"
            class="jumbotron__cta mail-button scale-on-hover"
            pill
            variant="primary"
        >Learn more</b-button>
    </div>
</template>

<script>
    export default {
        methods: {
            /**
             * Scrolls to the element of the given ID.
             * @param {string} id - The ID (HTML) of the element to scroll to.
            */
            scrollToElement(id) {
                if (document.querySelector(`#${id}`)) {
                    document.querySelector(`#${id}`).scrollIntoView({
                        behavior: "smooth",
                        block: "start",
                    });
                }
            }
        }
    }
</script>

<style lang="scss" scoped>
    .jumbotron {
        min-height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        font-weight: 600;
        background: transparent;

        &__heading {
            &,
            strong {
                font-size: 40px;
                color: white;
                z-index: 10000000;
            }
            
            @media screen and (max-width: 768px) {
                &,
                strong {
                    font-size: 30px;
                }
            }
        }

        &__cta {
            margin-top: 50px;
        }
    }
</style>