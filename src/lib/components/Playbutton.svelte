<script>
    let { onclick, isVisible } = $props();
</script>


<button class="playBtn" {onclick} >
    {isVisible ? "Faire monter la balle" : "Faire tomber la balle"}
</button>


<style>
    .playBtn {
        padding: 10px 20px;
        background-color: rgba(31, 31, 175, 0.8);
        border: none;
        border-radius: 5px;
        font-size: 1em;
        font-weight: 500;
        color: #fff;
        cursor: pointer;
        user-select: none;
    }

    .playBtn:hover {
        background-color: rgba(1, 1, 93, 0.8);
    }
</style>