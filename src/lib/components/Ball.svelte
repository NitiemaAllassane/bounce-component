<script>
    import { bounceOut, backOut } from "svelte/easing";

    let { color, width, height } = $props();

    function bounceTransition(node, { delay = 0, duration}) {
        return {
            delay,
            duration,
            css: (t) => {
                const eased = bounceOut(t);

                return `
                    transform: translateY(${(1 - eased) * -450}px);
                `
            }
        }
    }

    function outTransition(node, { delay = 0, duration}) {
        return {
            delay,
            duration,
            css: (u) => {
                const eased = backOut(u);

                return `
                    transform: translateY(${(1 - eased) * -450}px);
                `
            }
        }
    }
</script>


<div 
    class="ball"
    in:bounceTransition={{duration: 650}}
    out:outTransition={{ duration: 300}}
    style="background-color: {color}; width: {width}; height: {height} "
></div>

<style>
    .ball {
        /* width: 100px;
        height: 100px; */
        /* background-color: lightseagreen; */
        border-radius: 50%;
        border: 2px solid #000;
        position: absolute;
        bottom: 0;
    }
</style>