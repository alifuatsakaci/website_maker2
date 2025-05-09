<template>
  <div class="landing-page">
    <!-- Left column: title + nav -->
    <div class="landing-page__content">
      <h1 class="landing-page__title">Ali Fuat Sakaci</h1>
      <nav class="landing-page__nav">
        <NuxtLink class="landing-page__link landing-page__link--portfolio" to="/home">PORTFOLIO</NuxtLink>
        <NuxtLink class="landing-page__link" to="/portfolio">ME</NuxtLink>
        <NuxtLink class="landing-page__link" to="/about">ABOUT</NuxtLink>
        <NuxtLink class="landing-page__link" to="/contact">CONTACT</NuxtLink>
      </nav>
    </div>

    <!-- Right column: photo fullscreen -->
    <div class="landing-page__hero">
      <img
        class="landing-page__photo"
        :src="photo"
        alt="Ali Fuat Sakaci"
      />
    </div>
  </div>
</template>

<script setup>
import photo from '~/assets/images/IMG_4822.jpg'
</script>

<style scoped>
/* Full viewport two-column grid */
.landing-page {
  display: grid;
  grid-template-columns: 1fr 1fr;
  min-height: 100vh;
  margin: 0;
}

/* Left: name and nav */
.landing-page__content {
  position: relative;      /* enable absolute children */
  padding: 4rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  background-color: #fff;
}

.landing-page__title {
  position: absolute;
  top: 82px;
  left: 204px;
  font-family: serif;
  /* Updated font-size to match Adobe XD */
  font-size: 103px;
  font-weight: normal;
  margin: 0;
}

.landing-page__nav {
  margin-top: 200px; /* push nav below title */
  display: flex;
  flex-direction: column;
}

.landing-page__link {
  font-family: serif;
  font-size: 8rem;
  line-height: 1;
  text-decoration: none;
  color: #111;
  margin: 0.2rem 0;
  text-transform: uppercase;
}

/* Positioning for the PORTFOLIO link per design spec */
.landing-page__link--portfolio {
  position: absolute;
  top: 204px;
  left: 204px;
  font-size: 229px;
  margin: 0;
}

/* Right: photo covers entire column */
.landing-page__hero {
  position: relative;
  width: 100%;
  height: 100vh;
  overflow: hidden;
}

.landing-page__photo {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* Responsive: stack content and shrink font-sizes */
@media (max-width: 768px) {
  .landing-page {
    grid-template-columns: 1fr;
  }
  .landing-page__content {
    padding: 2rem;
    align-items: center;
    text-align: center;
  }
  .landing-page__title {
    position: static;
    font-size: 2rem;
    margin-bottom: 1.5rem;
    left: auto;
    top: auto;
  }
  .landing-page__nav {
    margin-top: 0;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    gap: 1rem;
  }
  .landing-page__link {
    font-size: 2.5rem;
  }
  .landing-page__hero {
    height: auto;
  }
  .landing-page__photo {
    position: static;
    width: 100%;
    height: auto;
  }
}
</style>
<template>
  <div class="landing-page">
    <!-- Left column: title + nav -->
    <div class="landing-page__content">
      <h1 class="landing-page__title">Ali Fuat Sakaci</h1>
      <nav class="landing-page__nav">
        <NuxtLink class="landing-page__link landing-page__link--portfolio" to="/home">PORTFOLIO</NuxtLink>
        <NuxtLink class="landing-page__link" to="/portfolio">ME</NuxtLink>
        <NuxtLink class="landing-page__link" to="/about">ABOUT</NuxtLink>
        <NuxtLink class="landing-page__link" to="/contact">CONTACT</NuxtLink>
      </nav>
    </div>

    <!-- Right column: photo fullscreen -->
    <div class="landing-page__hero">
      <img
        class="landing-page__photo"
        :src="photo"
        alt="Ali Fuat Sakaci"
      />
    </div>
  </div>
</template>

<script setup>
import photo from '~/assets/images/IMG_4822.jpg'
</script>

<style scoped>
/* Full viewport two-column grid */
.landing-page {
  display: grid;
  grid-template-columns: 1fr 1fr;
  min-height: 100vh;
  margin: 0;
}

/* Left: name and nav */
.landing-page__content {
  position: relative;      /* enable absolute children */
  padding: 4rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  background-color: #fff;
}

.landing-page__title {
  position: absolute;
  top: 82px;
  left: 204px;
  font-family: serif;
  /* Updated font-size to match Adobe XD */
  font-size: 103px;
  font-weight: normal;
  margin: 0;
}

.landing-page__nav {
  margin-top: 200px; /* push nav below title */
  display: flex;
  flex-direction: column;
}

.landing-page__link {
  font-family: serif;
  font-size: 8rem;
  line-height: 1;
  text-decoration: none;
  color: #111;
  margin: 0.2rem 0;
  text-transform: uppercase;
}

/* Positioning for the PORTFOLIO link per design spec */
.landing-page__link--portfolio {
  position: absolute;
  top: 204px;
  left: 204px;
  font-size: 229px;
  margin: 0;
}

/* Right: photo covers entire column */
.landing-page__hero {
  position: relative;
  width: 100%;
  height: 100vh;
  overflow: hidden;
}

.landing-page__photo {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* Responsive: stack content and shrink font-sizes */
@media (max-width: 768px) {
  .landing-page {
    grid-template-columns: 1fr;
  }
  .landing-page__content {
    padding: 2rem;
    align-items: center;
    text-align: center;
  }
  .landing-page__title {
    position: static;
    font-size: 2rem;
    margin-bottom: 1.5rem;
    left: auto;
    top: auto;
  }
  .landing-page__nav {
    margin-top: 0;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    gap: 1rem;
  }
  .landing-page__link {
    font-size: 2.5rem;
  }
  .landing-page__hero {
    height: auto;
  }
  .landing-page__photo {
    position: static;
    width: 100%;
    height: auto;
  }
}
</style>
