<script lang='ts'>
    let { name,
        fake_name = null
     }:{
        name: string;
        fake_name?: string | null
    } = $props();
</script>

<h1>
    Hello {name }
</h1>
<h2>
    {name.replaceAll("l","r")}
</h2>
<p>Fake name : {fake_name}</p>

<style>

</style>