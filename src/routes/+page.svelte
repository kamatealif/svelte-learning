<script lang='ts'>
    import Header from "./Header.svelte";
    let name = $state('')

    let status: "OPEN" | "CLOSED" = $state("OPEN")

    let full_name = $derived(name + " " + "Smith")

    // function toggle(){
    //     status = status === "OPEN" ? "CLOSED" : "OPEN";
    // }

    function onclick(){
        status = status === 'OPEN' ? 'CLOSED' : 'OPEN'
    }
</script>

<Header {name} fake_name="lallu"/>

<input type="text" bind:value={name} />


<p>The store is now {status}</p>
<button onclick={onclick}>Toggle Status</button>
<h2>{full_name}</h2>

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