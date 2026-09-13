<script>
	import { resolve } from '$app/paths';
</script>

<svelte:head>
	<title>Gelato History - กรรมวิธีทำ</title>
</svelte:head>

<div class="space-y-12 pb-12">
	<!-- Hero Section (โทนสีฟ้าคงเดิม) -->
	<header class="rounded-2xl bg-[#e6f0ff] px-6 py-12 text-center shadow-sm">
		<h1 class="mb-4 text-4xl font-extrabold text-[#2b4c7e] md:text-5xl">ศิลปะแห่งการปั่น 👨‍🍳</h1>
		<p class="text-lg text-[#5a7192] md:text-xl">เบื้องหลังเนื้อสัมผัสที่เหนียวนุ่มและละลายในปาก</p>
	</header>

	<!-- ส่วนเนื้อหาและรูปภาพ จัดกึ่งกลางเหมือนหน้า History -->
	<section class="mx-auto max-w-4xl text-center">
		<h2
			class="mb-6 inline-block border-b-4 border-[#a3c2f0] pb-2 text-2xl font-bold text-[#4a3b32]"
		>
			ความลับอยู่ที่อากาศและอุณหภูมิ
		</h2>
		<p class="mb-10 text-lg leading-relaxed text-gray-700 md:text-xl">
			กระบวนการปั่นเจลลาโต้จะใช้ความเร็วที่ช้ากว่าไอศกรีมมาก ทำให้มีอากาศแทรกซึมเข้าไป (Overrun)
			เพียงแค่ 20-30% เนื้อที่ได้จึงมีความแน่น หนึบ และเข้มข้น
			นอกจากนี้เจลลาโต้ยังถูกเสิร์ฟในอุณหภูมิที่อุ่นกว่าไอศกรีมเล็กน้อย
			ทำให้ต่อมรับรสของเราสัมผัสถึงความอร่อยได้เต็มที่ตั้งแต่คำแรก
		</p>

		<!-- กล่อง Mockup รูปภาพ (อัปเดตขนาดและสัดส่วน 16:9) -->
		<div
			class="mx-auto flex aspect-video w-full max-w-4xl flex-col items-center justify-center rounded-xl border-4 border-dashed border-[#7a9eb1] bg-[#f0f4f8] p-6 text-center shadow-sm"
		>
			<span class="mb-4 text-5xl">⚙️🍧</span>
			<span class="text-xl font-bold text-[#555]">[ ภาพประกอบ: เครื่องปั่น หรือ ขั้นตอนการทำ ]</span
			>
			<span class="mt-2 text-base font-semibold text-[#2b4c7e]"
				>📌 ขนาดที่แนะนำ: 1280 x 720 px (สัดส่วน 16:9)</span
			>
			<span class="mt-2 text-sm text-gray-500"
				>(พื้นที่สำหรับทีมวาดรูป: วาดเครื่องทำเจลลาโต้ หรือเชฟกำลังตักเจลลาโต้ด้วยไม้พาย)</span
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
