<template>
  <div class="user-popup-mask">
    <div class="user-popup">
      <div class="user-popup-header">
        <span class="user-popup-title">Профиль пользователя:</span>
        <img class="user-popup-close" @click="$emit('close')" src="@/assets/close.png" />
      </div>
      <div class="user-popup-main">
        <div class="user-popup-avatar">
          <img :src="user.avatar" :style="getBorderColor" />
        </div>
        <div class="user-popup-info">
          <p class="user-popup-info-title">Имя:</p>
          <p>{{ user.name }}</p>
          <p class="user-popup-info-title">Баллы:</p>
          <p>{{ user.rating }}</p>
          <p class="user-popup-info-title">Позиция в рейтинге:</p>
          <p>{{ user.position }}</p>
        </div>
      </div>
      <div class="user-popup-about-me">
        <p class="user-popup-about-me-title">О себе:</p>
        <p>{{ user.description }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserPopup",
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
.user-popup-mask {
  position: fixed;
  z-index: 10;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.2);
  display: flex;
  justify-content: center;
  align-items: center;

  .user-popup {
    width: 500px;
    padding: 20px;
    background-color: #fff;

    .user-popup-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 10px;

      .user-popup-title {
        font-size: 24px;
      }

      .user-popup-close {
        border-radius: 50%;
        width: 16px;
        height: 16px;
        padding: 8px;

        &:hover {
          background: rgba(0, 0, 0, 0.07);
          cursor: url("../assets/cursor.png"), auto;
        }
      }
    }

    .user-popup-main {
      display: flex;
      justify-content: flex-start;

      .user-popup-avatar {
        width: 150px;
        height: 150px;
        display: flex;
        justify-content: center;
        align-items: center;

        img {
          border-radius: 50%;
          width: 129px;
          height: 129px;
        }
      }

      .user-popup-info {
        margin-left: 10px;

        .user-popup-info-title {
          font-size: 18px;
        }

        p {
          margin: 4px 0;
        }
      }
    }

    .user-popup-about-me {
      margin-left: 2px;

      .user-popup-about-me-title {
        font-size: 18px;
      }

      p {
        margin: 5px 0;
      }
    }
  }
}
</style>
