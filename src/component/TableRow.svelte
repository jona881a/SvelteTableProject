<script>
  import Modal from "./Modal.svelte";

  import { createEventDispatcher } from 'svelte';

  export let stringToMatch;
  export let people;

  function searchForPeople(people, stringToMatch){
	if(stringToMatch){
		return people.filter(person => {
			return person.person.firstname.toLowerCase().includes(stringToMatch.toLowerCase())
          || person.person.lastname.toLowerCase().includes(stringToMatch.toLowerCase())
          || person.person.jobTitle.toLowerCase().includes(stringToMatch.toLowerCase());
		});
	} else {
		return people
	}
}

</script>

<tbody>
  {#each searchForPeople(people,stringToMatch) as person}
  <!--{#each people as person (person.id)}-->
  <tr>
      <!-- svelte-ignore a11y-missing-attribute -->
      <td><img src={person.person.mugshot} > </td>
      <td>{person.person.firstname}</td>
      <td>{person.person.lastname}</td>
      <td>{person.person.jobTitle}</td>
      <td>{person.person.phoneNumber}</td>
      <!--<Modal person={person}/>-->
  </tr>
  {/each}
</tbody>

<style>
  img {
    width: 50px;
    height: 50px;
  }

  td {
    padding: 12px 15px;
    text-align: left;
  }

  tr {
    border-bottom: 2px solid #dddddd;
  }

  tr:nth-child(even) {
    background-color: #f3f3f3;
  }

  tr:last-of-type {
    border-bottom: 5px solid #ff3e00;
  }

  tr:hover {
    cursor: pointer;
    background-color: #a0a0a0;
  }
</style>