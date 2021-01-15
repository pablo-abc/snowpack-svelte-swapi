<script>
  import { MaterialApp, Container, Row, Col } from 'svelte-materialify';
  import NavBar from './components/NavBar.svelte'
  import PeopleList from './components/PeopleList.svelte'
  import Person from './components/Person.svelte'
</script>

<MaterialApp theme=light>
  <NavBar />
  <Row>
    <Col class="pa-0" cols={12} md={4} lg={3}>
      <PeopleList />
    </Col>
    <Col cols={12} md={8} lg={9}>
      <Person />
    </Col>
  </Row>
</MaterialApp>
