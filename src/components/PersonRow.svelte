<script>
  import { ListItem, Divider } from 'svelte-materialify'
</script>

<ListItem>
  <span class="default grey-text text-darken-1">
    <slot />
  </span>
  <span slot="append" class="append black-text">
    <slot name="append" />
  </span>
</ListItem>
<Divider />

<style>
  span {
    font-weight: bold;
  }

  .append {
    text-transform: capitalize;
  }
</style>
