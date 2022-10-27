<template>
    <!-- App wrapper -->
    <div class="app-wrapper">
        <!-- Content -->
        <main class="home">
            <Jumbotron />

            <About />

            <!-- Contact section -->
            <section class="home__section" id="contact">
                <Heading text="Contact me"></Heading>

                <div class="home__section__content contact__content">
                    <p>
                        Feel free to send me an e-mail regarding everything from business
                        enquiries to feedback about my portfolio site. I will also consider freelance opportunities!
                    </p>

                    <b-button
                        class="home__cta mail-button scale-on-hover"
                        pill
                        variant="primary"
                        href="mailto:eduardo.mecchia.dev@gmail.com"
                    >Send Mail</b-button>

                    <!-- <ul class="social-media">
                        <li>You can also reach me through social media!</li>
                        
                        // First instance of social media component
                        <li class="social-media-icon">LOOP THROUGH SOCIAL MEDIAS</li>
                    </ul> -->
                </div>
            </section>

            <!-- Projects section -->
            <section class="home__section" id="projects">
                <Heading text="Projects"></Heading>

                <div class="home__section__content projects__content">
                    <ProjectCard  v-for="(project, index) in projects" :key="index" :project="project"/>
                </div>
            </section>
        </main>

        <StandardFooter />
    </div>
</template>

<script>
import Project from '../components/models/Project';

export default {
    data() {
        return {
            projects: [
                new Project("Boolflix", "Netflix-inspired movie database built with Vue.js", "boolflix.jpg", "https://edu-boolflix.netlify.app/", ["HTML", "CSS", "Vue.js"], "https://github.com/eduardomecchia/vue-boolflix"),
                new Project("Boolzapp", "Simple, interactive Vue replica of WhatsApp", "boolzapp.jpg", "https://edu-boolzapp.netlify.app/", ["HTML", "CSS", "Vue.js"], "https://github.com/eduardomecchia/vue-boolzapp")
            ]
        };
    },

    methods: {
    },
};
</script>

<style lang="scss" scoped>
    html,
    body {
        height: 100%;
    }

    .home {
        background-color: #e4ebf3;

        @media screen and (max-width: 768px) {
            & {
                padding-left: 10px;
                padding-right: 10px;
            }
        }
        
        padding-left: 80px;
        padding-right: 80px;

        &__learn-more {
            cursor: pointer;
            font-weight: bolder;
        }

        &__cta {
            margin-bottom: 50px;
        }

        &__section {
            margin-top: 70vh;
        }

        .contact__content {
            display: flex;
            flex-direction: column;
            text-align: center;

            .mail-button {
                align-self: center;
            }

            .social-media {
                li:first-child {
                    margin-bottom: 30px;
                }
                
                margin-bottom: 50px;
                list-style: none;
            }
        }

        .projects__content {
            display: flex;
            flex-direction: row;
            flex-wrap: wrap;
            justify-content: space-evenly;
            align-items: center;
            margin-top: 20px;

            /* @media screen and (max-width: 992px) {
                & {
                    justify-content: center;
                }
            } */
        }
    }
</style>