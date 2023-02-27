<template>
  <div class="app">
    <header>
      <div class="title">
        <h1>
          <img src="./assets/heart.svg" alt="site-logo" />
          Hyrule Jobs
          <img src="./assets/rupee.svg" alt="" />
        </h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">Odered by Title</button>
        <button @click="handleClick('salary')">Odered by Salary</button>
        <button @click="handleClick('location')">Odered by Job location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order"></JobList>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import JobList from "./components/jobList.vue";
import job from "./types/jobs";
import orderTerm from "./types/orderTerm";

export default defineComponent({
  name: "App",
  setup() {
    // const state = reactive({
    //   name: "Link",
    //   age: 26 as number | string,
    // });
    // return { ...toRefs(state) };

    const jobs = ref<job[]>([
      {
        title: "Farm worked",
        location: "lon lon ranch",
        salary: 3000,
        id: "1",
      },
      {
        title: "quarryman",
        location: "death mountain",
        salary: 40000,
        id: "2",
      },
      {
        title: "flute player",
        location: "the lost woods",
        salary: 35000,
        id: "3",
      },
      { title: "fisherman", location: "lake hylia", salary: 21000, id: "4" },
      {
        title: "prison guard",
        location: "gerudo valley",
        salary: 2000,
        id: "5",
      },
    ]);
    const order = ref<orderTerm>("title");
    const handleClick = (term: orderTerm) => {
      order.value = term;
    };
    return { jobs, handleClick, order };
  },
  components: { JobList },
});
</script>

<style>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #10475c;
  border: 3px solid #64b2d1;
  background: #e1edf4;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}

header .title {
  display: flex;
  justify-content: center;
}
header img {
  width: 60px;
  margin-right: 20px;
}
header h1 {
  font-size: 3em;
}
</style>
