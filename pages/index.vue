<template>
    <!-- App wrapper -->
    <div class="app-wrapper">
        <!-- Content -->
        <main class="home">
            <div class="home__hero-section">
                <h1 class="home__hero-section__heading slide-in-from-left">
                    Hey! I'm Eduardo, a
                    <strong class="gradient-text">full stack web developer</strong>.<br/>
                    The website is a WiP, I will be adding my projects and more sections soon!
                </h1>

                <b-button
                    @click="scrollToElement('about')"
                    class="home__cta mail-button scale-on-hover"
                    pill
                    variant="primary"
                >Learn more</b-button>
            </div>

            <!-- About section -->
            <section class="home__section" id="about" ref="aboutSection">
                <h2 class="home__section__heading">About me</h2>
                <Divider />

                <div class="home__section__content about__content">
                    <p class="home__section__content__paragraph" id="first-paragraph">
                        I’m a 21-year-old <strong>software developer</strong> from Rome with
                        a strong passion for everything that has to do with technology and
                        innovation. I started tinkering with my first PC when I was 7 years
                        old and since that day I have never stopped: I fell in love with the
                        Internet and its being a free and enormous source of knowledge.
                        That’s why I decided to dive into <strong>web development</strong>,
                        dreaming to make people’s lives easier thanks to sophisticated and
                        <strong>user-friendly</strong> products. I've also chosen this field
                        because of its constant evolution and because of my perpetual desire
                        to grow and learn. I’m also a big fan of plain and simple
                        <strong>problem solving</strong>: one of the greatest sources of
                        satisfaction in my life is fixing the problems of those who don’t
                        know their way around technology and most importantly teach them, if
                        possible, to handle similar barriers themselves in the future.
                    </p>

                    <!-- Photo of me -->
                    <figure class="home__section__content__figure">
                        <b-img
                            src="~/assets/images/person.png"
                            fluid
                            alt="Photo of Eduardo Mecchia"
                        ></b-img>
                    </figure>
                </div>

                <div class="technologies">ROWS OF TECHNOLOGIES USED</div>
            </section>

            <!-- Contact section -->
            <section class="home__section" id="contact">
                <h2 class="home__section__heading">Contact me</h2>
                <Divider />

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

                    <ul class="social-media">
                        <li>You can also reach me through social media!</li>
                        
                        <!-- First instance of social media component -->
                        <li class="social-media-icon">CYCLE THROUGH SOCIAL MEDIAS</li>
                    </ul>
                </div>
            </section>

            <!-- Projects section -->
            <section class="home__section" id="projects">
                <h2 class="home__section__heading">Projects</h2>
                <Divider />

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
        },
    }
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

        &__cta {
            margin-top: 50px;
        }

        &__hero-section {
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
        }

        &__section {
            padding: 20px;

            &__heading {
                text-align: center;
                font-weight: bold;
                font-size: 40px;
            }

            &__content {
                margin-top: 20px;
            }

            .about__content {
                display: flex;

                @media screen and (max-width: 768px) {
                    & {
                        flex-direction: column;
                    }
                }

                p {
                    width: 50%;
                    padding: 20px;

                    @media screen and (max-width: 768px) {
                        & {
                            width: 100%;
                            order: 2;
                        }
                    }
                }

                figure {
                    @media screen and (max-width: 768px) {
                        & {
                            width: 100%;
                            order: 1;
                        }
                    }

                    width: 50%;
                    display: flex;
                    justify-content: center;
                    align-items: center;

                    img {
                        box-shadow: 5px 10px 18px #888;
                        transition: all .2s ease-in-out;
                        cursor: pointer;

                        &:hover {
                            transform: scale(1.05);
                            box-shadow: 5px 10px 18px #3b5998;
                        }
                    }
                }

            }

            .technologies {
                display: flex;
                justify-content: center;
                align-items: center;
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

                    margin-top: 50px;
                    list-style: none;
                }
            }

            .projects__content {
                display: flex;
                flex-direction: row;
                flex-wrap: wrap;
                justify-content: space-between;
                align-items: center;
                margin-top: 20px;

                @media screen and (max-width: 768px) {
                    & {
                        justify-content: center;
                    }
                }
            }
        }

        &__learn-more {
            cursor: pointer;
            font-weight: bolder;
        }
    }
</style>