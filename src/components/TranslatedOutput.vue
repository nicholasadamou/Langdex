/* eslint-disable */

<template lang="pug">
  article.message.is-info
    .message-header
      | Translation Information
    .message-body
      | {{ data }}
</template>

<script>
export default {
  name: "translatedOutput",
  props: ["data"]
};
</script>