<template>
  <div class="expanded-container__stat-row">
    <div class="expanded-container__percentage">{{ percentage }}</div>
    <div class="progress-bar">
      <div :class="['progress-bar', selectProgressBar]" />
    </div>
    <div class="expanded-container__difficulty">
      <img
        class="expanded-container__difficulty__img"
        src="~/assets/icons/easy.svg"
      />{{ $t(difficulty) }}
    </div>
  </div>
</template>

<script>
export default {
  props: {
    percentage: {
      type: String,
      required: true,
    },
    difficulty: {
      type: String,
      required: true,
    },
    id: {
      type: Number,
      required: true,
    },
  },
  computed: {
    selectProgressBar() {
      if (this.id === 0) {
        return "progress-bar__bar1";
      } else if (this.id === 1) {
        return "progress-bar__bar2";
      } else {
        return "progress-bar__bar3";
      }
    },
  },
};
</script>

<style lang="scss" scoped>
@import "~/assets/scss/components/stats/information-card";
</style>
