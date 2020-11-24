<template>
  <div class="DataLoader">
    <slot v-if="response.loading" name="loader">
      <p><strong>Loading...</strong></p>
    </slot>
    <template v-if="!response.loading">
      <slot v-if="response.data" :data="response.data" name="data">
        <p>Success, you got an response:</p>
        <code>{{ response.data }}</code>
      </slot>
      <slot v-if="response.error" :error="response.error" name="error">
        <p>Oh no, there was an error with your request:</p>
        <code>{{ response.error }}</code>
      </slot>
    </template>
  </div>
</template>

<script>
import { computed, defineComponent, ComputedRef } from "vue";

import vueFetch from "@whatsaaaaa/vue-data-fetch/dist";

export default {
  name: "DataLoader",
  props: {
    url: {
      type: String,
      required: true,
    },
  },
  setup(props) {
    const url = computed(() => props.url);
    const response = vueFetch(url);

    return {
      response,
    };
  },
};
</script>
