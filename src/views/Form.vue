<template>
  <div class="form">
    <h1>This is the form with validation page</h1>
    <FormValidation/>
  </div>
</template>

<script>

import { Component, Vue } from 'vue-property-decorator';
import FormValidation from '../components/FormValidation';

export default {
  name: 'form',
  components: {
    FormValidation,
  }
}

</script>