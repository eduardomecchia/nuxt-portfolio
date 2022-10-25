<template>
    <section id="about">
        <Heading text="About me"></Heading>

        <article>
            <p>
                I’m a 21-year-old <strong>software developer</strong> from Rome with
                a strong passion for everything that has to do with technology and
                innovation.
                <br>
                I started tinkering with my first PC when I was 7 years
                old and since that day I have never stopped: I fell in love with the
                Internet and its being a free and enormous source of knowledge.
                <br>
                That’s why I decided to dive into <strong>web development</strong>,
                dreaming to make people’s lives easier thanks to sophisticated and
                <strong>user-friendly</strong> products. I've also chosen this field
                because of its constant evolution and because of my perpetual desire
                to grow and learn.
                <br>
                I’m a big fan of plain and simple
                <strong>problem solving</strong>: one of the greatest sources of
                satisfaction in my life is fixing the problems of those who don’t
                know their way around technology and most importantly teach them, if
                possible, to handle similar barriers themselves in the future.
            </p>

            <!-- Photo of me -->
            <figure>
                <b-img
                    src="~/assets/images/playa-tora-paguera.png"
                    fluid
                    alt="Photo of Eduardo Mecchia looking at the ocean in Playa Tora, Paguera, Mallorca."
                ></b-img>
            </figure>
        </article>

        <!-- <div class="technologies">ROWS OF TECHNOLOGIES USED</div> -->
    </section>
</template>

<style lang="scss" scoped>
    section {
        padding: 20px;

        article {
            margin-top: 20px;
            display: flex;

            @media screen and (max-width: 768px) {
                & {
                    flex-direction: column;
                }
            }

            p {
                width: 50%;
                padding: 20px;
                text-align: right;
                
                @media screen and (max-width: 768px) {
                    & {
                        margin-top: 50px;
                        width: 100%;
                        order: 2;
                        text-align: center;
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
            margin: 50px 0;
        }
    }
</style>