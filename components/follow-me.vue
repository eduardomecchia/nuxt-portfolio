<template>
    <div class="follow-me">
        <ul>
            <li>
                <small>Follow me</small>
            </li>

            <li>
                <a class="social-network-icon github" target="_blank" href="https://github.com/eduardomecchia" title="Follow on GitHub">
                    <img src="~/assets/svg/github.svg" alt="GitHub" />
                </a>
            </li>

            <li>
                <a class="social-network-icon linkedin" target="_blank" href="https://linkedin.com/in/eduardomecchia" title="Connect on Linkedin">
                    <img src="~/assets/svg/linkedin.svg" alt="LinkedIn" />
                </a>
            </li>
            
            <li>
                <a class="social-network-icon twitter" target="_blank" href="https://twitter.com/eduardo_mecchia" title="Follow on Twitter">
                    <img src="~/assets/svg/twitter.svg" alt="Twitter" />
                </a>
            </li>
            
            <li>
                <a class="social-network-icon instagram" target="_blank" href="https://instagram.com/mec43" title="Follow on Instagram">
                    <img src="~/assets/svg/instagram.svg" alt="Instagram" />
                </a>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: 'FollowMe'
    }
</script>

<style lang="scss" scoped>
    .follow-me {
        // TODO: IF YOU BUILD OTHER PAGES, THE BOX ELEMENTS NEED TO DISSOLVE WITH A TRANSITION
        @media screen and (max-width: 768px) {
            & {
                bottom: 111px;
                width: 100%;
                height: auto;
                top: auto;
                left: 0;
                text-align: left;

                ul {
                    display: flex;
                }
            }
        }

        z-index: 1001;
        position: fixed;
        left: 0;
        top: calc(50% - (275px / 2));
        width: 55px;
        height: 275px;

        ul {
            margin: 0; // Necessary cause of reboot.scss, look into it
        }

        li {
            transition: transform 425ms cubic-bezier(.69,.03,.03,.93),opacity .15s ease-out;
            display: inline-block;

            a {
                display: flex;
                align-items: center;
                justify-content: center;
                width: 75px;
                height: 55px;
                padding-left: 20px;
                margin-left: -20px;
                transition: transform 425ms cubic-bezier(.05,.65,.18,1);

                &:hover {
                    -moz-transform: translate3d(20px,0,0);
                    -ms-transform: translate3d(20px,0,0);
                    -webkit-transform: translate3d(20px,0,0);
                    transform: translate3d(20px,0,0);
                }

                @media screen and (max-width: 768px) {
                    & {
                        height: 50px;
                        width: 50px;
                        padding-left: 0;
                        margin-left: 0;

                        &:hover {
                            transform: none;
                        }
                    }
                }
            }
        }

        small {
            position: absolute;
            top: 5px;
            left: -2px;
            width: 100%;
            text-align: right;
            color: #7a7a7a;
            font-weight: 600;
            font-size: .65em;

            @media screen and (max-width: 768px) {
                & {
                    text-align: left;
                    padding-left: 10px;
                    top: -20px;
                }
            }
        }

        .social-network-icon {
            img {
                width: 25px;
                height: 25px;
            }
        }

        .github,
        .linkedin,
        .instagram {
            img {
                filter: invert(1);
            }
        }

        .github {
            background-color: #4e545a;
        }

        .linkedin {
            background-color: #0077ba;
        }

        .twitter {
            background-color: #50abf1;
        }

        .instagram {
            background: radial-gradient(circle at 25% 110%,#fdf497 0,#fdf497 5%,#fd5949 45%,#d6249f 60%,#285aeb 90%),radial-gradient(circle at 25% 110%,#b9a800 0,#938500 5%,#b10f00 45%,#8c0061 60%,#002ca9 90%);
        }
    }
</style>