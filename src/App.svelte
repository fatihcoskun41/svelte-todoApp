<script>

import autoAnimate from '@formkit/auto-animate';


  let input = ""
  let data = []
  let search = ""
  
  // $:filter = data.filter(item=>item.title.includes(input))
  const add = ()=>{
    data = [...data,{id:Date.now(),title:input}]
    input = ""
  }
  const deleteFromArray = (index)=>{
    data.splice(index,1)
    data = data

  }
  const updateItem = (index)=>{

  }
  $:filter = data.filter(item=>item.title.includes(search.toString().toLowerCase()))
  

</script>

<main >
  <div class="d-flex flex-column align-items-center justify-content-center">
  <input bind:value={input} type="text" placeholder="Add" class="form-control w-25"/>
  {#if data.length>0}  <input bind:value={search} type="text" placeholder="Search" class="form-control w-25 my-3"/> {/if}
  <button on:click={add} class="btn btn-primary my-3">Add</button>

<ul class="list-group w-25 d-flex" use:autoAnimate>
  {#each filter as item,index}
  <div class="w-100 d-flex justify-content-between my-2">
    <li class="list-group-item w-100  ">
      {item.title}
    </li>
    <button class="btn btn-danger " on:click={()=>deleteFromArray(index)}>Sil</button>
  </div>
 
  

  
    
  {/each}
 

</ul>
{#if data.length>0} <div class="d-flex align-items-center justify-content-center">
  <p class="text-muted">{data.length} Showing</p>
</div>{/if}
{#if data.length==0}
<div class="alert alert-danger w-25">Empty List</div>
{/if}
</div>


</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }

  img {
    height: 16rem;
    width: 16rem;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4rem;
    font-weight: 100;
    line-height: 1.1;
    margin: 2rem auto;
    max-width: 14rem;
  }

  p {
    max-width: 14rem;
    margin: 1rem auto;
    line-height: 1.35;
  }

  @media (min-width: 480px) {
    h1 {
      max-width: none;
    }

    p {
      max-width: none;
    }
  }
</style>
