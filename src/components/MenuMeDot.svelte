<script lang=ts>
    // this menu will include
    // 2 flex row box
    // left
    // NULL, me, art, code and game as a menu
    // right
    // showing more of left menu if not NULL

    import { tweened } from 'svelte/motion';
    import { cubicOut, cubicInOut } from 'svelte/easing';

    const shlong = tweened(0, {
        duration: 500,
        easing:cubicOut
    });

    const shwap = tweened(0, {
        duration: 500,
        easing:cubicInOut
    });

    function handleMouseOut(){
        shlong.set(0);
        shwap.set(0);
    }

    function handleMouseIn(){
        shlong.set(69);
        shwap.set(1);
    }

</script>

<div class="flex flex-col m-1 border border-lime-400 bg-slate-900 rounded-lg" id="menu_me_dot">

    <div class="m-1 flex justify-center rounded-md bg-rose-500"
    on:mouseleave="{handleMouseOut}"
    on:mouseenter="{handleMouseIn}">
    hover
    </div>
</div>
<shlong class="flex m-1 w-4/6 border border-lime-400 bg-slate-900 rounded-lg" id="menu_me_dot_more" style="width:{$shlong}%; opacity: {$shwap};">
</shlong> 


<style>
    #menu_me_dot{
        width: 10%;
    }
</style>