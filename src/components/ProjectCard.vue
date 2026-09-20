<template>
  <article class="card" v-if="project">
    <img class="cover" :src="project.imageUrl" :alt="project.title" />
    <div class="body">
      <h3 class="title">{{ project.title }}</h3>
      <p class="description">{{ project.description }}</p>
      <a class="cta" href="#case">
        Смотреть кейс
        <img :src="arrowIcon" alt="" class="icon" aria-hidden="true" />
      </a>
    </div>
  </article>
</template>

<script>
import arrowIcon from '../assets/arrow.svg';

export default {
  name: 'ProjectCard',
  props: {
    project: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      arrowIcon,
    };
  },
};
</script>

<style scoped>
.card {
  width: 100%;
  background-color: var(--color-white);
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 8px 24px rgba(0, 25, 64, 0.03);
}

.cover {
  display: block;
  width: 100%;
  height: 180px;
  object-fit: cover;
}

.body {
  display: flex;
  flex-direction: column;
  gap: 10px;
  padding: 16px 20px 20px;
}

.title {
  margin: 0;
  font-size: 18px;
  font-weight: 600;
  color: var(--color-dark-blue);
}

.description {
  margin: 0;
  font-size: 13px;
  line-height: 1.45;
  color: var(--color-ink);
}

.cta {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  margin-top: 4px;
  color: var(--color-orange);
  font-size: 13px;
  font-weight: 600;
  text-decoration: none;
}

.icon {
  width: 16px;
  height: 16px;
  filter: invert(42%) sepia(74%) saturate(1800%) hue-rotate(339deg) brightness(96%) contrast(90%);
}
</style>
