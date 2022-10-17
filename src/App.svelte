<script>

  import Modal from './modal.svelte';
  let people = [
    { name: "yoshi", beltColor: "black", age: 25, id: 1 },
    { name: "Mario", beltColor: "orange", age: 45, id: 2 },
    { name: "luigi", beltColor: "brown", age: 35, id: 3 },
  ];

  const handleClick = (id) => {
    people = people.filter((person) => person.id != id);
  };
  let num = 5;
  let showModal = false

  const toggleModal = () =>{
    showModal = !showModal
  }
</script>

{#if num > 20}
  <p>plus grand que 20</p>
{/if}
<Modal {showModal} on:click={toggleModal}>


</Modal>
<main>
  <button on:click={toggleModal}>Open modal</button>
  {#each people as person (person.id)}
    <div>
      <h4>{person.name}</h4>
      {#if person.beltColor == "black"}
        <p><strong>Master Ninja</strong></p>
      {/if}
      <p>{person.age} year old {person.beltColor}</p>
      <button on:click={() => handleClick(person.id)}>delete</button>
    </div>
  {:else}
    <p>la liste est vide mon boug reste concentré</p>
  {/each}


  
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }


  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

