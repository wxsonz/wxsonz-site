<script>
    import MenuMeDot from "./MenuMeDot.svelte";
</script>

<div class="flex w-screen h-screen" id="playground">
    <div class="flex m-1 p-1 w-full h-3/4 border border-cyan-400 rounded-lg" id="playground_menu">
        <div class="flex w-1/6 flex-col m-1 border border-lime-400 rounded-lg" id="menu_me"></div> 
        <MenuMeDot />
    </div>
</div>