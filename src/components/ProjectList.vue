<template>
  <section class="projects">
    <div class="grid" v-if="projects.length > 0">
      <ProjectCard
        v-for="project in projects"
        :key="project.id"
        :project="project"
      />
    </div>
    <p class="empty" v-else>Проекты не найдены</p>
  </section>
</template>

<script>
import ProjectCard from './ProjectCard.vue';

export default {
  name: 'ProjectList',
  components: {
    ProjectCard,
  },
  props: {
    projects: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {};
  },
};
</script>

<style scoped>
.projects {
  display: block;
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 24px;
}

.empty {
  margin: 0;
  padding: 24px;
  background-color: var(--color-white);
  border-radius: 20px;
  box-shadow: 0 8px 24px rgba(0, 25, 64, 0.03);
  color: var(--color-ink);
  font-size: 14px;
}
</style>
