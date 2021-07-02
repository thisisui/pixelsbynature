<template>
  <div class="card card--decorated">
    <h3 class="card__title">{{ title }}</h3>
    <div class="card__hero">
      <img
        class="card__hero-image"
        :src="require('@/assets/' + imagePath + '')"
        alt=""
      />
    </div>
    <p class="card__description">{{ description }}</p>
    <ul class="card__tags">
      <li v-for="tag in tags" :key="tag" class="card__tag">{{ tag }}</li>
    </ul>
  </div>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "Card",
  props: {
    title: {
      type: String,
      default: "Title",
    },
    imagePath: {
      type: String,
      default: "#",
    },
    description: {
      type: String,
      default: "Title",
    },
    tags: {
      type: Array,
      default: () => {
        return;
      },
    },
  },
});
</script>

<style scoped lang="scss">
@import "@/styles/_colors";

.card {
  text-align: left;
  border: 1px solid $secondary-color;
  padding: 20px;
  flex: 1;
  margin: 0 20px 20px;

  &--decorated {
    border-top: 4px solid $primary-color;
    will-change: border-top-color;
    transition: border-top-color 0.5s ease;

    &:hover {
      border-top-color: $primary-color-accent;
    }
  }

  &__hero {
    margin-bottom: 20px;
  }

  &__hero-image {
    width: 100%;
    outline: 3px dotted $secondary-color;
  }

  &__tags {
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
    flex-wrap: wrap;
  }

  &__tag {
    border: 1px solid $secondary-color;
    padding: 5px;
    margin-right: 10px;
    margin-bottom: 10px;
  }

  &__title {
    margin-top: 0;
  }

  &__description {
    margin: 0 0 20px;
    line-height: 32px;
  }
}
</style>
