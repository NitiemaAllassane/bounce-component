<script>
    import { fly, slide } from "svelte/transition";
    import { bounceOut } from "svelte/easing";
    import Playbutton from "./lib/components/Playbutton.svelte";

    let isVisible = $state(false);

    function bounceTransition(node, { delay = 0, duration}) {
        return {
            delay,
            duration,
            css: (t) => {
                const eased = bounceOut(t);

                return `
                    transform: translateY(${(1 - eased) * -180}px);
                `
            }
        }
    }
</script>

<main>
    <div class="container">
        <Playbutton onclick={() => isVisible = !isVisible} {isVisible} />
        <section>
            {#if isVisible}
                <div 
                    class="ball"
                    in:bounceTransition={{duration: 450}}
                    out:fly={{y: -180, duration: 200}}
                >
                </div>
            {/if}
        </section>
    </div>
</main>


<style>
    main {
        min-height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    .container {
        max-width: 1080px;
        margin: 0 auto;
        display: flex;
        align-items: flex-end;
        gap: 2em;
    }

    section {
        position: relative;
        width: 450px;
        height: 450px;
        border: 2px solid #333;
        border-radius: 10px;
        display: flex;
        justify-content: center;
        overflow: hidden;
    }

    .ball {
        width: 120px;
        height: 120px;
        background-color: lightseagreen;
        border-radius: 50%;
        position: absolute;
        bottom: 0;
    }

    @media  (max-width: 40rem) {
        .container {
            flex-direction: column-reverse;
            max-width: 90%;
        }

        section {
            max-width: 100%;
        }
    }
</style>