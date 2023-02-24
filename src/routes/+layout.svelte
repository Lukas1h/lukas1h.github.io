<script>
    import NavBar from "./NavBar.svelte";
    export const prerender = true;
</script>

<NavBar> </NavBar>

<svelte:head>
    <link rel="stylesheet" href="/src/styles.css">
</svelte:head>


<slot></slot>

<style>

    :global(:root){
        --color100: #fff;   /*Card Backgrond*/
        --color200: #f2f2f2;   /*Alt-Background*/
        --color300: #f2f2f2;   /*Background*/
        --color400: #abc;   /*Comp Background*/
        --color500: #284b63;   /*Text*/
    } 
    
    



    @import url('https://css.gg/css');
</style>


    <!-- /* Theme One */
    @media DISABLED {
        :global(:root){
            --blue100: #e07a5f;   /*Card Backgrond*/
            --blue200: #f2cc8f;   /*Alt-Background*/
            --blue300: #f4f1de;   /*Background*/
            --blue400: #81b29a;   /*Comp Background*/
            --blue500: #3d405b;   /*Text*/
        }
    }

    /* Theme Blue */
    @media DISABLED {
        :global(:root){
            --blue100: #3b587d;
            --blue200: #355070;
            --blue300: #2e4561; 
            --blue400: #273b53;
            --blue500: #1a2737; 
        }
    } -->