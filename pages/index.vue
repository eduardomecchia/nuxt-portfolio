<template>
    <!-- App wrapper -->
    <div class="app-wrapper">
        <canvas></canvas>
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

import * as THREE from "three";

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

    mounted() {
        const scene = new THREE.Scene();

        const camera = new THREE.PerspectiveCamera(
            75,
            window.innerWidth / window.innerHeight,
            0.1,
            1000
        );

        const renderer = new THREE.WebGLRenderer({
            
            canvas: document.querySelector("canvas"),
        });

        // debugger;

        renderer.setPixelRatio(window.devicePixelRatio);
        renderer.setSize(window.innerWidth, window.innerHeight);
        camera.position.setZ(30);

        renderer.render(scene, camera);

        const geometry = new THREE.TorusGeometry(10, 3, 16, 100);
        const material = new THREE.MeshStandardMaterial({ color: 0xff6347 });
        const torus = new THREE.Mesh(geometry, material);

        scene.add(torus);
        const pointLight = new THREE.PointLight(0xffffff);
        pointLight.position.set(5, 5, 5);

        const ambientLight = new THREE.AmbientLight(0xffffff);
        scene.add(pointLight, ambientLight);

        const lightHelper = new THREE.PointLightHelper(pointLight);
        const gridHelper = new THREE.GridHelper(200, 50);
        scene.add(lightHelper, gridHelper);

        const controls = new THREE.OrbitControls(camera, renderer.domElement);

        function addStar() {
            const geometry = new THREE.SphereGeometry(0.25);
            const material = new THREE.MeshStandardMaterial({ color: 0xffffff });
            const star = new THREE.Mesh(geometry, material);

            const [x, y, z] = Array(3)
                .fill()
                .map(() => THREE.MathUtils.randFloatSpread(100));

            star.position.set(x, y, z);
            scene.add(star);
        }

        Array(250).fill().forEach(addStar);

        const spaceTexture = new THREE.TextureLoader().load("/../images/black.jpg");
        scene.background = spaceTexture;

        const avatarTexture = new THREE.TextureLoader().load(
            "/../images/avatar.jpg"
        );

        const avatar = new THREE.Mesh(
            new THREE.BoxGeometry(3, 3, 3),
            new THREE.MeshBasicMaterial({ map: avatarTexture })
        );

        scene.add(avatar);

        const planetTexture = new THREE.TextureLoader().load(
            "/../mercury/scene.gltf"
        );

        const planet = new THREE.Mesh(
            new THREE.SphereGeometry(3, 32, 32),
            new THREE.MeshStandardMaterial({ map: planetTexture })
        );

        scene.add(planet);

        planet.position.z = 30;
        planet.position.setX(-10);

        function moveCamera() {
            const t = document.body.getBoundingClientRect().top;
            planet.rotation.x += 0.05;
            planet.rotation.y += 0.075;
            planet.rotation.z += 0.05;

            avatar.rotation.y += 0.01;
            avatar.rotation.z += 0.01;

            camera.position.z = t * -0.01;
            camera.position.x = t * -0.0002;
            camera.rotation.y = t * -0.0002;
        }

        document.body.onscroll = moveCamera;

        function animate() {
            requestAnimationFrame(animate);
            torus.rotation.x += 0.01;
            torus.rotation.y += 0.005;
            torus.rotation.y += 0.01;

            controls.update();

            renderer.render(scene, camera);
        }

        animate();
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

        canvas {
            position: absolute;
            z-index: 10000;
        }
    }
</style>