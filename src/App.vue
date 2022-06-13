<template>
  <div>
    <the-header></the-header>
    <badge-list></badge-list>
    <user-info
      :full-name="activeUser.name"
      :info-text="activeUser.description"
      :role="activeUser.role"
    ></user-info>
    <h2>Scoped Slots</h2>
    <course-goal #default="slotProps">
      <h2>{{ slotProps.item }}</h2>
      <p>{{ slotProps.anotherProp }}</p>
    </course-goal>
    <h2>Dynamic Components</h2>
    <button @click="selectedCmp('goal-new')">New Goal</button>
    <button @click="selectedCmp('goal-old')">Old Goal</button>
    <keep-alive>
      <component :is="selectedComponent"></component>
    </keep-alive>
  </div>
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
import BadgeList from "./components/BadgeList.vue";
import UserInfo from "./components/UserInfo.vue";
import CourseGoal from "./components/CourseGoal.vue";
import GoalNew from "./components/GoalNew.vue";
import GoalOld from "./components/GoalOld.vue";

export default {
  components: {
    TheHeader,
    BadgeList,
    UserInfo,
    CourseGoal,
    GoalNew,
    GoalOld,
  },
  data() {
    return {
      activeUser: {
        name: "Femke Boermans",
        description: "Site owner and admin",
        role: "admin",
      },
      selectedComponent: "goal-new",
    };
  },
  methods: {
    selectedCmp(cmp) {
      this.selectedComponent = cmp;
    },
  },
};
</script>

<style scoped>
html {
  font-family: sans-serif;
}

body {
  margin: 0;
}
</style>