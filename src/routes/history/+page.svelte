<script>
	import { resolve } from '$app/paths';
	// Import icons from lucide-svelte
	import { ScrollText, Map, ArrowLeft } from 'lucide-svelte';
</script>

<svelte:head>
	<title>History of Gelato</title>
</svelte:head>

<div class="space-y-12 pb-12">
	<!-- Header section (โทนสีแดงอมชมพู ตัดกับไอคอนสีฟ้า) -->
	<header class="rounded-2xl bg-[#ffe4e6] px-6 py-12 text-center shadow-sm">
		<h1
			class="mb-4 flex flex-wrap items-center justify-center gap-3 text-4xl font-extrabold text-[#be123c] md:text-5xl"
		>
			<ScrollText size={48} class="text-[#0ea5e9]" /> History of Gelato
		</h1>
		<p class="text-lg text-[#881337] md:text-xl">
			The origin of the sweet and fragrant journey from Italy
		</p>
	</header>

	<!-- Content and image section -->
	<section class="mx-auto max-w-4xl text-center">
		<p class="mb-10 text-lg leading-relaxed text-gray-700 md:text-xl">
			เจลาโต้ (Gelato) มีต้นกำเนิดมาจากประเทศอิตาลี คำว่า "เจลาโต้" ในภาษาอิตาเลียนมีความหมายว่า "เย็น" ต้นกำเนิดของเจลาโต้ต้องย้อนกลับไปในช่วงยุคเรอเนสซองส์ ที่มีการผสมเฮเซลนัทหรือไอศกรีมกับผลไม้และน้ำ ต่อมาก็มีการพัฒนาสูตรด้วยน้ำตาลและไข่ จนกลายเป็นของหวานที่ได้รับความนิยมทั่วโลก
		</p>

		<!-- Mockup image box (โทนสีเหลือง) -->
		<!-- กรอบแสดงรูปภาพของจริง (แทนที่ Mockup) -->
		<div
			class="mx-auto w-full max-w-4xl overflow-hidden rounded-xl border-4 border-[#fcd34d] bg-[#fef3c7] p-4 shadow-sm transition duration-300 hover:shadow-md hover:shadow-[#fcd34d]/40"
		>
			<!-- ดึงรูปภาพจาก /image/history/ -->
			<img 
				src="/image/history/history.jpg" 
				alt="ประวัติศาสตร์และต้นกำเนิดเจลลาโต้" 
				class="aspect-video w-full rounded-lg object-cover shadow-sm"
			/>
			
			<!-- แคปชั่นใต้รูปภาพ พร้อมไอคอนสีเหลืองอำพันเข้ากับกรอบ -->
			<div class="mt-4 flex items-center justify-center gap-3 text-[#d97706]">
				<Map size={24} />
				<span class="text-lg font-bold text-[#b45309]">ต้นกำเนิดเจลลาโต้จากอิตาลี</span>
				<Map size={24} />
			</div>
		</div>
	</section>

	<!-- Back to home button (โทนสีฟ้า) -->
	<div class="mt-12 text-center">
		<a
			href={resolve('/')}
			class="inline-flex items-center justify-center gap-3 rounded-xl bg-[#bae6fd] px-8 py-4 text-lg font-bold text-[#0369a1] shadow-md transition duration-300 hover:-translate-y-1 hover:bg-[#7dd3fc] hover:shadow-lg"
		>
			<ArrowLeft size={28} /> Back to Home
		</a>
	</div>
</div>