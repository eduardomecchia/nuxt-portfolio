<template>
    <div class="jumbotron">
        <h1 class="jumbotron__heading slide-in-from-left">
            Hey! I'm Eduardo, a
            <strong class="gradient-text">full stack web developer</strong>.<br/>
            The website is a WiP, I will be adding my projects and more sections soon!
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
         * Scrolls to the element of the given ID
         * @param {string} id - The ID (HTML) of the element to scroll to
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
        height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        font-weight: 600;

        &__heading {
            font-size: 50px;
            text-align: center;

            @media screen and (max-width: 768px) {
                & {
                    font-size: 35px;
                }
            }
        }

        &__cta {
            margin-top: 50px;
        }
    }
</style>