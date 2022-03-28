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
        <h1 class="home__hero-section__heading">Hey! I'm Eduardo, a <strong>full stack web developer</strong>.</h1>

        <NuxtLink to="#about">Learn more</NuxtLink>
      </div>

      <section class="home__section" id="about">
        <h2 class="home__section__heading">About me</h2>

        <div class="home__section__content">
          <p class="home__section__content__paragraph" id="first-paragraph">I’m a 21-year-old software developer from Rome with a strong passion for everything that has to do with technology and innovation.
          I started tinkering with my first PC when I was 7 years old and since that day I have never stopped: I fell in love with the Internet and its being a free and enormous source of knowledge.
          That’s why I decided to dive into web development, dreaming to make people’s lives easier thanks to sophisticated and user-friendly products. I've also chosen this field because of its constant evolution and because of my perpetual desire to grow and learn.
          I’m also a big fan of plain and simple problem solving: one of the greatest sources of satisfaction in my life is fixing the problems of those who don’t know their way around technology and most importantly teach them, if possible, to handle similar barriers themselves in the future.</p>

          <!-- Photo of me -->
          <figure class="home__section__content__figure">
            <img src="~/assets/images/person.png" alt="Photo of me">
          </figure>
        </div>
      </section>
    </main>

    <follow-me />

    <footer id="website-footer">&copy; 2022 Eduardo Mecchia</footer>
  </div>
</template>

<script>
  import followMe from '../components/follow-me.vue';

  export default {
    components: {
      followMe
    }
  }
</script>
