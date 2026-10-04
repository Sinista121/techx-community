<main class="pb-40">
	<section class="relative h-screen">
		<img
			srcset="hero-large3.jpg 600w, hero-large3.jpg 1200w, hero-large3.jpg 2000w"
			alt="Crisp background"
			class="absolute h-full w-full object-cover"
		/>
		<div class="absolute h-full w-full bg-black/60"></div>

		<div class="absolute inset-0 z-10 flex flex-col p-2 md:p-6">
			<div class="flex h-full w-full flex-col items-center justify-center gap-10 text-center">
				<h1 class="text-2xl md:text-5xl font-bold uppercase max-w-4xl title">
					Welcome to our community
					<br />
					<p class="text-2xl normal-case text-[#e8e8e8] mt-2 text-shadow-sm">
						Where students collaborate, build <br/> and inovate new technology
					</p>
				</h1>
				<div class="flex gap-2">
					<a
						href="/#about"
						class="hidden md:flex cursor-pointer rounded border border-[#848484] p-0.5"
					>
						<div
							class="rounded bg-white/90 text-black text-sm px-10 py-2 font-bold uppercase transition-all hover:opacity-80"
						>
							Let's Go
						</div>
					</a>
					<a
						href="/#about"
						class="hidden md:flex cursor-pointer rounded border border-[#848484] p-0.5"
					>
						<div
							class="rounded bg-[#1E2027] text-white text-sm px-10 py-2 font-bold uppercase transition-all hover:opacity-80"
						>
							View Components
						</div>
					</a>
				</div>
			</div>
			<div class="flex absolute bottom-6 left-2 md:left-6 flex-col items-center gap-10">
				<div class="h-10 w-1 bg-white"></div>
				<img
					src="tech-vector.svg"
					alt="tech visual"
					class="h-60 w-auto object-contain text-white"
				/>
			</div>
			<div class="flex absolute top-20 right-2 md:right-6 flex-col items-center gap-5">
				<img
					src="tech-vector.svg"
					alt="tech visual"
					class="h-60 w-auto object-contain text-white"
				/>
				<div class="h-10 w-1 bg-white"></div>
			</div>
		</div>
	</section>
	<section id="about" class="w-full">
		<div class="grid h-20 grid-cols-12">
			<div class="border-b border-white/10"></div>
			<div class="col-span-10 border-x border-b border-white/10 border-b-white/30"></div>
			<div class="border-b border-white/10"></div>
		</div>
		<div class="grid grid-cols-12">
			<div></div>
			<div
				class="col-span-10 flex flex-col gap-10 border-x border-b border-white/30 p-6 md:p-14 text-center"
			>
				<h1 class="text-2xl md:text-5xl font-black">About Us</h1>
				<p class="md:mx-30 text-sm md:text-xl text-balance text-white/90">
					We are a lively tech community where passion meets play. Instead of just grinding through
					code alone, we team up to explore new tech, join high-energy game jams, conduct casual
					code evenings and more! It is all about experimenting, making mistakes, and building cool
					things together without the pressure of a formal workplace. Whether you are a seasoned
					developer or just writing your first lines of code, you will find a welcoming spot here.
					We swap ideas, solve tricky bugs over pizza, and cheer each other on. Come hang out, spark
					your creativity, and make some awesome friends who love tech just as much as you do.
				</p>
			</div>
			<div></div>
		</div>
		<div class="grid h-20 grid-cols-12">
			<div class="border-t border-white/10"></div>
			<div class="col-span-10 border-x border-t border-white/10 border-b-white/30"></div>
			<div class="border-t border-white/10"></div>
		</div>
	</section>
</main>
