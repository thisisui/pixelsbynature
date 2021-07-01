<template>
  <div class="main home">
    <section class="hero">
      <h1 data-glitch="Pixels by Nature" class="hero__title">
        Pixels by Nature
      </h1>
    </section>
    <section class="box">
      <h3 class="box__title">Projects</h3>
      <Card
        title="Atlas of Medicinal plants"
        imagePath="medical-plants.jpg"
        description="Free mobile application for Android where I've gathered 371 medicinal
          plants. It lists active substances and usage of each of the plant."
        :tags="['React Native', 'Redux']"
      />
      <Card
        title="Homie The Game"
        imagePath="homie-the-game.jpg"
        description="Unity game about a average boy who needs to save his neighbourhood againts
      big corporation. (not live yet)"
        :tags="['Unity', 'Aseprite', 'Pixel Studio Pro']"
      />
    </section>
    <section class="footer">
      <ul class="footer__menu">
        <li class="footer__menu-item">
          <a
            class="footer__menu-item-link"
            href="mailto:contact@pixelsbynature.com"
            >Contact me</a
          >
        </li>
      </ul>
    </section>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Card from "@/components/Card.vue";

export default defineComponent({
  name: "Home",
  components: { Card },
});
</script>

<style scoped lang="scss">
@import "@/styles/_colors";

.hero {
  margin: 40px 0 20px;
  text-align: right;
  position: relative;

  &__title {
    text-decoration: none;
    text-transform: uppercase;
    text-align: center;
    margin: 0;
    letter-spacing: 5px;
    position: relative;

    &:before,
    &:after {
      display: block;
      content: attr(data-glitch);
      text-transform: uppercase;
      text-align: center;
      position: absolute;
      top: 0;
      left: 0;
      height: 100%;
      width: 100%;
      opacity: 0.8;
    }
    &:after {
      color: $primary-color;
      z-index: -2;
    }
    &:before {
      color: $primary-color-accent;
      z-index: -1;
    }
    &:hover {
      &:before {
        animation: glitch 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94) both 5;
      }
      &:after {
        animation: glitch 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94) reverse both
          5;
      }
    }
  }
}

.box {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;

  &__title {
    flex: 0 0 calc(100% - 40px);
    margin: 0 20px 20px;
  }

  @media screen and (max-width: 768px) {
    flex-direction: column;
  }
}

.footer {
  background: $primary-color-accent;
  padding: 20px 0;

  &__menu {
    margin: 0;
    list-style: none;
  }

  &__menu-item-link {
    color: #fff;
    text-decoration: none;

    &:hover {
      text-decoration: dotted;
    }
  }
}

@keyframes glitch {
  0% {
    transform: translate(0);
  }
  20% {
    transform: translate(-5px, 5px);
  }
  40% {
    transform: translate(-5px, -5px);
  }
  60% {
    transform: translate(5px, 5px);
  }
  80% {
    transform: translate(5px, -5px);
  }
  to {
    transform: translate(0);
  }
}
</style>
