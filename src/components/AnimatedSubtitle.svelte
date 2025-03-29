<script lang="ts">
    import { onMount } from "svelte";
    import { fly } from "svelte/transition";

    const list = ["Education", "Video Games", "Productivity", "Design"]
    let current = $state(0);
    let flipSwitch = $state(true);
    // let elem: HTMLElement | undefined = $state(undefined);

    onMount(() => {
        let interval = setInterval(() => {
            current+=1;
            flipSwitch = false;
            setTimeout(() => {
                flipSwitch = true;
            })
        }, 5500)

        return interval
    })

</script>

<p class="font-semibold text-2xl text-uppercase text-white/35 relative">
    {#if flipSwitch}
        <span in:fly={{y: 15}} class="absolute top-0">{list[current % list.length]}.</span>
    {/if}
    <span class="invisible">{list[current % list.length]}</span>
</p>
<!-- <div>
    <p class="font-semibold text-2xl text-uppercase text-white/35 relative">
        Where <span class="underline decoration-accent">creative-engineering</span> meets
        {#if flipSwitch}
            <span in:fly={{y: 15}} bind:this={elem} class="font-semibold text-2xl text-uppercase text-white/35 absolute top-0">{list[current % list.length]}</span>
        {/if}
        <span in:fly={{y: 20}} bind:this={elem} class="invisible">{list[current % list.length]}</span>
    </p>
</div> -->