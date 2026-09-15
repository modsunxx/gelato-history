<script>
	import { resolve } from '$app/paths';
	// Import ไอคอนที่ต้องการจาก lucide-svelte
	import { Camera, IceCream, Citrus, Leaf, Coffee, ArrowLeft } from 'lucide-svelte';
</script>

<svelte:head>
	<title>Gelato History - แกลเลอรี</title>
</svelte:head>

<div class="space-y-12 pb-12">
	<!-- Hero Section (โทนสีม่วง/ชมพูคงเดิม) -->
	<header class="rounded-2xl bg-[#fcf0fa] px-6 py-12 text-center shadow-sm">
		<h1
			class="mb-4 flex flex-wrap items-center justify-center gap-3 text-4xl font-extrabold text-[#70386a] md:text-5xl"
		>
			<Camera size={48} /> แกลเลอรีของหวาน
		</h1>
		<p class="text-lg text-[#855a80] md:text-xl">
			รวมภาพความน่ากินของ Gelato รสชาติต่างๆ[cite: 11]
		</p>
	</header>

	<!-- จัด Section ให้อยู่กึ่งกลางเหมือนหน้าอื่นๆ -->
	<section class="mx-auto max-w-4xl text-center">
		<h2
			class="mb-8 inline-block border-b-4 border-[#e6b8df] pb-2 text-2xl font-bold text-[#4a3b32]"
		>
			หลากหลายรสชาติให้ลิ้มลอง[cite: 11]
		</h2>

		<!-- ปรับ Grid ให้เป็น 2 คอลัมน์ (2x2) เพื่อความสมดุลของ 4 รูป -->
		<div class="grid grid-cols-1 gap-8 sm:grid-cols-2">
			<!-- Mockup 1 -->
			<div
				class="flex aspect-square flex-col items-center justify-center rounded-xl border-4 border-dashed border-[#d897ce] bg-[#fdf5fc] p-4 text-center shadow-sm transition hover:scale-[1.02]"
			>
				<IceCream size={56} class="mb-4 text-[#d897ce]" />
				<span class="text-lg font-bold text-[#555]">Gelato รูปที่ 1</span>
				<span class="mt-1 text-sm text-gray-500">(รสช็อกโกแลต)[cite: 11]</span>
				<span class="mt-4 text-xs font-semibold text-[#70386a]"
					>📌 แนะนำขนาด 1:1 (เช่น 800x800 px)[cite: 11]</span
				>
			</div>

			<!-- Mockup 2 -->
			<div
				class="flex aspect-square flex-col items-center justify-center rounded-xl border-4 border-dashed border-[#d897ce] bg-[#fdf5fc] p-4 text-center shadow-sm transition hover:scale-[1.02]"
			>
				<Citrus size={56} class="mb-4 text-[#d897ce]" />
				<span class="text-lg font-bold text-[#555]">Gelato รูปที่ 2</span>
				<span class="mt-1 text-sm text-gray-500">(ซอร์เบต์เลมอน)[cite: 11]</span>
				<span class="mt-4 text-xs font-semibold text-[#70386a]"
					>📌 แนะนำขนาด 1:1 (เช่น 800x800 px)[cite: 11]</span
				>
			</div>

			<!-- Mockup 3 -->
			<div
				class="flex aspect-square flex-col items-center justify-center rounded-xl border-4 border-dashed border-[#d897ce] bg-[#fdf5fc] p-4 text-center shadow-sm transition hover:scale-[1.02]"
			>
				<Leaf size={56} class="mb-4 text-[#d897ce]" />
				<span class="text-lg font-bold text-[#555]">Gelato รูปที่ 3</span>
				<span class="mt-1 text-sm text-gray-500">(รสชาเขียว/พิสตาชิโอ)[cite: 11]</span>
				<span class="mt-4 text-xs font-semibold text-[#70386a]"
					>📌 แนะนำขนาด 1:1 (เช่น 800x800 px)[cite: 11]</span
				>
			</div>

			<!-- Mockup 4 -->
			<div
				class="flex aspect-square flex-col items-center justify-center rounded-xl border-4 border-dashed border-[#d897ce] bg-[#fdf5fc] p-4 text-center shadow-sm transition hover:scale-[1.02]"
			>
				<Coffee size={56} class="mb-4 text-[#d897ce]" />
				<span class="text-lg font-bold text-[#555]">Gelato รูปที่ 4</span>
				<span class="mt-1 text-sm text-gray-500">(รสกาแฟ)[cite: 11]</span>
				<span class="mt-4 text-xs font-semibold text-[#70386a]"
					>📌 แนะนำขนาด 1:1 (เช่น 800x800 px)[cite: 11]</span
				>
			</div>
		</div>
	</section>

	<!-- ปุ่มกลับหน้าแรกแบบเด่นๆ -->
	<div class="mt-12 text-center">
		<a
			href={resolve('/')}
			class="inline-flex items-center justify-center gap-3 rounded-xl bg-[#ffd1dc] px-8 py-4 text-lg font-bold text-[#5a3d31] shadow-md transition duration-300 hover:-translate-y-1 hover:bg-[#ffb6c1] hover:shadow-lg"
		>
			<ArrowLeft size={28} /> กลับหน้าแรก
		</a>
	</div>
</div>
