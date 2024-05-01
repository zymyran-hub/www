<template>
  <UButton
    block
    size="xl"
    :disabled="!isFinished"
    :label="title+' ('+prettifyTimer+')'"
    @click="handleButtonClick"
  />
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
    },
    minutes: {
      type: Number,
      default: 1,
    },
    seconds: {
      type: Number,
      default: 0,
    },
  },
  setup(props, {emit}) {
    const minutes = ref(props.minutes);
    const seconds = ref(props.seconds);
    const isFinished = ref(false);

    onMounted(() => {
      watchEffect(() => {
        let intervalId = setInterval(() => {
          if (seconds.value === 0) {
            if (minutes.value === 0) {
              isFinished.value = true;
              clearInterval(intervalId);
            } else {
              minutes.value--;
              seconds.value = 59;
            }
          } else {
            seconds.value--;
          }
        }, 1000);
        return () => {
          clearInterval(intervalId);
        };
      });
    });

    const prettifyTimer = computed(() => {
      return `${('0' + minutes.value).slice(-2)}:${('0' + seconds.value).slice(-2)}`;
    });

    const handleButtonClick = () => {
      emit('timerFinished');
    };

    return {
      prettifyTimer,
      isFinished,
      handleButtonClick
    };
  },
};
</script>
