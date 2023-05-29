<script>
	import logo from '$lib/assets/logo.svg';
	import { onMount } from 'svelte';
	let gridItems = ['FFF37A', '37393F', 'DCDCDC', '35363D', 'B1AAAA', '36383E'];
	let animate = false;
	import { fade } from 'svelte/transition';
	onMount(() => (animate = true));
</script>

<div class="w-screen h-screen bg-[#242529] text-white flex">
	<div
		class="SIDEBAR w-[20%] h-screen border-r border-solid border-[rgba(255,255,255,0.1)] relative"
	>
		<div class="LOGO w-full flex justify-center items-center py-8 sm:px-8 md:px-16 lg:px-32 gap-2">
			<img class="flex-grow" src={logo} alt="Project logo" />
			<div class="text-3xl">Wise</div>
		</div>
		<div class="PROFILE text-center px-32">
			<div class="rounded-full aspect-square overflow-hidden">
				<img
					class=""
					src="https://images.unsplash.com/photo-1500648767791-00dcc994a43e?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=687&q=80"
					alt=""
				/>
			</div>
			<div class="my-2 font-semibold">Lewis Carter</div>
			<div
				class="w-fit px-4 rounded-full mx-auto mb-4 border border-solid border-[rgba(255,255,255,0.2)]"
			>
				Edit
			</div>
		</div>
		<div class="LINKS" />
		<div class="absolute bottom-4 right-0 left-0">SWITCH</div>
	</div>
	<div class="MAIN w-[80%] p-8">
		<div class="grid grid-cols-3 w-full md:gap-12 lg:gap-24">
			{#if animate}
				{#each gridItems as item, i}
					<div
						in:fade={{ duration: 500, delay: i * 700 }}
						out:fade={{ duration: 500, delay: i * 700 }}
						class={`rounded-2xl aspect-square bg-[#${item}] hover:brightness-110 hover:scale-105 transition-all grid place-items-center`}
					>
						Hello
					</div>
				{/each}
			{/if}
		</div>
	</div>
</div>

<style>
	/* had to predefine tw styles here due to its perging of unused styles and the timeing of js compilation */
	.bg-\[\#FFF37A\] {
		background-color: #fff37a;
	}

	.bg-\[\#37393F\] {
		background-color: #37393f;
	}
	.bg-\[\#DCDCDC\] {
		background-color: #dcdcdc;
	}
	.bg-\[\#35363D\] {
		background-color: #35363d;
	}
	.bg-\[\#B1AAAA\] {
		background-color: #b1aaaa;
	}
	.bg-\[\#36383E\] {
		background-color: #36383e;
	}
</style>
