<template>
    <!-- App wrapper -->
    <div class="app-wrapper">
        <canvas id="c"></canvas>

        <div class="content">
            <!-- Content -->
            <main class="home">
                <Jumbotron />

                <About class="home__section" />

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
                        <ProjectCard v-for="(project, index) in projects" :key="index" :project="project"/>
                    </div>
                </section>
            </main>

            <StandardFooter />
        </div>
    </div>
</template>

<script>
import Project from '../components/models/Project';

export default {
    data() {
        return {
            projects: [
                new Project(
                    "Guess the Number",
                    "Small application built over the course of a weekend with Electron for the first HR test of my life",
                    "guess-the-number.png",
                    "https://drive.google.com/file/d/1USGqq7_gAJyrzaA-ZlHqvfnMFe_EG9gd/view?usp=sharing",
                    ["HTML", "CSS", "Electron"],
                    "https://github.com/eduardomecchia/guess-the-number"
                ),

                new Project(
                    "Eduardo's Task Tracker",
                    "A responsive single page application built with Vue.js to familiarize myself with Vue CLI and keep track of what I have to watch/read/etc.",
                    "task-tracker.png",
                    "https://eduardomecchia.github.io/todos/",
                    ["HTML", "CSS", "Vue.js"],
                    "https://github.com/eduardomecchia/todos"
                ),

                new Project(
                    "Boolflix",
                    "Netflix-inspired movie database built with Vue.js",
                    "boolflix.jpg",
                    "https://edu-boolflix.netlify.app/",
                    ["HTML", "CSS", "Vue.js"],
                    "https://github.com/eduardomecchia/vue-boolflix"
                ),

                new Project(
                    "Boolzapp",
                    "Simple, interactive Vue replica of WhatsApp",
                    "boolzapp.jpg",
                    "https://edu-boolzapp.netlify.app/",
                    ["HTML", "CSS", "Vue.js"],
                    "https://github.com/eduardomecchia/vue-boolzapp"
                )
            ]
        };
    },

    methods: {
    },

    mounted() {
        // geting canvas by Boujjou Achraf
        var c = document.getElementById("c");
        var ctx = c.getContext("2d");

        //making the canvas full screen
        c.height = window.innerHeight;
        c.width = window.innerWidth;

        //chinese characters - taken from the unicode charset
        var matrix = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ123456789@#$%^&*()*&^%+-/~{[|`]}";
        //converting the string into an array of single characters
        matrix = matrix.split("");

        var font_size = 10;
        var columns = c.width/font_size; //number of columns for the rain
        //an array of drops - one per column
        var drops = [];
        //x below is the x coordinate
        //1 = y co-ordinate of the drop(same for every drop initially)
        for(var x = 0; x < columns; x++)
            drops[x] = 1; 

        //drawing the characters
        function draw()
        {
            //Black BG for the canvas
            //translucent BG to show trail
            ctx.fillStyle = "rgba(0, 0, 0, 0.04)";
            ctx.fillRect(0, 0, c.width, c.height);

            ctx.fillStyle = "#0048c5"; // Text color
            ctx.font = font_size + "px arial";
            //looping over drops
            for(var i = 0; i < drops.length; i++)
            {
                //a random chinese character to print
                var text = matrix[Math.floor(Math.random()*matrix.length)];
                //x = i*font_size, y = value of drops[i]*font_size
                ctx.fillText(text, i*font_size, drops[i]*font_size);

                //sending the drop back to the top randomly after it has crossed the screen
                //adding a randomness to the reset to make the drops scattered on the Y axis
                if(drops[i]*font_size > c.height && Math.random() > 0.975)
                    drops[i] = 0;

                //incrementing Y coordinate
                drops[i]++;
            }
        }

        setInterval(draw, 35);

    }
};
</script>

<style lang="scss" scoped>
    body { background: black; }

    canvas {
        display: block;
        width: 100vw;
        height: 100vh;
        position: fixed;
        z-index: -1;
    }
    .home {
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
            margin-top: 50px;
        }

        &__section {
            margin-top: 45vh;
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
            
            @media screen and (max-width: 768px) {
                & {
                    padding: 20px;
                }
            }
        }
    }

    .jumbotron__heading, .content {
        z-index: 10000000;
        color: white;
    }
</style>