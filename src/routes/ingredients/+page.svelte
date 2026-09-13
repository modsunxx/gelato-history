<script>
	import { resolve } from '$app/paths';
</script>

<svelte:head>
	<title>Gelato History - ส่วนผสมหลัก</title>
</svelte:head>

<div class="space-y-12 pb-12">
	<!-- Hero Section (โทนสีเขียวคงเดิม) -->
	<header class="rounded-2xl bg-[#e6f4ea] px-6 py-12 text-center shadow-sm">
		<h1 class="mb-4 text-4xl font-extrabold text-[#2d5a27] md:text-5xl">วัตถุดิบคุณภาพ 🍓</h1>
		<p class="text-lg text-[#556b50] md:text-xl">
			หัวใจสำคัญที่ทำให้ Gelato มีรสชาติเข้มข้นและเป็นเอกลักษณ์
		</p>
	</header>

	<!-- ส่วนเนื้อหาและรูปภาพ จัดกึ่งกลางเหมือนหน้า History -->
	<section class="mx-auto max-w-4xl text-center">
		<h2
			class="mb-6 inline-block border-b-4 border-[#a8d5ba] pb-2 text-2xl font-bold text-[#4a3b32]"
		>
			ส่วนผสมที่แตกต่างจากไอศกรีม
		</h2>
		<p class="mb-10 text-lg leading-relaxed text-gray-700 md:text-xl">
			เจลลาโต้เน้นการใช้นมสดมากกว่าครีม ทำให้มีปริมาณไขมันต่ำกว่าไอศกรีมทั่วไป (ประมาณ 4-8%
			เท่านั้น) นอกจากนี้ยังใช้วัตถุดิบสดใหม่จากธรรมชาติ เช่น ผลไม้ตามฤดูกาล
			ถั่วพรีเมียมอย่างพิสตาชิโอ หรือช็อกโกแลตแท้ โดยไม่พึ่งพาสารแต่งกลิ่นสังเคราะห์
		</p>

		<!-- กล่อง Mockup รูปภาพ (อัปเดตขนาดและสัดส่วน 16:9) -->
		<div
			class="mx-auto flex aspect-video w-full max-w-4xl flex-col items-center justify-center rounded-xl border-4 border-dashed border-[#87bba2] bg-[#f0f7f4] p-6 text-center shadow-sm"
		>
			<span class="mb-4 text-5xl">🥛🍓🥜</span>
			<span class="text-xl font-bold text-[#555]">[ ภาพประกอบ: วัตถุดิบทำ Gelato ]</span>
			<span class="mt-2 text-base font-semibold text-[#2d5a27]"
				>📌 ขนาดที่แนะนำ: 1280 x 720 px (สัดส่วน 16:9)</span
			>
			<span class="mt-2 text-sm text-gray-500"
				>(พื้นที่สำหรับทีมวาดรูป: วาดนมสด สตรอว์เบอร์รี ถั่ว หรือช็อกโกแลต)</span
			>
		</div>
	</section>

	<!-- ปุ่มกลับหน้าแรกแบบเด่นๆ -->
	<div class="mt-12 text-center">
		<a
			href={resolve('/')}
			class="inline-flex items-center justify-center gap-3 rounded-xl bg-[#ffd1dc] px-8 py-4 text-lg font-bold text-[#5a3d31] shadow-md transition duration-300 hover:-translate-y-1 hover:bg-[#ffb6c1] hover:shadow-lg"
		>
			<span class="text-2xl">⬅️</span> กลับหน้าแรก
		</a>
	</div>
</div>
