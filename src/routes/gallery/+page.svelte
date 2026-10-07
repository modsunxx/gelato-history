<script>
	import { resolve } from '$app/paths';
	// Import ไอคอนที่ต้องการจาก lucide-svelte
	import { Camera, IceCream, Citrus, Leaf, Coffee, ArrowLeft } from 'lucide-svelte';
</script>

<svelte:head>
	<title>Gelato History - แกลเลอรี</title>
</svelte:head>

<div class="space-y-12 pb-12">
	<!-- Hero Section (โทนสีม่วงอ่อน) -->
	<header class="rounded-2xl bg-[#faf5ff] px-6 py-12 text-center shadow-sm">
		<h1
			class="mb-4 flex flex-wrap items-center justify-center gap-3 text-4xl font-extrabold text-[#7e22ce] md:text-5xl"
		>
			<Camera size={48} /> แกลเลอรีของหวาน
		</h1>
		<p class="text-lg text-[#9333ea] md:text-xl">
			รวมภาพความน่ากินของ Gelato รสชาติต่างๆ
		</p>
	</header>

	<!-- จัด Section ให้อยู่กึ่งกลางเหมือนหน้าอื่นๆ -->
	<section class="mx-auto max-w-4xl text-center">
		<!-- หัวข้อใช้โทนสีชมพูเข้ม -->
		<h2
			class="mb-8 inline-block border-b-4 border-[#f472b6] pb-2 text-2xl font-bold text-[#be185d]"
		>
			หลากหลายรสชาติให้ลิ้มลอง
		</h2>

		<!-- ปรับ Grid ให้เป็น 2 คอลัมน์ (2x2) เพื่อความสมดุลของ 4 รูป -->
		<div class="grid grid-cols-1 gap-8 sm:grid-cols-2">
			<!-- Mockup 1 (ใช้โทนสีชมพูอมแดง) -->
			<div
				class="flex aspect-square flex-col items-center justify-center rounded-xl border-4 border-dashed border-[#fb7185] bg-[#fff1f2] p-4 text-center shadow-sm transition hover:scale-[1.02]"
			>
				<IceCream size={56} class="mb-4 text-[#e11d48]" />
				<span class="text-lg font-bold text-[#555]">Gelato รูปที่ 1</span>
				<span class="mt-1 text-sm text-gray-500">(รสช็อกโกแลต)</span>
				<span class="mt-4 text-xs font-semibold text-[#9f1239]"
					>📌 แนะนำขนาด 1:1 (เช่น 800x800 px)</span
				>
			</div>

			<!-- Mockup 2 -->
			<div
				class="flex aspect-square flex-col items-center justify-center rounded-xl border-4 border-dashed border-[#fb7185] bg-[#fff1f2] p-4 text-center shadow-sm transition hover:scale-[1.02]"
			>
				<Citrus size={56} class="mb-4 text-[#e11d48]" />
				<span class="text-lg font-bold text-[#555]">Gelato รูปที่ 2</span>
				<span class="mt-1 text-sm text-gray-500">(ซอร์เบต์เลมอน)</span>
				<span class="mt-4 text-xs font-semibold text-[#9f1239]"
					>📌 แนะนำขนาด 1:1 (เช่น 800x800 px)</span
				>
			</div>

			<!-- Mockup 3 -->
			<div
				class="flex aspect-square flex-col items-center justify-center rounded-xl border-4 border-dashed border-[#fb7185] bg-[#fff1f2] p-4 text-center shadow-sm transition hover:scale-[1.02]"
			>
				<Leaf size={56} class="mb-4 text-[#e11d48]" />
				<span class="text-lg font-bold text-[#555]">Gelato รูปที่ 3</span>
				<span class="mt-1 text-sm text-gray-500">(รสชาเขียว/พิสตาชิโอ)</span>
				<span class="mt-4 text-xs font-semibold text-[#9f1239]"
					>📌 แนะนำขนาด 1:1 (เช่น 800x800 px)</span
				>
			</div>

			<!-- Mockup 4 -->
			<div
				class="flex aspect-square flex-col items-center justify-center rounded-xl border-4 border-dashed border-[#fb7185] bg-[#fff1f2] p-4 text-center shadow-sm transition hover:scale-[1.02]"
			>
				<Coffee size={56} class="mb-4 text-[#e11d48]" />
				<span class="text-lg font-bold text-[#555]">Gelato รูปที่ 4</span>
				<span class="mt-1 text-sm text-gray-500">(รสกาแฟ)</span>
				<span class="mt-4 text-xs font-semibold text-[#9f1239]"
					>📌 แนะนำขนาด 1:1 (เช่น 800x800 px)</span
				>
			</div>
		</div>
	</section>

	<!-- ปุ่มกลับหน้าแรกแบบเด่นๆ (ใช้โทนสีชมพู) -->
	<div class="mt-12 text-center">
		<a
			href={resolve('/')}
			class="inline-flex items-center justify-center gap-3 rounded-xl bg-[#fbcfe8] px-8 py-4 text-lg font-bold text-[#831843] shadow-md transition duration-300 hover:-translate-y-1 hover:bg-[#f9a8d4] hover:shadow-lg"
		>
			<ArrowLeft size={28} /> กลับหน้าแรก
		</a>
	</div>
</div>