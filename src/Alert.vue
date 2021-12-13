<template>

  <div>

    <!--
    <transition name="fade" appear>
    <transition :css="false" @enter="enter" @leave="leave">
    -->

    <transition name="bounce" appear mode="out-in">
      <div class="ui alert message success" v-if="visible" key="visible">
        Un peu de texte
      </div>
      <div class="ui alert message error" v-else key="invisible">
        D'autres choses
      </div>
    </transition>
    <button @click="toggle">Bascule</button>

      <transition-group name="bounce" tag="ul">
        <li v-for="item in items" :key="item">
          {{ item }}
        </li>
      </transition-group>

    <button class="ui button" @click="add">Ajouter</button>
    <button class="ui button error" @click="shuffle">Mélanger</button>

  </div>

</template>

<script>

export default {
  /*
  mixins: [slides],
   */
  data () {
    return {
      visible: true,
      items: [1,2,3,4,5]
    }
  },
  methods: {
    add: function () {
      this.items.push(Math.random())
    },
    shuffle: function () {
      this.items = [2,4,3,1,5]
    },
    toggle: function () {
      this.visible = !this.visible
    }
  }

}

/*
let slides = {
  methods: {
    enter: function (el, done) {
      $(el).hide().slideDown(500, done)
    },
    leave: function (el, done) {
      $(el).show().slideUp(500, done)
    },
    toggle: function () {
      this.visible = !this.visible
    }
  }
}
 */
</script>

<style>
  .fade-enter-active, .fade-leave-active {
    transition: opacity 1s, transform 1s;
  }
  .fade-enter, .fade-leave-active {
    opacity: 0;
    transform: translate(20px);
  }
  .bounce-enter-active {
    animation: bounce-in .5s;
  }
  .bounce-leave-active {
    animation: bounce-out .5s;
  }
  .bounce-move {
    transition: transform 5s;
  }

  @keyframes bounce-in {
    0% {
      transform: scale(0);
    }
    50% {
      transform: scale(1.5);
    }
    100% {
      transform: scale(1);
    }
  }
  @keyframes bounce-out {
    0% {
      transform: scale(1);
    }
    50% {
      transform: scale(1.5);
    }
    100% {
      transform: scale(0);
    }
  }
</style>
