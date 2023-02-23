
<script>
    import Card from "./Card.svelte";

    let scrollVal = "0"
    let scroller;

    const scrollFunc = () =>{
        scrollVal = scroller.scrollLeft

        console.log("sroll",scrollVal,scroller.offsetHeight)
    }
</script>

<div class="root" style="--scrollVal:{scrollVal};">
    <div class="bg">
        <div class="first-div">
        </div>
        <div class="sec-div">
        </div>
    </div>
    <h1 class="hero-text">
        Lorem Ipsum
    </h1>
    <div class="com-div">
        <div class="com-header">
            <div></div>
            <div></div>
            <div></div>
        </div>
        <div style="padding: 20px;">
            <h1>Hello</h1>
            <p>Ex labore enim quis sunt id Lorem. Ad nulla et dolor aliquip officia amet aliquip occaecat minim est eu. Do quis amet nulla eu culpa dolor. Aliqua aute et cillum sunt fugiat non dolore Lorem. Voluptate et amet mollit proident amet commodo reprehenderit ex consequat commodo ex incididunt aute eiusmod. </p>
        </div>
    </div>
    <h2 style="text-align:center; margin:auto; margin-top:40px; max-width:90vw; ">Check out some of my articles!</h2>
    <div class="slider" on:scroll={scrollFunc} bind:this={scroller}>
        <section class="" style='--size:{scrollVal};'>
            <Card class="Card" style='--size:{scrollVal};'></Card>
        </section>
         <section class="" style='--size:{scrollVal};'>
            <Card class="Card" style='--size:{scrollVal};'></Card>
        </section>
         <section style='--size:{scrollVal};'>
            <Card class="Card" style='--size:{scrollVal};'></Card>
        </section>
    </div>
</div>

<div class="sizediv" style='--size:{scrollVal};'></div>

<style>
	.slider {
        perspective: 1px;
		scroll-snap-type: x mandatory;	
		display: flex;
		-webkit-overflow-scrolling: touch;
		overflow-x: scroll;
        padding: 0px;
        /* padding-left: 10vw; */
	}
    Card {
        transform:translateZ(calc( var(--size) * -1px / 600 ));
    }
    
	section {
        
		min-width: 80vw;
		height: 100vh;
		scroll-snap-align: center;
		position: relative;
        margin: auto;
        padding: auto;
        
	}



    .bg {
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        z-index: -1;
    }

    .first-div {
        width: 100%;
        height: 600px;
        background-color: var(--blue200);
        clip-path: polygon(0 0, 100% 0, 100% 520px, 0% 100%);
    }
    .sec-div {
        margin-top: 400px;
        width: 100%;
        height: 100vh;
        background-color: var(--blue200);
        clip-path: polygon(0 80px, 100% 0, 100% 100%, 0% 100%);
    }
    
    .hero-text {
        text-align: center;
        font-size: 2.5rem;
        margin: 100px auto;

    }
    
    .com-div {
        margin: 20px;
        background-color: var(--blue400);
        border-radius: 16px;
        overflow: hidden;
    }

    .com-div h1 {
        margin-bottom: 20px;
        color: var(--blue500);
    }

    .com-div p {
        font-size: 1.2rem;
    }

    .com-header {
        height: 30px;
        background-color: var(--blue500);
        display: flex;
        align-items: center;
        justify-content: left;
        padding-left: 8px;
    }

    .com-header  div {
        height: 10px;
        width: 10px;
        border-radius: 20px;
        background-color: var(--blue100);
        margin: 0px 2px;  
    }
</style>

