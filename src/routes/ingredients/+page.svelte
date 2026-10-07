<script>
	import { resolve } from '$app/paths';
	// Import icons from lucide-svelte
	import { Cherry, Milk, ArrowLeft } from 'lucide-svelte';
</script>

<svelte:head>
	<title>Gelato History - ส่วนผสมหลัก</title>
</svelte:head>

<div class="space-y-12 pb-12">
	<!-- Hero Section (พื้นหลังสีชมพูอ่อน ตัดด้วยไอคอนสีเขียวมิ้นต์) -->
	<header class="rounded-2xl bg-[#fff1f2] px-6 py-12 text-center shadow-sm">
		<h1
			class="mb-4 flex flex-wrap items-center justify-center gap-3 text-4xl font-extrabold text-[#be123c] md:text-5xl"
		>
			<Cherry size={48} class="text-[#10b981]" /> วัตถุดิบคุณภาพ
		</h1>
		<p class="text-lg text-[#9f1239] md:text-xl">
			หัวใจสำคัญที่ทำให้ Gelato มีรสชาติเข้มข้นและเป็นเอกลักษณ์
		</p>
	</header>

	<!-- Section with content and images -->
	<section class="mx-auto max-w-4xl text-center">
		<!-- เส้นใต้สีเขียวมิ้นต์เพื่อให้โดดเด่นออกมาจากข้อความสีชมพูแดง -->
		<h2
			class="mb-6 inline-block border-b-4 border-[#10b981] pb-2 text-2xl font-bold text-[#881337]"
		>
			ส่วนผสมที่แตกต่างจากไอศกรีม
		</h2>
		<p class="mb-10 text-lg leading-relaxed text-gray-700 md:text-xl">
			เจลลาโต้เน้นการใช้นมสดมากกว่าครีม ทำให้มีปริมาณไขมันต่ำกว่าไอศกรีมทั่วไป (ประมาณ 4-8%
			เท่านั้น) นอกจากนี้ยังใช้วัตถุดิบสดใหม่จากธรรมชาติ เช่น ผลไม้ตามฤดูกาล
			ถั่วพรีเมียมอย่างพิสตาชิโอ หรือช็อกโกแลตแท้ โดยไม่พึ่งพาสารแต่งกลิ่นสังเคราะห์
		</p>

		<!-- Mockup image box (โทนสีเขียวมิ้นต์ ตัดด้วยไอคอนสีแดงอมชมพู) -->
		<div
			class="mx-auto flex aspect-video w-full max-w-4xl flex-col items-center justify-center rounded-xl border-4 border-dashed border-[#34d399] bg-[#ecfdf5] p-6 text-center shadow-sm"
		>
			<div class="mb-4 flex gap-4 text-[#be123c]">
				<Milk size={56} />
				<Cherry size={56} />
			</div>
			<span class="text-xl font-bold text-[#065f46]">[ ภาพประกอบ: วัตถุดิบทำ Gelato ]</span>
			<span class="mt-2 text-base font-semibold text-[#047857]"
				>📌 ขนาดที่แนะนำ: 1280 x 720 px (สัดส่วน 16:9)</span
			>
			<span class="mt-2 text-sm text-gray-500"
				>(พื้นที่สำหรับทีมวาดรูป: วาดนมสด สตรอว์เบอร์รี ถั่ว หรือช็อกโกแลต)</span
			>
		</div>
	</section>

	<!-- Back to home page button (ปุ่มสีชมพูพร้อมไอคอนสีเขียวตอน hover) -->
	<div class="mt-12 text-center">
		<a
			href={resolve('/')}
			class="group inline-flex items-center justify-center gap-3 rounded-xl bg-[#fecdd3] px-8 py-4 text-lg font-bold text-[#881337] shadow-md transition duration-300 hover:-translate-y-1 hover:bg-[#fda4af] hover:shadow-lg hover:shadow-[#fda4af]/30"
		>
			<ArrowLeft size={28} class="text-[#10b981] transition group-hover:scale-110" /> กลับหน้าแรก
		</a>
	</div>
</div>