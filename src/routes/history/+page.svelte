<script>
	import { resolve } from '$app/paths';
	// Import ไอคอนที่ต้องการจาก lucide-svelte
	import { ScrollText, Map, ArrowLeft } from 'lucide-svelte';
</script>

<svelte:head>
	<title>ประวัติศาสตร์ Gelato</title>
</svelte:head>

<div class="space-y-12 pb-12">
	<!-- ส่วนหัว (Hero Section) ช่วยลดความโล่งของหน้าเว็บ -->
	<header class="rounded-2xl bg-[#fdf5fc] px-6 py-12 text-center shadow-sm">
		<h1
			class="mb-4 flex flex-wrap items-center justify-center gap-3 text-4xl font-extrabold text-[#d64550] md:text-5xl"
		>
			<ScrollText size={48} /> ประวัติศาสตร์ของ Gelato
		</h1>
		<p class="text-lg text-[#7a6355] md:text-xl">
			จุดเริ่มต้นของความหอมหวานที่เดินทางข้ามกาลเวลาจากอิตาลี[cite: 9]
		</p>
	</header>

	<!-- ส่วนเนื้อหาและรูปภาพ -->
	<section class="mx-auto max-w-4xl text-center">
		<p class="mb-10 text-lg leading-relaxed text-gray-700 md:text-xl">
			เจลลาโต้ (Gelato) มีต้นกำเนิดมาจากประเทศอิตาลี โดยคำว่า "Gelato" ในภาษาอิตาลีแปลว่า "แช่แข็ง"
			จุดเริ่มต้นของเจลลาโต้ต้องย้อนกลับไปในยุคเรอเนสซองส์
			ซึ่งมีการผสมผสานหิมะหรือน้ำแข็งเข้ากับผลไม้และน้ำผึ้ง ต่อมาได้มีการพัฒนาสูตรโดยใช้นมและไข่
			จนกลายมาเป็นของหวานยอดฮิตระดับโลก[cite: 9]
		</p>

		<!-- กล่อง Mockup รูปภาพ (อัปเดตขนาดและสัดส่วน 16:9) -->
		<div
			class="mx-auto flex aspect-video w-full max-w-4xl flex-col items-center justify-center rounded-xl border-4 border-dashed border-[#d897ce] bg-[#fcf0fa] p-6 text-center shadow-sm"
		>
			<Map size={56} class="mb-4 text-[#d897ce]" />
			<span class="text-xl font-bold text-[#555]"
				>[ ภาพประกอบ: ประวัติศาสตร์ / แผนที่อิตาลี ][cite: 9]</span
			>
			<span class="mt-2 text-base font-semibold text-[#70386a]"
				>📌 ขนาดที่แนะนำ: 1280 x 720 px (สัดส่วน 16:9)[cite: 9]</span
			>
			<span class="mt-2 text-sm text-gray-500"
				>(เตรียมใส่รูปภาพที่วาดเอง ถ่ายเอง ตัดต่อ หรือใช้ AI ที่นี่)[cite: 9]</span
			>
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
