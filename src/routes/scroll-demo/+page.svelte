<script>
  //IMPORTS
  import { onMount } from 'svelte';
  import * as Threlte from "@threlte/core";
  import * as Three from "three";
  import * as Utils from "three/src/math/MathUtils";
  import * as Extra from "@threlte/extras";
  import {useGltf} from "@threlte/extras";
  import mousePosition from "../mouse";
  import { fade,scale, slide } from 'svelte/transition';
  import Card from "../Card.svelte"

  // Helper Functions
  const between = function(num,a, b) {
    var min = Math.min.apply(Math, [a, b]),
      max = Math.max.apply(Math, [a, b]);
    return num >= min && num < max;
  };
  const lerp = (x, y, a) => x * (1 - a) + y * a;
  const clamp = (a, min = 0, max = 1) => Math.min(max, Math.max(min, a));
  const invlerp = (x, y, a) => clamp((a - x) / (y - x));
  const range = (x1, y1, x2, y2, a) => lerp(x2, y2, invlerp(x1, y1, a));

  //Lets
  let screenWidth, screenHeight;
  let scrollVal;
  let height;
  $: percent = invlerp(0,height - screenHeight+57,scrollVal) * 100


</script>
<div bind:clientHeight={height}>

<div class="cont">


<div class="content">

  {#if between(percent,0,2)}
      <h1 in:scale out:scale class="header-text">👋 Hey, I'm Lukas</h1>
      <h2 transition:scale={{delay:100}} class="header-text" style="top: 110px;">I like to build websites</h2>
  {/if}
  
  {#if between(percent,2,10)}
      <div in:scale out:scale class="card1">
        <h1>Hello</h1>
        <p>Enim pariatur eu elit amet nulla. Culpa laboris exercitation irure culpa sunt ullamco labore nostrud. Sit amet ullamco nostrud fugiat Lorem sint laborum anim velit velit incididunt ipsum qui.</p>
      </div>
  {/if}
  {#if between(percent,10,18)}
    <div in:scale out:scale class="card2">
      <h1>Hello</h1>
      <p>Enim pariatur eu elit amet nulla. Culpa laboris exercitation irure culpa sunt ullamco labore nostrud. Sit amet ullamco nostrud fugiat Lorem sint laborum anim velit velit incididunt ipsum qui.</p>
    </div>
  {/if}
  


  <p class="scroll-info">Scroll Percent: {percent.toFixed(2)}</p>
</div>


<div class="scene" >
  <Threlte.Canvas >
    <!-- Camera -->
    <Threlte.PerspectiveCamera position={{ x: 0, y: 0, z: 20 }} fov={60}>
    </Threlte.PerspectiveCamera>

    <!-- Lights the scene equally -->
    <Threlte.AmbientLight color="white" intensity={1} />

    <!-- Light that casts a shadow -->
    <Threlte.DirectionalLight
      color="white"
      intensity={10}
      position={{ x: 20, y: 20 }}
      target={{x:0,y:0,z:0}}
    />
    
    <Extra.Environment
      files={"models/hdr.jpg"}
      isBackground={false}
    />

    <Threlte.Object3D
      position={{
        x: (function() {
              let magicOffScreenNumber = 4

              if(between(percent,0,2)){
                return 0
              }

              if(between(percent,2,6)){
                return Math.min(lerp(0,magicOffScreenNumber,(percent/10 - 2/10) * 4), magicOffScreenNumber)
              }

              if(between(percent,6,8)){
                return magicOffScreenNumber
              }

              if(between(percent,8,10)){
                return -Math.min(lerp(-magicOffScreenNumber,magicOffScreenNumber,(percent/10 - 8/10) * 6), magicOffScreenNumber)
              }
              
              if(between(percent,10,16)){
                return -magicOffScreenNumber
              }

              if(between(percent,16,100)){
                return -Math.min(lerp(magicOffScreenNumber,20,(percent/10 - 16/10) * 4), 20)
              }
              if(between(percent,20,100)){
                return -5
              }

          }())
      }}
    >
      <Extra.GLTF 
        scale={{ x: 15, y: 15, z: 15 }} 
        rotation={{y:180 * Utils.DEG2RAD}}
        url="models/iphone13.glb" 
        enabled=false
      />
      <Extra.HTML
            position={{z:0.35}}
            rotation={{}}
            transform
            
        >
            <div class="notch"></div>

            {#if true}
              <div class="frame bg">
              </div>
            {:else}
              <iframe title="Hello" src="http://localhost:5173" frameBorder="0" width="270px" height="580px" class="frame" style="background-color:white;" >
              </iframe>
            {/if}
      </Extra.HTML>
    </Threlte.Object3D>
  </Threlte.Canvas>
</div>
<div style="height: 2000px;"></div>
</div>
</div>
<svelte:window
  bind:innerHeight={screenHeight}
  bind:innerWidth={screenWidth}
  bind:scrollY={scrollVal}
/>

<style>
  .hed {  
    
  }

  .hl {
    border: solid;
    border-width: 0px;
    border-bottom-width:2px;
    border-color: palevioletred;
  }


  .com-div {
      /* From https://css.glass */
      background: rgba(94, 94, 94, 0.19);
      border-radius: 16px;
      box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
      backdrop-filter: blur(3px);
      -webkit-backdrop-filter: blur(3px);
      border-radius: 16px;
      overflow: hidden;
  }

  .com-div h1 {
      margin-bottom: 20px;
      color: white;
      transition: font-size 0.1s ease-in-out;
  }

  .com-div p {
      font-size: 1.2rem;
  }

  .com-header {
      height: 30px;
      background-color: rgba(0, 0, 0, 0.3);
      display: flex;
      align-items: center;
      justify-content: left;
      padding-left: 8px;
  }

  .com-header  div {
      height: 10px;
      width: 10px;
      border-radius: 20px;
      background-color: white;
      margin: 0px 2px;  
  }

  .content > * {
    position: fixed;
    float: left;
    color: white;
    z-index: 20;
  }

  .header-text {
    top: 70px;
    left: 0;
    right: 0;
    text-align: center;
    color: white;
  }

  .card1 {
    width: 200px;
    height: 400px;
    text-align: left;
    padding: 20px;
    margin: auto;
    left: 50%;
    margin-left:-50vw;
    transform:translateY(100px);
  }
  



  .card2 {
    width: 200px;
    height: 400px;
    text-align: right;
    padding: 20px;
    right: 50%;
    margin-right:-50vw;
    transform:translateY(100px);
  }

  .scroll-info {
    top:0px;
    left: 0;
    right: 0;
    color: black;
    font-weight: bold;
    text-align: right;
    position:fixed;
    
    
  }





  .notch {
    position: absolute;
    top: 0;
    left: 50%;
    width: 120px;
    height: 20px;
    background-color: black;
    border-radius: 0 0 28px 28px;
    transform: translateX(-50%);
    z-index: 20;

  }

  .frame {
    width: 270px;
    height: 577px;
    
    border-radius: 40px;
    background-color: white;


  }

  .bg {
    background-image:  linear-gradient(0deg, rgba(4,114,199,0.3) 0%, rgba(205,24,69,0.3) 100%), radial-gradient(circle, #4d4d4d 1.2px, rgba(0, 0, 0, 0) 1px), radial-gradient(hsl(220 14% 20%), hsl(220 20% 10%));
    background-size: auto,40px 40px,auto;
  }


  .scene {
    width: 100%;
    height: 100vh;
    position: sticky;
    top: 0;
    background: none;
    


     z-index: 0;
  }

  .cont {
    background-image:  linear-gradient(0deg, rgba(4,114,199,0.3) 0%, rgba(205,24,69,0.3) 100%), radial-gradient(circle, #4d4d4d 1.2px, rgba(0, 0, 0, 0) 1px), radial-gradient(hsl(220 14% 20%), hsl(220 20% 10%));
    background-size: auto,40px 40px,auto;
  }
</style>
