<template>
  <div class="rating">
    <div class="rating-header">
      <span class="title-rating">Рейтинг пользователей:</span>
      <img class="sort-rating" @click="users.reverse()" src="@/assets/sort.png" />
    </div>
    <div v-for="user in users" :key="user.id" @click="openUserPopup(user)">
      <user-card :user="user"></user-card>
    </div>
    <user-popup v-if="showPopup" :user="currentUser" @close="showPopup = false"></user-popup>
  </div>
</template>

<script>
import UserCard from "./UserCard.vue";
import UserPopup from "./UserPopup.vue";
import axios from "axios";

export default {
  name: "UserRating",
  components: {
    UserCard,
    UserPopup,
  },
  data: () => ({
    users: [],
    showPopup: false,
    currentUser: {},
  }),
  methods: {
    openUserPopup(user) {
      this.currentUser = user;
      this.showPopup = true;
    },
  },
  created() {
    axios({
      url: "https://my-json-server.typicode.com/Vespand/crmm-tasks/users",
      method: "get",
    })
      .then((resp) => {
        this.users = resp.data
          .sort((a, b) => b.rating - a.rating)
          .map((user, index) => {
            user.position = index + 1;
            return user;
          });
      })
      .catch((err) => {
        console.error(err);
      });
  },
};
</script>

<style scoped lang="scss">
.rating {
  max-width: 600px;
  margin: 0 auto;

  .rating-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 10px;

    .title-rating {
      font-size: 24px;
    }

    .sort-rating {
      border: 1px solid rgba(44, 62, 80, 0.67);
      border-radius: 8px;
      margin-right: 5px;
      padding: 2px;

      &:hover {
        background: rgba(0, 0, 0, 0.07);
        cursor: url("../assets/cursor.png"), auto;
      }
    }
  }
}
</style>
