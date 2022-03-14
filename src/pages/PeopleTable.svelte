<script>
import TableHead from '../component/TableHead.svelte';
import TableRow from '../component/TableRow.svelte';

import { faker } from '@faker-js/faker';
import Modal from '../component/Modal.svelte';

let people = [];
let person;
let selectedSortingCondition;
let stringToMatch;
let pageSize;

for(let i = 0; i <= 50; i++) {
  person = {
    mugshot: faker.image.avatar(),
    firstname: faker.name.firstName(),
    lastname: faker.name.lastName(),
    jobTitle: faker.name.jobTitle(),
    phoneNumber: faker.phone.phoneNumber()
  }

  people.push({id: i, person});
}

function sortBy() {

  people.sort(function(second,first) {
    const secondPerson = Object.entries(second.person).find(entry => entry[0] === selectedSortingCondition);
    const firstPerson = Object.entries(first.person).find(entry => entry[0] === selectedSortingCondition);

    if(secondPerson < firstPerson) {
      console.log("-1",secondPerson,firstPerson);
      return -1;
    } else if(secondPerson > firstPerson) {
      console.log("1",secondPerson,firstPerson);
      return 1;
    } else {
      console.log(0,secondPerson, firstPerson);
      return 0;
    }

  });
  people = [...people]; //Updates the array which is enough to change the table data dynamically
}

function pageination() {
  
}

</script>
<select bind:value={pageSize} on:change={pageination}>
  <option value={5}>5</option>
  <option value={10}>10</option>
  <option value={15}>15</option>
  <option value={25}>25</option>
  <option value={50}>50</option>
  <option value={100}>100</option>
</select>


<select bind:value={selectedSortingCondition} on:change={sortBy}>
  <option>Sort by</option>
  <option value={"firstname"}>Firstname</option>
  <option value={"lastname"}>Lastname</option>
  <option value={"jobTitle"}>Job Title</option>
</select>

<input type="text" bind:value={stringToMatch} placeholder="Search...">
<!--<button on:click={filterBy}>Filter</button>-->

<table class="content-table" id="peopletable">
  <TableHead keys = {Object.keys(person)}/>
  <TableRow people = {people} stringToMatch={stringToMatch}/>
</table>

<Modal/>

<style>
  .content-table {
    border-collapse: collapse;
    font-size: 0.9em;
    margin: 0 auto;
    overflow: hidden;
    border-radius: 10px 10px 0 0;
    box-shadow: 0 0 20px rgba(0,0,0,0.15);
  }
</style>