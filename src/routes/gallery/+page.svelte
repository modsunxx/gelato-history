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

		<!-- ปรับ Grid ให้เป็น 2 คอลัมน์ (2x2) ใส่รูปจริง -->
		<div class="grid grid-cols-1 gap-8 sm:grid-cols-2">
			<!-- รูปที่ 1: ช็อกโกแลต -->
			<div
				class="group flex flex-col items-center rounded-xl border border-[#fb7185]/30 bg-[#fff1f2] p-4 text-center shadow-sm transition duration-300 hover:-translate-y-1 hover:shadow-md hover:shadow-[#fb7185]/20"
			>
				<!-- อัปเดต: เปลี่ยนเป็น .PNG พิมพ์ใหญ่ ตามไฟล์จริง -->
				<img 
					src="/image/gallary/chocalate.PNG" 
					alt="Gelato รสช็อกโกแลต" 
					class="mb-4 aspect-square w-full rounded-lg object-cover shadow-sm transition duration-300 group-hover:scale-[1.02]" 
				/>
				<h3 class="flex items-center gap-2 text-xl font-bold text-[#9f1239]">
					<IceCream size={24} class="text-[#e11d48]" /> รสช็อกโกแลต
				</h3>
			</div>

			<!-- รูปที่ 2: ซอร์เบต์เลมอน -->
			<div
				class="group flex flex-col items-center rounded-xl border border-[#fb7185]/30 bg-[#fff1f2] p-4 text-center shadow-sm transition duration-300 hover:-translate-y-1 hover:shadow-md hover:shadow-[#fb7185]/20"
			>
				<!-- อัปเดต: ไฟล์นี้เป็น .png พิมพ์เล็ก ถูกแล้ว -->
				<img 
					src="/image/gallary/lemon.png" 
					alt="Gelato ซอร์เบต์เลมอน" 
					class="mb-4 aspect-square w-full rounded-lg object-cover shadow-sm transition duration-300 group-hover:scale-[1.02]" 
				/>
				<h3 class="flex items-center gap-2 text-xl font-bold text-[#9f1239]">
					<Citrus size={24} class="text-[#e11d48]" /> ซอร์เบต์เลมอน
				</h3>
			</div>

			<!-- รูปที่ 3: พิสตาชิโอ -->
			<div
				class="group flex flex-col items-center rounded-xl border border-[#fb7185]/30 bg-[#fff1f2] p-4 text-center shadow-sm transition duration-300 hover:-translate-y-1 hover:shadow-md hover:shadow-[#fb7185]/20"
			>
				<!-- อัปเดต: เปลี่ยนเป็น .PNG พิมพ์ใหญ่ ตามไฟล์จริง -->
				<img 
					src="/image/gallary/pitachio.PNG" 
					alt="Gelato รสพิสตาชิโอ" 
					class="mb-4 aspect-square w-full rounded-lg object-cover shadow-sm transition duration-300 group-hover:scale-[1.02]" 
				/>
				<h3 class="flex items-center gap-2 text-xl font-bold text-[#9f1239]">
					<Leaf size={24} class="text-[#e11d48]" /> รสพิสตาชิโอ
				</h3>
			</div>

			<!-- รูปที่ 4: กาแฟ -->
			<div
				class="group flex flex-col items-center rounded-xl border border-[#fb7185]/30 bg-[#fff1f2] p-4 text-center shadow-sm transition duration-300 hover:-translate-y-1 hover:shadow-md hover:shadow-[#fb7185]/20"
			>
				<!-- อัปเดต: เปลี่ยนเป็น .PNG พิมพ์ใหญ่ ตามไฟล์จริง -->
				<img 
					src="/image/gallary/coffee.PNG" 
					alt="Gelato รสกาแฟ" 
					class="mb-4 aspect-square w-full rounded-lg object-cover shadow-sm transition duration-300 group-hover:scale-[1.02]" 
				/>
				<h3 class="flex items-center gap-2 text-xl font-bold text-[#9f1239]">
					<Coffee size={24} class="text-[#e11d48]" /> รสกาแฟ
				</h3>
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