<template>
  <div class="page">
    <header class="header">
      <img :src="logo" alt="MERIDIAN" class="logo" />

      <nav class="nav" aria-label="Основная навигация">
        <a class="nav-link active" href="#home">Главная</a>
        <a class="nav-link" href="#projects">Проекты</a>
        <a class="nav-link" href="#about">Обо мне</a>
        <a class="nav-link" href="#contact">Контакты</a>
      </nav>

      <a class="hire-btn" href="#hire">Нанять</a>
    </header>

    <main class="main" id="projects">
      <div class="toolbar">
        <h1 class="title">Проекты</h1>
        <div class="filter-row">
          <FilterInput v-model="searchQuery" />
        </div>
      </div>

      <ProjectList :projects="filteredProjects" />
    </main>
  </div>
</template>

<script>
import FilterInput from './components/FilterInput.vue';
import ProjectList from './components/ProjectList.vue';
import logo from './assets/logo.svg';
import dashboardPreview from './assets/dashboard-preview.webp';
import projectCover from './assets/project-cover.webp';

export default {
  name: 'App',
  components: {
    FilterInput,
    ProjectList,
  },
  data() {
    return {
      logo,
      searchQuery: '',
      projects: [
        {
          id: 1,
          title: 'Финансовый дашборд',
          description:
            'Адаптивный интерфейс аналитики: графики, фильтры и ролевой доступ для fintech-клиента.',
          imageUrl: dashboardPreview,
        },
        {
          id: 2,
          title: 'Портфолио MERIDIAN',
          description:
            'Лендинг фриланс-разработчика с дизайн-системой, карточками кейсов и формой связи.',
          imageUrl: projectCover,
        },
        {
          id: 3,
          title: 'UI-kit для SaaS',
          description:
            'Набор переиспользуемых компонентов: кнопки, поля ввода, теги и карточки продуктов.',
          imageUrl: projectCover,
        },
        {
          id: 4,
          title: 'Кабинет клиента',
          description:
            'Личный кабинет с историей заказов, статусами и быстрым доступом к документам.',
          imageUrl: projectCover,
        },
      ],
    };
  },
  computed: {
    filteredProjects() {
      const query = this.searchQuery.trim().toLowerCase();

      if (!query) {
        return this.projects;
      }

      return this.projects.filter((project) => {
        const title = project.title.toLowerCase();
        const description = project.description.toLowerCase();
        return title.includes(query) || description.includes(query);
      });
    },
  },
};
</script>

<style scoped>
.page {
  min-height: 100vh;
  padding: 24px;
  background-color: var(--color-cream);
}

.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 24px;
  max-width: 1100px;
  margin: 0 auto 32px;
  padding: 16px 28px;
  background-color: var(--color-white);
  border-radius: 16px;
  box-shadow: 0 8px 24px rgba(0, 25, 64, 0.03);
}

.logo {
  height: 36px;
  width: auto;
  flex-shrink: 0;
}

.nav {
  display: flex;
  align-items: center;
  gap: 28px;
  flex-wrap: wrap;
}

.nav-link {
  color: var(--color-dark-blue);
  text-decoration: none;
  font-size: 14px;
  font-weight: 500;
}

.nav-link:hover {
  color: var(--color-orange);
}

.nav-link.active {
  color: var(--color-orange);
  font-weight: 600;
}

.hire-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  height: 36px;
  padding: 0 18px;
  border-radius: 10px;
  background-color: var(--color-dark-blue);
  color: var(--color-cream);
  font-size: 13px;
  font-weight: 600;
  text-decoration: none;
  transition: opacity 0.15s ease;
}

.hire-btn:hover {
  opacity: 0.8;
}

.main {
  max-width: 1100px;
  margin: 0 auto;
}

.toolbar {
  display: flex;
  flex-direction: column;
  align-items: stretch;
  gap: 16px;
  margin-bottom: 24px;
}

.title {
  margin: 0;
  font-size: 28px;
  font-weight: 600;
  color: var(--color-dark-blue);
}

.filter-row {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
  gap: 24px;
  width: 100%;
}

@media (max-width: 860px) {
  .header {
    flex-direction: column;
    align-items: flex-start;
  }
}
</style>
