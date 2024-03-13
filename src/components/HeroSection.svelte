<script lang="ts">
	import { onDestroy, onMount } from 'svelte';
	import { slide } from 'svelte/transition';

	let titleTexts = ['cookbook', 'phone', 'video', 'tablet', 'laptop'];
	let titleTextColors = [
		// generate 5 text colors
		'text-indigo-500',
		'text-teal-500',
		'text-amber-600',
		'text-red-500',
		'text-green-600'
	];
	let currentTitleIndex = 0;

	onMount(() => {
		const interval = setInterval(() => {
			if (currentTitleIndex === titleTexts.length - 1) currentTitleIndex = 0;
			else currentTitleIndex++;
		}, 1250);

		onDestroy(() => {
			clearInterval(interval);
		});
	});
</script>

<div class="bg-white">
	<div class="relative isolate overflow-hidden bg-gradient-to-b from-indigo-100/20">
		<div
			class="mx-auto max-w-7xl pb-24 pt-10 sm:pb-32 lg:grid lg:grid-cols-2 lg:gap-x-8 lg:px-8 lg:py-40"
		>
			<div class="px-6 lg:px-0 lg:pt-4">
				<div class="mx-auto max-w-2xl">
					<div class="max-w-lg">
						<img
							class="h-11"
							src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=600"
							alt="Your Company"
						/>
						<div class="mt-24 sm:mt-32 lg:mt-16">
							<a href="#" class="inline-flex space-x-6">
								<span
									class="rounded-full bg-indigo-600/10 px-3 py-1 text-sm font-semibold leading-6 text-indigo-600 ring-1 ring-inset ring-indigo-600/10"
									>What's new</span
								>
								<span
									class="inline-flex items-center space-x-2 text-sm font-medium leading-6 text-gray-600"
								>
									<span>Join the waitlist</span>
									<svg
										class="h-5 w-5 text-gray-400"
										viewBox="0 0 20 20"
										fill="currentColor"
										aria-hidden="true"
									>
										<path
											fill-rule="evenodd"
											d="M7.21 14.77a.75.75 0 01.02-1.06L11.168 10 7.23 6.29a.75.75 0 111.04-1.08l4.5 4.25a.75.75 0 010 1.08l-4.5 4.25a.75.75 0 01-1.06-.02z"
											clip-rule="evenodd"
										/>
									</svg>
								</span>
							</a>
						</div>
						<h1 class="mt-10 text-4xl font-bold tracking-tight text-gray-900 sm:text-6xl">
							Cook anything without watching
							{#key currentTitleIndex}
								<h1 transition:slide class={titleTextColors[currentTitleIndex]}>
									{titleTexts[currentTitleIndex]}
								</h1>
							{/key}
						</h1>
						<p class="mt-6 text-lg leading-8 text-gray-600">
							Anim aute id magna aliqua ad ad non deserunt sunt. Qui irure qui lorem cupidatat
							commodo. Elit sunt amet fugiat veniam occaecat fugiat aliqua.
						</p>
						<div class="mt-10 flex items-center gap-x-6">
							<a
								href="#"
								class="rounded-md bg-indigo-600 px-3.5 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
								>Documentation</a
							>
							<a href="#" class="text-sm font-semibold leading-6 text-gray-900"
								>View on GitHub <span aria-hidden="true">→</span></a
							>
						</div>
					</div>
				</div>
			</div>
			<!-- random image grid, vertical -->
		</div>
		<div class="absolute inset-x-0 bottom-0 -z-10 h-24 bg-gradient-to-t from-white sm:h-32"></div>
	</div>
</div>
