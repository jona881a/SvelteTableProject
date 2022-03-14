<script>
/*
import { createEventDispatcher } from 'svelte';

const dispatch = createEventDispatcher();
*/

export let person;
const modal = document.querySelector(".modal");
//const showModal = modal.style.display;

function openModal() {
  modal.style.display = "block";
}

function closeModal() {
  modal.style.display = "none";
}
  /*
  function getModal() {
    dispatch('message', {
      openModal : openModal()
    });
  }

  Vi kan måske bruge $: modal.display.style = "block"?

  */

  window.onclick = function(event) {
  if (event.target == modal) {
    modal.style.display = "none";
  }

}

</script>

<div class="modal">
  <div class="modal-content">
    <span></span>
    <span class="close" on:click = {closeModal}>&times;</span>
    <!--<p><img src={person.mugshot}></p> 
    <p>{person.firstname}</p> 
    <p>{person.lastname}</p> 
    <p>{person.jobTitle}</p> 
    <p>{person.phoneNumber}</p> -->
  </div>
</div>

<style>
  .modal {
    display: none;
    position: fixed;
    z-index: 1;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    overflow: auto;
    background-color: rgb(0,0,0);
    background-color: rgba(0,0,0,0.4);
  }

  .modal-content {
    background-color: #fefefe;
    margin: auto;
    padding: 20px;
    border: 1px solid #888;
    width: 80%;
  }

  .close {
    color: #aaaaaa;
    float: right;
    font-size: 28px;
    font-weight: bold;
  }

  .close:hover,
  .close:focus {
    color: #000;
    text-decoration: none;
    cursor: pointer;
  }

</style>