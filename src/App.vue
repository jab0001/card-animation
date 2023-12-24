<template>
  <div class="game">
    <ul class="game__list">
      <li v-for="(card, index) in cards" :key="index">
        <CardItem :card="card" />
      </li>
    </ul>
    <button @click="switchCard" class="game__btn">Открыть карту</button>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import CardItem from "./components/CardItem.vue";

export default Vue.extend({
  name: "App",
  components: {
    CardItem,
  },
  data() {
    return {
      cards: [
        { id: 1, isOpened: false },
        { id: 2, isOpened: false },
        { id: 3, isOpened: false },
      ],
    };
  },
  methods: {
    switchCard() {
      this.$set(this.cards, 1, {
        isOpened: !this.cards[1].isOpened,
      });
    },
  },
});
</script>

<style lang="scss">
.game {
  background-color: #1a1d33;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: end;

  &__list {
    display: flex;
    min-width: 595px;
    margin: 0 auto;
    justify-content: space-between;
    margin-bottom: 45px;
  }

  &__btn {
    margin: 20px 0px 100px 0px;
    padding: 10px;
    border: none;
    background: yellow;
    border-radius: 16px;

    font-size: 20px;
  }

  @media (min-width: 320px) and (max-width: 600px) {
    justify-content: center;
    &__list {
      min-width: initial;
      gap: 7px;
    }

    &__btn {
      margin: 0px 0px 20px 0px;
    }
  }
}
</style>
