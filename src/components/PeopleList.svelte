<script>
  import { selected } from '../store'
  import { Divider, List, ListItem } from 'svelte-materialify'
  import { ALL_PEOPLE } from '../queries'
  import client from '../request'

  const peopleRequest = client.request(ALL_PEOPLE)
</script>

<section>
  {#await peopleRequest}
    <p>Loading....</p>
  {:then response}
    {#if response.allPeople?.people}
      <List>
        {#each response.allPeople.people as person}
          <ListItem on:click="{() => $selected = person}">
            {person.name}
            <span slot=subtitle>
              {person.species?.name || 'Human'}
            </span>
          </ListItem>
          <Divider />
        {/each}
    </List>
    {/if}
  {/await}
</section>

<style>
  section {
    padding-left: 16px;
    padding-top: 64px;
    border-right: 1px solid #AAA;
    overflow-y: scroll;
    height: 100vh;
  }
</style>
