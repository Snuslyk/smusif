<script lang="ts">
    import "$lib/assets/css/global.scss"
</script>

<title>Smusif</title>

<div class="content">
    <slot/>
</div>

<style lang="scss">
    .content {
      z-index: -100;
      background: black;
      min-height: 100vh;
      overflow: hidden;
    }
</style>