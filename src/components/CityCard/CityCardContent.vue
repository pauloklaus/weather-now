<template>
  <div class="card-content" :class="colorByTemp">
    <div class="card-content__temp">{{ temp }}</div>
    <div class="card-content__deg">&deg;</div>
  </div>
</template>

<script>
import { computed, defineComponent } from "vue";

export default defineComponent({
  props: {
    temp: {
      type: Number,
      required: true,
    },
  },
  setup({ temp }) {
    const colorByTemp = computed(() => {
      const colorClass = "card-content--";

      if (temp <= 5) {
        return `${colorClass}blue`;
      }

      if (temp >= 25) {
        return `${colorClass}red`;
      }

      return `${colorClass}orange`;
    });

    return {
      colorByTemp,
    };
  },
});
</script>

<style scoped>
.card-content {
  display: flex;
  justify-content: center;
}

.card-content__temp {
  font-size: 5rem;
  letter-spacing: -5px;
}

.card-content__deg {
  font-size: 2.5rem;
  margin-top: 14px;
}

.card-content--blue > div {
  color: var(--info);
}

.card-content--red > div {
  color: var(--danger);
}

.card-content--orange > div {
  color: var(--warning);
}

@media (min-width: 640px) {
  .card-content__temp {
    margin-top: 20px;
  }

  .card-content__deg {
    margin-top: 26px;
  }
}
</style>
