<script>
import AllCourses from './components/AllCourses.vue';
import CoursePlanner from './components/CoursePlanner.vue';

export default {
  data() {
    return {
      currentPage: 'all-courses',
    };
  },
  computed: {
    currentComponent() {
      return this.currentPage === 'all-courses' ? AllCourses : CoursePlanner;
    },
  },
  methods: {
    navigateTo(page) {
      this.currentPage = page;
    },
  },
};
</script>

<template>
  <div id="app" class="app-container">
    <aside class="sidebar">
      <ul>
        <li @click="navigateTo('all-courses')" :class="{ active: currentPage === 'all-courses' }">全部课程</li>
        <li @click="navigateTo('course-planner')" :class="{ active: currentPage === 'course-planner' }">课程规划</li>
      </ul>
    </aside>
    <main class="main-content">
      <component :is="currentComponent"/>
    </main>
  </div>
</template>

<style scoped>
.app-container {
  display: flex;
  height: 100vh;
  background-color: white;
}

.sidebar {
  width: 200px;
  background-color: #f0f8ff;
  border-right: 1px solid #e0e0e0;
  padding: 1rem;
}

.sidebar ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.sidebar li {
  padding: 0.5rem;
  cursor: pointer;
  color: #333;
  border-radius: 4px;
  transition: background-color 0.3s;
}

.sidebar li:hover {
  background-color: #e0f7ff;
}

.sidebar li.active {
  background-color: #d0ebff;
  font-weight: bold;
}

.main-content {
  flex: 1;
  padding: 1rem;
}
</style>
