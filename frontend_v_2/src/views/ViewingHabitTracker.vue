<template>
  <div class="container col-xxl-8 px-2 py-2 bg-white cursor">
    <form>
      <h2 class="benefits__title_theme_templates">
        Выберите привычку, которую вы бы хотели просмотреть:</h2>
      <div id="v-model-radiobutton" class="demo">
          <li v-for="habit in habits">
            <div class="card mb-3 shadow-lg ">
              <div class="card-body">
                <ul class="diary__title">
                  <a class="link_list_diary">
                    <router-link :to="{ path: '/viewing_habit_tracker/'+ habit.habit_id}"><a>{{ habit.habit_name }}</a>
                    </router-link>
                  </a>
                </ul>
              </div>
            </div>
          </li>
        </div>
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "ViewingHabitTracker",
  data() {
    return {
      habits: [],
      errorMsg: `An error occurred, please try again`
    }
  },
  async created() {
// GET request using axios with async/await// исправить в зависисмости от url
    const response = await axios.get("https://eternal-awareness.herokuapp.com/habit_trackers");
    this.habits = response.data["habits"];
    console.log(this.habits)
  },
}
</script>

<style scoped>
h4 {
  margin-left: 30px;
}

li {
  list-style-type: none;
}

h3 {
  margin-left: 100px;
}

a {
  color: black;
  text-decoration: none; /* Отменяем подчеркивание у ссылки */
}

a:hover {
color: #4f73e8; /* Цвет ссылки при наведении */
      cursor: pointer;
}

a:focus {
  outline: none;
}

.cursor {
  cursor: default;
}
</style>



