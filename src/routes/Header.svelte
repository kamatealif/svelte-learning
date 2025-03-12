<script lang='ts'>
    let { name }:{
        name: string;
    } = $props();
</script>

<h1>
    Hello {name }
</h1>
<h2>
    {name.replace("l","r")}
</h2>

<style>

</style>