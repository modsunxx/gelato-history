<script>
	import { resolve } from '$app/paths';
	// Import ไอคอนที่ต้องการจาก lucide-svelte
	import {
		IceCream,
		ScrollText,
		Cherry,
		ChefHat,
		Camera
	} from 'lucide-svelte';
</script>

<svelte:head>
	<title>Gelato History - หน้าแรก</title>
</svelte:head>

<div class="space-y-12 pb-12">
	<!-- ส่วนหัวของเว็บไซต์ (Hero Section - โทนส้มพีช) -->
	<header class="rounded-2xl bg-[#f6e8d5] px-6 py-12 text-center shadow-sm">
		<h1
			class="mb-4 flex flex-wrap items-center justify-center gap-3 text-4xl font-extrabold text-[#e06853] md:text-5xl"
		>
			สัมผัสความหอมหวานของ Gelato <IceCream size={48} class="text-[#e06853]" />
		</h1>
		<p class="text-lg text-[#c2410c] md:text-xl">
			ศิลปะแห่งของหวานแช่แข็งจากอิตาลี ที่ครองใจคนทั่วโลก
		</p>
	</header>

	<!-- ส่วนเนื้อหาและรูปภาพ -->
	<section class="mx-auto max-w-4xl text-center">
		<!-- เปลี่ยนสีหัวข้อเป็นน้ำเงินเข้ม ตัดกับเส้นใต้สีส้มพีช -->
		<h2
			class="mb-6 inline-block border-b-4 border-[#e06853] pb-2 text-2xl font-bold text-[#1e40af]"
		>
			Gelato คืออะไร?
		</h2>
		<p class="mb-10 text-lg leading-relaxed text-gray-700 md:text-xl">
			เจลลาโต้ (Gelato) เป็นของหวานแช่แข็งสไตล์อิตาเลียนที่แตกต่างจากไอศกรีมทั่วไป
			ด้วยเนื้อสัมผัสที่เนียนนุ่ม รสชาติเข้มข้น และไขมันที่น้อยกว่า
			เตรียมพบกับเรื่องราวความอร่อยที่เราตั้งใจนำเสนอ
		</p>

		<!-- กรอบแสดงรูปภาพของจริง (แทนที่ Mockup) -->
    <div
      class="mx-auto w-full max-w-4xl overflow-hidden rounded-xl border-4 border-[#f6e8d5] shadow-md transition duration-300 hover:shadow-lg hover:shadow-[#e06853]/30"
    >
      <img 
        src="/image/main/main.JPG" 
        alt="ภาพรวม Gelato หลากรสชาติ" 
        class="aspect-video w-full object-cover"
      />
    </div>
	</section>

	<!-- ส่วนวิดีโอหรือภาพเคลื่อนไหว -->
	<section class="mx-auto max-w-4xl text-center mt-12">
		<h2
			class="mb-6 inline-block border-b-4 border-[#e06853] pb-2 text-2xl font-bold text-[#1e40af]"
		>
			ชมกรรมวิธีการทำเบื้องต้น
		</h2>
		<p class="mb-10 text-lg leading-relaxed text-gray-700 md:text-xl">
			วิดีโอแอนิเมชันด้านล่างนี้จะแสดงให้เห็นถึงขั้นตอนและศิลปะในการปั่นเจลลาโต้ให้ออกมาสมบูรณ์แบบ
		</p>

		<!-- กรอบแสดงวิดีโอของจริง (แทนที่ Mockup) -->
		<div
			class="mx-auto w-full max-w-4xl overflow-hidden rounded-xl border-4 border-[#f6e8d5] shadow-md transition duration-300 hover:shadow-lg hover:shadow-[#e06853]/30"
		>
			<!-- ดึงวิดีโอจากโฟลเดอร์ /video/ -->
			<video 
				controls 
				autoplay 
				muted 
				loop
				class="aspect-video w-full bg-black object-cover"
			>
				<source src="/video/video gelato.mp4" type="video/quicktime" />
				<source src="/video/video gelato.mp4" type="video/mp4" />
				เบราว์เซอร์ของคุณไม่รองรับการเล่นวิดีโอนี้
			</video>
		</div>
	</section>

	<!-- ส่วนเมนูนำทางแบบการ์ดด้านล่าง (ใส่ลูกเล่น Hover เป็นสีฟ้า/น้ำเงิน) -->
	<section class="mt-16 text-center">
		<h2 class="mb-8 text-2xl font-bold text-[#1e40af]">สำรวจเรื่องราวของ Gelato</h2>
		<div class="grid grid-cols-1 gap-6 sm:grid-cols-2 md:grid-cols-4">
			<a
				href={resolve('/history')}
				class="group rounded-xl border-2 border-[#f6e8d5] bg-white p-6 transition duration-300 hover:-translate-y-1 hover:border-[#bfdbfe] hover:shadow-lg hover:shadow-[#bfdbfe]/40"
			>
				<h3 class="mb-2 flex items-center justify-center gap-2 text-xl font-bold text-[#e06853] transition group-hover:text-[#2563eb]">
					<ScrollText size={24} class="transition group-hover:scale-110" /> ประวัติศาสตร์
				</h3>
				<p class="text-sm text-gray-500">ต้นกำเนิดจากอิตาลี</p>
			</a>
			<a
				href={resolve('/ingredients')}
				class="group rounded-xl border-2 border-[#f6e8d5] bg-white p-6 transition duration-300 hover:-translate-y-1 hover:border-[#bfdbfe] hover:shadow-lg hover:shadow-[#bfdbfe]/40"
			>
				<h3 class="mb-2 flex items-center justify-center gap-2 text-xl font-bold text-[#e06853] transition group-hover:text-[#2563eb]">
					<Cherry size={24} class="transition group-hover:scale-110" /> ส่วนผสมหลัก
				</h3>
				<p class="text-sm text-gray-500">เคล็ดลับความอร่อย</p>
			</a>
			<a
				href={resolve('/process')}
				class="group rounded-xl border-2 border-[#f6e8d5] bg-white p-6 transition duration-300 hover:-translate-y-1 hover:border-[#bfdbfe] hover:shadow-lg hover:shadow-[#bfdbfe]/40"
			>
				<h3 class="mb-2 flex items-center justify-center gap-2 text-xl font-bold text-[#e06853] transition group-hover:text-[#2563eb]">
					<ChefHat size={24} class="transition group-hover:scale-110" /> วิธีการทำ
				</h3>
				<p class="text-sm text-gray-500">ขั้นตอนการปั่น</p>
			</a>
			<a
				href={resolve('/gallery')}
				class="group rounded-xl border-2 border-[#f6e8d5] bg-white p-6 transition duration-300 hover:-translate-y-1 hover:border-[#bfdbfe] hover:shadow-lg hover:shadow-[#bfdbfe]/40"
			>
				<h3 class="mb-2 flex items-center justify-center gap-2 text-xl font-bold text-[#e06853] transition group-hover:text-[#2563eb]">
					<Camera size={24} class="transition group-hover:scale-110" /> แกลเลอรี
				</h3>
				<p class="text-sm text-gray-500">รวมภาพของหวาน</p>
			</a>
		</div>
	</section>
</div>