<script>
  import { AppBar } from 'svelte-materialify'
</script>

<AppBar class="black theme--dark" height={64} fixed={true} style="width: 100%;">
  <h1 slot=title>Ravn Star Wars Registry</h1>
</AppBar>

<style>
  h1 {
    font-size: 1.25rem;
    font-weight: bold;
  }
</style>
