<script>
	import FilterIcon from '~icons/mdi/filter';

	let projects = $state([
		{
			id: 1,
			title: 'Project Title 01',
			desc: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
			user: 'Robert',
			image: 'https://picsum.photos/800/400',
			userImage:
				'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSV_MlO3koV2GayVLm8an7l8W_Y3syrPmJHZQ2tX_Ev8w&s=10',
			tag: 'Web Development'
		},
		{
			id: 2,
			title: 'Project Title 02',
			desc: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
			user: 'USER',
			image: 'https://picsum.photos/900/400',
			userImage:
				'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSV_MlO3koV2GayVLm8an7l8W_Y3syrPmJHZQ2tX_Ev8w&s=10',
			tag: 'Design'
		},
		{
			id: 3,
			title: 'Project Title 03',
			desc: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
			user: 'USER',
			image: 'https://picsum.photos/1000/400',
			userImage:
				'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSV_MlO3koV2GayVLm8an7l8W_Y3syrPmJHZQ2tX_Ev8w&s=10',
			tag: 'Engineering'
		},
		{
			id: 4,
			title: 'Project Title 04',
			desc: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
			user: 'USER',
			image: 'https://picsum.photos/1200/400',
			userImage:
				'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSV_MlO3koV2GayVLm8an7l8W_Y3syrPmJHZQ2tX_Ev8w&s=10',
			tag: 'Data Science'
		},
		{
			id: 5,
			title: 'Project Title 05',
			desc: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
			user: 'USER',
			image: 'https://picsum.photos/1400/400',
			userImage:
				'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSV_MlO3koV2GayVLm8an7l8W_Y3syrPmJHZQ2tX_Ev8w&s=10',
			tag: 'Web Development'
		},
		{
			id: 6,
			title: 'Project Title 06',
			desc: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
			user: 'USER',
			image: 'https://picsum.photos/1600/400',
			userImage:
				'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSV_MlO3koV2GayVLm8an7l8W_Y3syrPmJHZQ2tX_Ev8w&s=10',
			tag: 'Design'
		}
	]);

	let searchQuery = $state('');
	let isFilterOpen = $state(false);
	let activeFilter = $state('All');
	const filterOptions = ['All', 'Web Development', 'Design', 'Engineering', 'Data Science'];

	function toggleFilter() {
		isFilterOpen = !isFilterOpen;
	}

	/**
	 * @param {string} option
	 */
	function selectFilter(option) {
		activeFilter = option;
		isFilterOpen = false;
	}

	let filteredProjects = $derived(
		projects.filter((project) => {
			const matchesSearch =
				project.title.toLowerCase().includes(searchQuery.toLowerCase()) ||
				project.desc.toLowerCase().includes(searchQuery.toLowerCase());
			const matchesFilter = activeFilter === 'All' || project.tag === activeFilter;
			return matchesSearch && matchesFilter;
		})
	);
</script>

<main
	class="relative flex min-h-screen max-w-full flex-col bg-[#111215] custom-scrollbar overflow-x-hidden"
>
	<div class="fixed inset-0 z-0 h-screen w-full pointer-events-none">
		<img
			srcset="bg-small.jpg 600w, bg-medium.jpg 1200w, hero-large3.jpg 2000w"
			alt="Crisp background"
			class="absolute h-full w-full object-cover"
		/>
		<div class="absolute h-full w-full bg-black/60"></div>
	</div>

	<div class="pointer-events-none fixed inset-0 z-30">
		<div class="hidden md:flex absolute bottom-6 left-6 flex-col items-center gap-10">
			<div class="h-10 w-1 bg-white"></div>
			<img src="tech-vector.svg" alt="tech visual" class="h-60 w-auto object-contain" />
		</div>
		<div class="hidden md:flex absolute top-30 right-6 flex-col items-center gap-10">
			<img src="tech-vector.svg" alt="tech visual" class="h-60 w-auto object-contain" />
			<div class="h-30 w-1 bg-white"></div>
		</div>
	</div>

	<section
		class="relative z-10 mx-auto flex w-full max-w-5xl flex-col gap-10 pt-40 pb-16 px-4 md:px-0 mb-40"
	>
		<div class="flex flex-col items-center justify-center gap-3 text-center">
			<h1 class="text-4xl font-black tracking-widest text-white uppercase md:text-5xl">EXPO</h1>
			<span
				class="rounded-full border border-white/90 bg-[#1a1c20]/40 px-4 py-1.5 text-xs font-bold tracking-[0.2em] text-white uppercase backdrop-blur-sm"
			>
				UNIVERSITY PROJECT DATABASE
			</span>
			<h2 class="mt-1 text-sm font-medium tracking-wide text-white/90">
				Find projects made by other students in our community
			</h2>
		</div>
		<div class="flex w-full flex-col items-stretch gap-3 sm:flex-row">
			<div class="relative flex-1">
				<input
					type="text"
					bind:value={searchQuery}
					placeholder="Search Project..."
					class="w-full rounded-lg border border-black/90 bg-[#1a1c20] px-4 py-3 text-xs tracking-wide text-white placeholder-white/60 transition-all duration-200 focus:border-white focus:ring-1 focus:ring-white focus:outline-none"
				/>
			</div>
			<div class="relative">
				<button
					onclick={toggleFilter}
					class="w-full sm:w-auto cursor-pointer flex items-center justify-center gap-2 rounded-lg bg-white/90 px-5 py-3 text-xs font-extrabold tracking-widest text-black shadow-lg shadow-white/5 transition-all duration-300 hover:bg-white/80"
				>
					<FilterIcon class="text-xs" />
					<span>{activeFilter.toUpperCase()}</span>
				</button>
				{#if isFilterOpen}
					<div
						class="absolute right-0 mt-2 z-40 w-56 rounded-lg border border-[#2d3139] bg-[#1a1c20] p-1 shadow-xl backdrop-blur-md"
					>
						{#each filterOptions as option, id (id)}
							<button
								onclick={() => selectFilter(option)}
								class="cursor-pointer w-full text-left rounded-md px-3 py-2 text-xs tracking-wider uppercase transition-colors duration-150 {activeFilter ===
								option
									? 'bg-white text-black font-bold'
									: 'text-white/70 hover:bg-white/5 hover:text-white'}"
							>
								{option}
							</button>
						{/each}
					</div>
				{/if}
			</div>
		</div>

		{#if filteredProjects.length > 0}
			<div class="w-full grid grid-cols-1 gap-5 md:grid-cols-2 lg:grid-cols-3">
				{#each filteredProjects as project (project.id)}
					<div
						class="group flex flex-col overflow-hidden rounded-xl border border-[#2d3139] bg-[#1a1c20]/90 shadow-md backdrop-blur-sm transition-all duration-300 hover:-translate-y-1 hover:border-white"
					>
						<div
							class="relative m-3 flex h-40 items-center justify-center overflow-hidden rounded-lg border border-dashed border-[#475569] bg-[#24272e] transition-colors group-hover:border-white/50"
						>
							<img
								src={project.image}
								alt={project.title}
								class="absolute inset-0 h-full w-full object-cover opacity-40 transition-opacity duration-300 group-hover:opacity-60"
							/>

							<div
								class="absolute inset-0 bg-linear-to-br from-white/5 to-transparent opacity-0 transition-opacity duration-300 group-hover:opacity-100"
							></div>
							<span
								class="absolute top-2.5 right-2.5 rounded border border-white/20 bg-black/60 px-2 py-0.5 text-xs font-extrabold tracking-wider text-white"
							>
								{project.tag}
							</span>
						</div>

						<div class="flex flex-1 flex-col px-3 pb-4">
							<h3
								class="mb-1 text-base font-bold text-white transition-colors duration-200 group-hover:text-white/90"
							>
								{project.title}
							</h3>
							<p class="mb-4 flex-1 text-xs leading-relaxed text-[#94a3b8]">
								{project.desc}
							</p>
							<div class="flex items-center">
								<div class="h-px w-full bg-white/10"></div>
								<div
									class="flex items-center gap-5 rounded-full border border-white/10 bg-white/5 p-1 text-[9px] font-bold tracking-wider text-white"
								>
									<img src={project.userImage} alt="" class="rounded-full h-10 w-12 opacity-80" />
								</div>
							</div>
						</div>
					</div>
				{/each}
			</div>
		{:else}
			<div
				class="flex flex-col items-center justify-center text-center py-20 border border-dashed border-[#2d3139] rounded-xl bg-[#1a1c20]/40 backdrop-blur-sm"
			>
				<span class="text-2xl mb-2">🔍</span>
				<h3 class="text-sm font-bold text-white uppercase tracking-wider">No matching projects</h3>
				<p class="text-xs text-[#94a3b8] mt-1">
					Try adjusting your keywords or filtering parameters
				</p>
			</div>
		{/if}
	</section>
</main>
