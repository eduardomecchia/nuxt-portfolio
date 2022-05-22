<template>
    <!-- App wrapper -->
    <div class="app-wrapper">
        <!-- Navbar 
        <header>
            <nav id="website-navbar">
                <ul>
                <li class="navbar-entry">
                    <a href="#" class="navbar-entry_">Eduardo Mecchia</a>
                </li>

                <li class="navbar-entry">
                    <a href="#" class="navbar-entry_">Projects</a>
                </li>
                
                <li class="navbar-entry">
                    <a href="#" class="navbar-entry_">Contact</a>
                </li>
                </ul>
            </nav>
        </header> -->

        <!-- Jumbotron -->
        <!-- <section id="website-jumbotron">
            <div class="jumbotron">
                <div class="jumbotron-content">
                    <h1 class="jumbotron-content_">Eduardo Mecchia</h1>
                    <p class="jumbotron-content_">
                        I'm a software developer, currently working at <a href="https://www.linkedin.com/in/eduardo-mecchia-a0a9b7b4/" target="_blank">LinkedIn</a>.
                    </p>
                </div>
            </div>
        </section> -->

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
                </div>
            </section>

            <!-- Projects section -->
            <section class="home__section" id="projects">
                <h2 class="home__section__heading">Projects</h2>
                <Divider />

                <div class="home__section__content contact__content">
                    <div v-for="(project, index) in projects" :key="index">
                        <ProjectCard :project="project" />
                    </div>
                </div>
            </section>
        </main>

        <FollowMe />

        <footer id="website-footer">
            <div>&copy;2022 Eduardo Mecchia</div>

            <div>
                <span>Built using Nuxt.js</span>

                <a href="https://nuxtjs.org/" target="_blank">
                    <img src="nuxt.ico" alt="Icon of Nuxt.js framework" width="25" height="25">
                </a>
            </div>
        </footer>
    </div>
</template>

<script>
import Project from '../components/models/Project.js';

export default {
    data() {
        return {
            projects: [
                new Project(
                    'Boolflix',
                    'Netflix-inspired movie database built with Vue.js',
                    '',
                    'https://edu-boolflix.netlify.app/',
                    ['HTML', 'CSS', 'Vue.js'],
                    'https://github.com/eduardomecchia/vue-boolflix'
                ),
                
                new Project(
                    'Boolzapp',
                    'Simple, interactive Vue replica of WhatsApp',
                    '',
                    'https://edu-boolzapp.netlify.app/',
                    ['HTML', 'CSS', 'Vue.js'],
                    'https://github.com/eduardomecchia/vue-boolzapp'
                )
            ]
        }
    },

    methods: {
        /**
         * Scrolls to the element of the given ID
         * @param {string} id - The ID (HTML) of the element to scroll to
        */
        scrollToElement(id) {
            if (document.querySelector(`#${id}`)) {
                document.querySelector(`#${id}`).scrollIntoView({
                    behavior: 'smooth',
                    block: 'start',
                });
            }
        },
    }
};
</script>
