<script>
  import axios from 'axios';

  let facts = []
  
  const getFacts = async () => {
    const {data} = await axios.get('https://cat-fact.herokuapp.com/facts');
    facts = data.all.slice(0, 50)
  }
  
  const deleteFact= (id) => {
    facts = facts.filter(fact => fact._id !== id)
  }
</script>

<div>
  <h1>Cat Facts!</h1>
  {#await getFacts()}
    <p>Loading..</p>
  {:then}
    {#each facts as {text, upvotes, _id}}
      <div class="fact">
        <p>{text}</p>
        <p>Votes: {upvotes}</p>
        <button on:click={() => deleteFact(_id)}>Delete</button>
      </div>
    {/each}
  {:catch error}
    <p>Error: {error}</p>
  {/await} 
</div>

<style>
  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  .fact {
    margin-top: 2rem;
    padding: 2rem;
    box-shadow: 1px 1px 5px lightgrey;
    text-align: left;
  }
</style> 
