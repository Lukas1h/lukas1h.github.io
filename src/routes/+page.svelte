
<script>
    let m = { x: 0, y: 0 };
    let innerWidth
    let root
    let container

	function handleMousemove(event) {
		m.x = event.screenX;
		m.y = event.screendY;
        console.log(innerWidth)
        root.style.backgroundPositionX = "0px,0px," + (-event.offsetX/innerWidth*8 + "px");
        root.style.backgroundPositionY = "0px,0px," + (-event.offsetY/innerWidth*8 + "px");

        container.style.left = (event.offsetX/innerWidth*6 + "px");
        container.style.top = (event.offsetY/innerWidth*6 + 60 + "px");

        console.log(-event.offsetX/innerWidth*0.1)
	}




    const webSkills = [
        {
            name:"SvelteKit",
            logo:'https://upload.vectorlogo.zone/logos/sveltetechnology/images/fc06c9b6-d01c-4e1f-82be-557ad5f65d6e.svg'
        },
        {
            name:"JavaScript",
            logo:'https://upload.vectorlogo.zone/logos/javascript/images/239ec8a4-163e-4792-83b6-3f6d96911757.svg'
        },
        {
            name:"HTML",
            logo:'https://www.vectorlogo.zone/logos/w3_html5/w3_html5-icon.svg'
        },
        {
            name:"CSS",
            logo:'https://www.vectorlogo.zone/logos/w3_css/w3_css-icon.svg'
        },
        {
            name:"Abobe Illustrator",
            logo:"https://www.vectorlogo.zone/logos/adobe_illustrator/adobe_illustrator-icon.svg"
        }
        
    ]

    
</script>

<svelte:body style="background-color: red;"></svelte:body>

<svelte:window on:mousemove={handleMousemove} bind:innerWidth={innerWidth}></svelte:window>


<div class="root" bind:this={root} >
    <div class="con" bind:this={container}>
        
        <div class="hero">
            <h1>
                <span role="img" class="emoji-img" aria-label="hand wave">🖐️</span> Hey there!
            </h1>
            <h2>
                I'm <strong>Lukas</strong>, a 15-year-old software developer with 3 years of experience.
            </h2>
            <div class="card">
                <h3>
                    I have experience in:
                </h3>
                <h5>Web Technolegs</h5>
                {#each webSkills as skill}
                     <div class="skill-list">
                        <img src={skill.logo} alt="">
                        <h4>
                            {skill.name}
                        </h4>
                    </div>
                {/each}
                <h5>Web Technolegs</h5>
                {#each webSkills as skill}
                     <div class="skill-list">
                        <img src={skill.logo} alt="">
                        <h4>
                            {skill.name}
                        </h4>
                    </div>
                {/each}
            </div>
            
            
            <!-- <ul>
                <li><p class="list-image">🚀</p><p class="list-text">SvelteKit</p></li>
                <li><p class="list-image">💻</p><p class="list-text">C/C++</p></li>
                <li><p class="list-image">🌐</p><p class="list-text">JavaScript</p></li>
                <li><p class="list-image">📄</p><p class="list-text">HTML</p></li>
                <li><p class="list-image">🎨</p><p class="list-text">CSS</p></li>
                <li><p class="list-image">🎨🖌️</p><p class="list-text">Design</p></li>
            </ul> -->

        </div>
    </div>    
</div>


<style>
    .skill-list {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin: 20px;

    }
    .skill-list > img {
        width: 40px;
        height: 40px;
    }

    .skill-list > h4 {
        color: white;
        font-size: larger;
        background: -webkit-linear-gradient(0deg, rgba(188, 57, 186, 0.7) -50%, rgba(21, 81, 154,0.7) 200%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
    }

    .card h5 {
        color: #4d4d4d;
        padding: 20px;
        padding-bottom: 8px;
        text-align: center;
        width: 100%;
        font-size: 16px;

    }

    .hero .card {
        width: min(400px,80vw);
        margin: 20vh auto;

            
        border: 2px solid rgba(165,46,201,0.3);
        border-radius: 20px;
        backdrop-filter: blur(10px);
        padding: 20px;
        animation: glow 1.5s infinite ease-in-out;

    }
    
    @keyframes glow {
    0% {
        box-shadow: 0 0 19px 13px rgba(181,110,64,0.1),
            0 0 30px 23px rgba(165,46,201,0.2);
    }
    50% {
        box-shadow: 0 0 19px 8px rgba(181,110,64,0.1),
            0 0 30px 18px rgba(165,46,201,0.2);
    }
    100% {
        box-shadow: 0 0 19px 13px rgba(181,110,64,0.1),
            0 0 30px 23px rgba(165,46,201,0.2);
    }
    }

    .hero{
        margin-top: 30vh;
    }

    

    h1, h2,h3, h1 span, h2 strong {
        text-align: center;
        margin: auto;
        max-width: 90vw;
        color: white;
    }

    .con{
        position: absolute;
        top: 60px;
        left: 0;
        width: 100%;
        height: 100%;
    }

    .root {
        background-image:  
            radial-gradient(
                min(100vw,800px) min(100vw,800px) at left top,
                rgba(51, 248, 255, 0.2) 0%,
                rgba(255, 255, 255, 0) 100%
            ),
            linear-gradient(0deg, rgba(4,114,199,0) 0%, rgba(205,24,69,0) 100%), 
            radial-gradient(circle, #4d4d4d 1.2px, rgba(0, 0, 0, 0) 1px), 
            radial-gradient(hsl(220 14% 20%), hsl(220 20% 10%));


        background-size: 
            auto,
            auto,
            40px 40px,
            auto;

        background-attachment: scroll,fixed,scroll,fixed;
        
        height: 400vh;
        padding: 8px;
        margin: var(--posx) px;
        /* animation: Animation 3s ease infinite; */
    }

    @keyframes Animation { 
        0% {
            background-position: 0rem 0rem;
        }
        100% {
            background-position: -1rem 1rem;
        }
    }
</style>

