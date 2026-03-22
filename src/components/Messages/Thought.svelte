<script lang="ts">
    import Flex from '$components/Flex.svelte';
    import Svg from '$components/Svg.svelte';

    const { thought } = $props();

    let isOpen = $state(false);
    let css = $derived.by(() => (isOpen ? 'rounded-xl w-full' : 'rounded-full'));

    function toggle() {
        isOpen = isOpen ? false : true;
    }
</script>

<Flex class={`border-light flex-col items-start ${css} mb-4 border p-2 px-3`}>
    <Flex onclick={toggle} class="hover:cursor-pointer">
        <Svg name="Lightbulb" class="text-dark h-4 w-4" />

        <Flex class="gap-2">
            <p class="flex items-center px-3 py-1 text-sm">
                <span class="text-yellow">Model Thoughts</span>
            </p>
        </Flex>
    </Flex>

    {#if isOpen}
        <div
            class="border-light mt-4 mb-1 w-full overflow-x-scroll rounded-md border p-2
            px-4 whitespace-pre-wrap"
        >
            {thought}
        </div>
    {/if}
</Flex>
