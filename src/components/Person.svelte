<script>
  import { selected } from '../store'
  import { List, Subheader } from 'svelte-materialify'
  import { PERSON } from '../queries'
  import client from '../request'
  import PersonRow from './PersonRow.svelte'

  $: personRequest = $selected ?
  client.request(PERSON, { id: $selected.id }) :
  Promise.resolve({})
</script>

<section>
  {#await personRequest}
    <p>Loading...</p>
  {:then { person }}
    {#if person}
      <List disabled>
        <Subheader>
          General Information
        </Subheader>
        <PersonRow>
          Eye Color
          <span slot="append">{person.eyeColor}</span>
        </PersonRow>
        <PersonRow>
          Hair Color
          <span slot="append">{person.hairColor}</span>
        </PersonRow>
        <PersonRow>
          Skin Color
          <span slot="append">{person.skinColor}</span>
        </PersonRow>
        <PersonRow>
          Birth Year
          <span slot="append">{person.birthYear}</span>
        </PersonRow>
        <Subheader class="mt-8">
          Vehicles
        </Subheader>
        {#each person.vehicleConnection.vehicles as vehicle}
          <PersonRow>
            {vehicle.name}
          </PersonRow>
        {/each}
      </List>
    {/if}
  {/await}
</section>

<style>
  section {
    margin-top: 64px;
  }
</style>
