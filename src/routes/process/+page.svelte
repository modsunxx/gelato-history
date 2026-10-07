<script>
	import { resolve } from '$app/paths';
	// Import ไอคอนที่ต้องการจาก lucide-svelte
	import { ChefHat, Settings, ArrowLeft, ThermometerSnowflake } from 'lucide-svelte';
</script>

<svelte:head>
	<title>Gelato History - กรรมวิธีทำ</title>
</svelte:head>

<div class="space-y-12 pb-12">
	<!-- Hero Section (Monochromatic โทนฟ้าสว่าง) -->
	<header class="rounded-2xl bg-[#f0f9ff] px-6 py-12 text-center shadow-sm">
		<h1
			class="mb-4 flex flex-wrap items-center justify-center gap-3 text-4xl font-extrabold text-[#0284c7] md:text-5xl"
		>
			<ChefHat size={48} /> ศิลปะแห่งการปั่น
		</h1>
		<p class="text-lg text-[#0369a1] md:text-xl">
			เบื้องหลังเนื้อสัมผัสที่เหนียวนุ่มและละลายในปาก
		</p>
	</header>

	<!-- ส่วนเนื้อหาและรูปภาพ จัดกึ่งกลาง -->
	<section class="mx-auto max-w-4xl text-center">
		<!-- หัวข้อหลักและเส้นใต้สีฟ้า -->
		<h2
			class="mb-6 inline-block border-b-4 border-[#7dd3fc] pb-2 text-2xl font-bold text-[#0c4a6e]"
		>
			ความลับอยู่ที่อากาศและอุณหภูมิ
		</h2>
		<p class="mb-10 text-lg leading-relaxed text-gray-700 md:text-xl">
			กระบวนการปั่นเจลลาโต้จะใช้ความเร็วที่ช้ากว่าไอศกรีมมาก ทำให้มีอากาศแทรกซึมเข้าไป (Overrun)
			เพียงแค่ 20-30% เนื้อที่ได้จึงมีความแน่น หนึบ และเข้มข้น
			นอกจากนี้เจลลาโต้ยังถูกเสิร์ฟในอุณหภูมิที่อุ่นกว่าไอศกรีมเล็กน้อย
			ทำให้ต่อมรับรสของเราสัมผัสถึงความอร่อยได้เต็มที่ตั้งแต่คำแรก
		</p>

		<!-- กล่อง Mockup รูปภาพ (แก้ไขโครงสร้าง span ที่พังให้ถูกต้อง) -->
		<div
			class="mx-auto flex aspect-video w-full max-w-4xl flex-col items-center justify-center rounded-xl border-4 border-dashed border-[#7dd3fc] bg-[#e0f2fe] p-6 text-center shadow-sm"
		>
			<div class="mb-4 flex gap-4 text-[#0284c7]">
				<Settings size={56} />
				<ThermometerSnowflake size={56} />
			</div>
			<span class="text-xl font-bold text-[#0c4a6e]"
				>[ ภาพประกอบ: เครื่องปั่น หรือ ขั้นตอนการทำ ]</span
			>
			<span class="mt-2 text-base font-semibold text-[#0369a1]"
				>📌 ขนาดที่แนะนำ: 1280 x 720 px (สัดส่วน 16:9)</span
			>
			<span class="mt-2 text-sm text-gray-500"
				>(พื้นที่สำหรับทีมวาดรูป: วาดเครื่องทำเจลลาโต้ หรือเชฟกำลังตักเจลลาโต้ด้วยไม้พาย)</span
			>
		</div>
	</section>

	<!-- ปุ่มกลับหน้าแรกแบบเด่นๆ (Monochromatic โทนฟ้า) -->
	<div class="mt-12 text-center">
		<a
			href={resolve('/')}
			class="group inline-flex items-center justify-center gap-3 rounded-xl bg-[#bae6fd] px-8 py-4 text-lg font-bold text-[#0c4a6e] shadow-md transition duration-300 hover:-translate-y-1 hover:bg-[#7dd3fc] hover:shadow-lg hover:shadow-[#7dd3fc]/30"
		>
			<ArrowLeft size={28} class="text-[#0284c7] transition group-hover:scale-110" /> กลับหน้าแรก
		</a>
	</div>
</div>