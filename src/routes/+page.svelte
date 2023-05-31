<script>
	import logo from '$lib/assets/logo.svg';
	import { onMount } from 'svelte';
	let gridItems = ['FFF37A', '37393F', 'DCDCDC', '35363D', 'B1AAAA', '36383E'];
	let animate = false;
	import { fade } from 'svelte/transition';
	onMount(() => (animate = true));
	import Icon from '@iconify/svelte';
	let sidebarOpen = true;
	let toggleSidebar = () => {
		sidebarOpen = !sidebarOpen;
	};
	let darkMode = true;
</script>

<div class=" min-h-screen bg-[#242529] text-white flex">
	<div
		class={`SIDEBAR ${
			sidebarOpen ? 'w-[20%]' : 'w-[72px]'
		} p-3 h-screen border-r border-solid border-[rgba(255,255,255,0.1)] transition-all relative`}
	>
		<div
			class="flex justify-end text-3xl"
			on:keyup={(e) => {
				if (e.key === 'Enter') {
					toggleSidebar();
				}
			}}
			on:click={toggleSidebar}
		>
			<Icon icon="material-symbols:menu" class="cursor-pointer" />
		</div>

		<div class={`${sidebarOpen ? 'opacity-100' : 'opacity-0'}`}>
			<div class="LOGO flex justify-center items-center py-8 sm:px-8 md:px-16 lg:px-32 gap-2">
				<img class="flex-grow" src={logo} alt="Project logo" />
				<div class="text-3xl">Wise</div>
			</div>
			<div class="PROFILE text-center px-32 mb-8">
				<div class="rounded-full aspect-square overflow-hidden">
					<img
						class=""
						src="https://images.unsplash.com/photo-1500648767791-00dcc994a43e?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=687&q=80"
						alt=""
					/>
				</div>
				<div class="my-2 font-semibold">Lewis Carter</div>
				<div
					class="w-fit px-4 rounded-full mx-auto mb-4 border border-solid border-[rgba(255,255,255,0.2)] hover:bg-[rgba(255,255,255,0.25)] cursor-pointer"
				>
					Edit
				</div>
			</div>
		</div>
		<div class="LINKS">
			<div
				class={'flex justify-start items-center gap-3 p-2 transition-all cursor-pointer rounded hover:bg-[rgba(255,255,255,0.25)]'}
			>
				<div class={`aspect-square  p-2`}>
					<Icon icon="ic:round-dashboard" />
				</div>
				{#if sidebarOpen}
					<div>Dashboard</div>
				{/if}
			</div>
			<div
				class={'flex justify-start items-center gap-3 p-2 transition-all cursor-pointer rounded hover:bg-[rgba(255,255,255,0.25)]'}
			>
				<div class={`aspect-square p-2`}>
					<Icon icon="fluent-emoji-high-contrast:page-facing-up" />
				</div>
				{#if sidebarOpen}
					<div>Activity</div>
				{/if}
			</div>
			<div
				class={'flex justify-start items-center gap-3 p-2 transition-all cursor-pointer rounded hover:bg-[rgba(255,255,255,0.25)]'}
			>
				<div class={`aspect-square  p-2`}>
					<Icon icon="ph:calendar-fill" />
				</div>
				{#if sidebarOpen}
					<div>Schedule</div>
				{/if}
			</div>
			<div
				class={'flex justify-start items-center gap-3 p-2 transition-all cursor-pointer rounded hover:bg-[rgba(255,255,255,0.25)]'}
			>
				<div class={`aspect-square p-2`}>
					<Icon icon="basil:settings-adjust-solid" />
				</div>
				{#if sidebarOpen}
					<div>Settings</div>
				{/if}
			</div>
		</div>
		<div class="absolute bottom-4 right-0 left-0">
			<div class={`${sidebarOpen ? 'opacity-100' : 'opacity-0'}`}>
				<!-- svelte-ignore a11y-click-events-have-key-events -->
				<div class="switchContainer relative" on:click={() => (darkMode = !darkMode)}>
					<div
						class="h-12 w-[150px] mx-auto rounded-full bg-[rgba(255,255,255,0.2)] border border-solid border-grey flex items-center"
					>
						<div class="flex mx-3 justify-between w-full">
							<div><Icon icon="bi:sun-fill" /></div>
							<div><Icon icon="teenyicons:moon-solid" /></div>
						</div>
						<div
							class={`absolute ml-1 h-10 aspect-square bg-[#FFF47A] rounded-full transition-all ${
								darkMode ? 'translate-x-[100px]' : null
							}`}
						/>
					</div>
				</div>
			</div>
		</div>
	</div>
	<div class={`MAIN ${sidebarOpen ? 'w-[80%]' : 'calcWidth'} p-8`}>
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
	.calcWidth {
		width: calc(100vw - 64px);
	}
</style>
