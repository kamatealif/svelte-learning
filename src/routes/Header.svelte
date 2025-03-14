<script>
</script>

<header>
    <nav>
        <ul>
            <li><a href="/">Home</a></li>
            <li><a href="/about">About</a></li>
            <li><a href="/contact">Contact</a></li>
        </ul>
    </nav>
</header>


<style>
    header{
        background-color:chocolate;
        display: flex;
        justify-content:end;
        align-items: center;
    }
    nav{
        padding: 0px 10px;
    }
    ul{
        display:flex;
        justify-content: center;
        align-items: center;
        list-style-type: none;
        
    }

    li > a{
        margin-left: 16px;
        text-decoration: none;
        font-family: Helvetica, sans-serif;
        font-weight: bold;
        color:white;

    }
    li > a:hover{
        color:black;
        transition: color 0.3s ease-in-out;
    }
</style>