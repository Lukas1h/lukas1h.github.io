<script>
    import { slide } from "./trans";
    let drawerVisable = false;

    function toggelDrawer(){
        drawerVisable = !drawerVisable
    }
</script>


<div class="header">
    <h1>Home</h1>
    <button on:click={toggelDrawer}>
        <img class="menu-icon" src="/icons/menu.svg" alt="">
    </button>
</div>

{#if drawerVisable}
    <div transition:slide="{{axis:"x"}}" class="drawer">
        <div>
            <div class="header">
                <h1>Menu</h1>
            </div>
            <h2><a href="/">Home</a></h2>
            <h2><a href="/">About</a></h2>
            <h2><a href="/">Blog</a></h2>
            <h2><a href="/">Projects</a></h2>
        </div>

    </div>
{/if}


<style>
    .drawer {
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        background-color: white;
        z-index: 25;
        box-shadow: rgb(0 0 0 / 8%) 2px 0;
    }
    @media (min-width: 500px) {
        .drawer{
            width:300px;
            left: auto;
            right: auto;
        }
    
    }


    .drawer > div {
        display: flex;
        justify-content: center;
        flex-direction: column;
        text-align: left;
    }
    .drawer  h2 {
        margin: 8px 0px;
        text-align: center;
    }


    .drawer a {
        transition: font-size 0.1s ease-in-out;
    }
    .drawer a:hover {
        font-size: 1.1rem;
    }

    

    h1{
        transition: transform 0.1s linear;
    }
    h1:hover{
        transform: scale(1.1);
    }



    button {
        z-index: 30;
        background: none;
        border: none;
        transition: transform 0.1s linear;
    }
    button:hover {
        transform: scale(1.2);
        border-radius: 4px;
    }

    button:active{
        filter:blur(100);
        opacity: 30%;
        transform: scale(1);
    }

    .header {
        z-index: 20;
        display: flex;
        padding: 10px 20px;
        justify-content: space-between;
        align-items: center;
        background-color: white;
        box-shadow: rgb(0 0 0 / 8%) 0 2px;
    }

</style>