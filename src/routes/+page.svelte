<script lang='ts'>
    import Header from "./Header.svelte";
    let name = $state('Scott')

    let status: "OPEN" | "CLOSED" = $state("OPEN")

    // function toggle(){
    //     status = status === "OPEN" ? "CLOSED" : "OPEN";
    // }

    function onclick(){
        status = status === 'OPEN' ? 'CLOSED' : 'OPEN'
    }
</script>

<Header {name}/>

<input type="text" bind:value={name} />


<p>The store is now {status}</p>
<button onclick={onclick}>Toggle Status</button>

<!-- COOL STUFF -->
<!-- <button {onclick}>Toggle Status</button>
-->

<button
    onclick={()=>{
        status = status === 'OPEN' ? 'CLOSED' : 'OPEN';
    }}
>
    Toggle Status /- inline function
</button>


<style>
    input{
        padding: 4px 8px;
    }
</style>