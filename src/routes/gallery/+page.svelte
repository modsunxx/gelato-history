<svelte:head>
	<title>Gelato History - แกลเลอรี</title>
</svelte:head>

<div class="space-y-12">
	<!-- Hero Section -->
	<header class="rounded-2xl bg-[#fcf0fa] px-6 py-12 text-center shadow-sm">
		<h1 class="mb-4 text-4xl font-extrabold text-[#70386a] md:text-5xl">แกลเลอรีของหวาน 📸</h1>
		<p class="text-lg text-[#855a80] md:text-xl">รวมภาพความน่ากินของ Gelato รสชาติต่างๆ</p>
	</header>

	<section>
		<h2
			class="mb-6 inline-block border-b-4 border-[#e6b8df] pb-2 text-2xl font-bold text-[#4a3b32]"
		>
			หลากหลายรสชาติให้ลิ้มลอง
		</h2>

		<!-- Grid สำหรับใส่รูปหลายๆ รูป -->
		<div class="grid grid-cols-1 gap-6 sm:grid-cols-2 md:grid-cols-3">
			<!-- Mockup 1 -->
			<div
				class="flex h-64 flex-col items-center justify-center rounded-xl border-4 border-dashed border-[#d897ce] bg-[#fdf5fc] p-4 text-center"
			>
				<span class="mb-2 text-4xl">🍦</span>
				<span class="font-bold text-[#555]">Gelato รูปที่ 1</span>
				<span class="mt-1 text-xs text-gray-500">(รสช็อกโกแลต)</span>
			</div>

			<!-- Mockup 2 -->
			<div
				class="flex h-64 flex-col items-center justify-center rounded-xl border-4 border-dashed border-[#d897ce] bg-[#fdf5fc] p-4 text-center"
			>
				<span class="mb-2 text-4xl">🍋</span>
				<span class="font-bold text-[#555]">Gelato รูปที่ 2</span>
				<span class="mt-1 text-xs text-gray-500">(ซอร์เบต์เลมอน)</span>
			</div>

			<!-- Mockup 3 -->
			<div
				class="flex h-64 flex-col items-center justify-center rounded-xl border-4 border-dashed border-[#d897ce] bg-[#fdf5fc] p-4 text-center"
			>
				<span class="mb-2 text-4xl">🍵</span>
				<span class="font-bold text-[#555]">Gelato รูปที่ 3</span>
				<span class="mt-1 text-xs text-gray-500">(รสชาเขียว/พิสตาชิโอ)</span>
			</div>

			<!-- Mockup 4 -->
			<div
				class="flex h-64 flex-col items-center justify-center rounded-xl border-4 border-dashed border-[#d897ce] bg-[#fdf5fc] p-4 text-center"
			>
				<span class="mb-2 text-4xl">☕</span>
				<span class="font-bold text-[#555]">Gelato รูปที่ 4</span>
				<span class="mt-1 text-xs text-gray-500">(รสกาแฟ)</span>
			</div>
		</div>
	</section>
</div>
