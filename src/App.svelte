<script>
    import Ball from "./lib/components/Ball.svelte";
    import Playbutton from "./lib/components/Playbutton.svelte";

    let ballColors = ['red', 'orange', 'yellow', 'green', 'blue', 'indigo', 'violet','white', 'black'];
    let actuelColor = $state(ballColors[0]);

    let ballTall = $state(120);

    let isVisible = $state(false);

    
</script>

<main>
    <div class="container">
        <div class="wrapper">
            <section>
                <form action="#" onsubmit={ (e) => e.preventDefault()}>
                    <h2>Parametres</h2>

                    <article class="colors-section">
                        <label for="colors">Choisissez une couleur</label>
                        <div class="colors">
                            {#each ballColors as color }
                                <button 
                                    class="color" 
                                    aria-label={color}
                                    style="background-color: {color} "
                                    onclick={() => actuelColor = color}
                                >
                                </button>
                            {/each}
                        </div>
                    </article>

                    <article class="tall-section">
                        <label for="talls">Modifier la taille</label>
                        <p>{ballTall}px</p>
                        <input 
                            type="range" 
                            name="talls" 
                            id="talls" 
                            min="64"
                            max="300"
                            bind:value={ballTall}
                       
                        >
                    </article>
                </form>
            </section>
            <section class="box-section" >
                {#if isVisible}
                    <Ball 
                        color={actuelColor}
                        width="{ballTall}px"
                        height="{ballTall}px"
                     />
                {/if}
            </section>
        </div>
        <Playbutton onclick={() => isVisible = !isVisible} {isVisible} />
    </div>
</main>

<footer>
    <p>&copy2025; Nitiema Allassane: Tous droit reservé</p>
</footer>


<style>
    main {
        min-height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin: 3rem 0;
    }
    .container {
        max-width: 1080px;
        margin: 0 auto;
        /* background-color:  ; */
    }

    .wrapper {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        gap: 2rem;
        margin-bottom: 2em;
    }
    .box-section {
        position: relative;
        width: 450px;
        height: 450px;
        border: 2px solid #333;
        border-radius: 10px;
        display: flex;
        justify-content: center;
        overflow: hidden;
    }


    /* Form style */

    form {
        background-color: #dde3eb;
        width: 100%;
        height: 100%;
        padding: 2em;
        border-radius: 5px;
        color: #333;
    }

    article {
        margin-bottom: 1rem;
    }

    h2 {
        font-size: 2.2em;
        font-weight: 500;
        margin-bottom: 1em;
    }

    label {
        font-size: 1.3em;
        font-weight: 400;
        line-height: 1.5;
        margin-bottom: 1.5em;
    }

    .tall-section label {
        display: block;
        margin-bottom: 0.5em;
    }
    .tall-section input {
        width: 100%;
        height: 30px;
    }

    .colors {
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        /* justify-content: center; */
        gap: 1em;
        padding: 1em;
        /* background-color: #fff; */
    }
    
    .color {
        width: 44px;
        height: 44px;
        border-radius: 50%;
        border: none;
        cursor: pointer;
        transition: transform 100ms ease-out;
    }

    .color:hover {
        transform: translateY(-10px);
    }

    .color:focus {
        border: 2px solid #000;
    }


    footer {
        background-color: #000;
        padding: 2em 0;
        color: #fff;
        text-align: center;
    }


    @media  (max-width: 1080px) {
        .container {
            max-width: 90%;
        }
    }

    @media  (max-width: 48rem) {
        .container {
            max-width: 90%;
        }
        .wrapper {
            display: flex;
            flex-direction: column;
        }

        .box-section {
            width: 100%;
        }
    }
</style>