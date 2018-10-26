<template>
  <div id="app">
    <div class="uk-width-2-3@m uk-position-center">
      <div class="uk-grid-match uk-grid-collapse uk-child-width-expand@s" uk-grid>
        <div class="uk-width-2-5@s bg-img">
          <app-description></app-description>
        </div>
        <div class="uk-width-3-5@s">
          <app-form></app-form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import Form from './components/Form.vue'
  import Description from './components/Description.vue'

  export default {
    components: {
      appForm: Form,
      appDescription: Description
    }
  }
</script>

<style>
  html {
    height: 100%;
  }

  body {
    min-height: 100%;
    background-color: #70b6e2;
  }
</style>
