<template>
  <div class="user-card">
    <div class="user-avatar">
      <img :src="user.avatar" :style="getBorderColor" />
    </div>
    <div class="user-info">
      <span>Пользователь:</span>
      <span>{{ user.name }}</span>
    </div>
    <div class="user-rating">
      <img src="@/assets/star.png" />
      <span>{{ user.rating }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserCard",
  props: {
    user: Object,
  },
  computed: {
    getBorderColor() {
      switch (this.user.position) {
        case 1:
          return "border: 4px solid #FDD835;";
        case 2:
          return "border: 4px solid #90A4AE;";
        case 3:
          return "border: 4px solid #795548;";
        default:
          return "";
      }
    },
  },
};
</script>

<style scoped lang="scss">
.user-card {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 18px;
  padding: 10px;

  &:hover {
    background: rgba(0, 0, 0, 0.07);
    border-radius: 10px;
    cursor: url("../assets/cursor.png"), auto;
  }

  .user-avatar {
    width: 80px;
    height: 80px;
    display: flex;
    justify-content: center;
    align-items: center;

    img {
      border-radius: 50%;
      width: 60px;
      height: 60px;
    }
  }

  .user-info {
    flex-grow: 1;
    padding-left: 20px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
  }

  .user-rating {
    display: flex;
    align-items: center;

    span {
      margin-left: 5px;
    }
  }
}
</style>
