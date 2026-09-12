<svelte:head>
	<title>Gelato History - หน้าแรก</title>
</svelte:head>

<div class="space-y-12">
	<!-- ส่วนหัวของเว็บไซต์ (Hero Section) -->
	<header class="rounded-2xl bg-[#ffe6eb] px-6 py-12 text-center shadow-sm">
		<h1 class="mb-4 text-4xl font-extrabold text-[#d64550] md:text-5xl">
			สัมผัสความหอมหวานของ Gelato 🍦
		</h1>
		<p class="text-lg text-[#7a6355] md:text-xl">
			ศิลปะแห่งของหวานแช่แข็งจากอิตาลี ที่ครองใจคนทั่วโลก
		</p>
	</header>

	<!-- ส่วนเนื้อหาและรูปภาพ -->
	<section>
		<h2
			class="mb-4 inline-block border-b-4 border-[#ffd1dc] pb-2 text-2xl font-bold text-[#4a3b32]"
		>
			Gelato คืออะไร?
		</h2>
		<p class="mb-6 text-lg leading-relaxed">
			เจลลาโต้ (Gelato) เป็นของหวานแช่แข็งสไตล์อิตาเลียนที่แตกต่างจากไอศกรีมทั่วไป
			ด้วยเนื้อสัมผัสที่เนียนนุ่ม รสชาติเข้มข้น และไขมันที่น้อยกว่า
			เตรียมพบกับเรื่องราวความอร่อยที่เราตั้งใจนำเสนอ
		</p>

		<!-- กล่อง Mockup รูปภาพ (ทำเอง/ถ่ายเอง/AI/ตัดต่อ)[cite: 1] -->
		<div
			class="flex h-80 flex-col items-center justify-center rounded-xl border-4 border-dashed border-[#87bba2] bg-[#f0f7f4] p-6 text-center"
		>
			<span class="mb-4 text-5xl">🖼️</span>
			<span class="text-xl font-bold text-[#555]">[ พื้นที่สำหรับรูปภาพ Gelato ]</span>
			<span class="mt-2 text-sm text-gray-500"
				>(เตรียมใส่รูปภาพที่วาดเอง ถ่ายเอง ตัดต่อ หรือใช้ AI ที่นี่)</span
			>
		</div>
	</section>

	<!-- ส่วนวิดีโอหรือภาพเคลื่อนไหว -->
	<section>
		<h2
			class="mb-4 inline-block border-b-4 border-[#ffd1dc] pb-2 text-2xl font-bold text-[#4a3b32]"
		>
			ชมกรรมวิธีการทำเบื้องต้น
		</h2>
		<p class="mb-6 text-lg leading-relaxed">
			วิดีโอแอนิเมชันด้านล่างนี้จะแสดงให้เห็นถึงขั้นตอนและศิลปะในการปั่นเจลลาโต้ให้ออกมาสมบูรณ์แบบ
		</p>

		<!-- กล่อง Mockup วิดีโอ/ภาพเคลื่อนไหว[cite: 1] -->
		<div
			class="relative flex h-96 flex-col items-center justify-center overflow-hidden rounded-xl border-4 border-dashed border-[#e9c46a] bg-[#fdf6e3] p-6 text-center"
		>
			<span class="z-10 mb-4 text-5xl">🎬</span>
			<span class="z-10 text-xl font-bold text-[#555]">[ พื้นที่สำหรับวิดีโอ / ภาพเคลื่อนไหว ]</span
			>
			<span class="z-10 mt-2 text-sm text-gray-600"
				>(ต้องใช้วิดีโอที่ทำเองอย่างน้อย 1 อันในเว็บเพจ)</span
			>
		</div>
	</section>

	<!-- ส่วนเมนูนำทางแบบการ์ดด้านล่าง -->
	<section class="mt-12 text-center">
		<h2 class="mb-6 text-2xl font-bold text-[#4a3b32]">สำรวจเรื่องราวของ Gelato</h2>
		<div class="grid grid-cols-1 gap-6 sm:grid-cols-2 md:grid-cols-4">
			<a
				href="/history"
				class="rounded-xl border-2 border-[#f0e4d7] bg-white p-6 transition duration-300 hover:-translate-y-1 hover:border-[#ffd1dc] hover:shadow-lg"
			>
				<h3 class="mb-2 text-xl font-bold text-[#d64550]">📜 ประวัติศาสตร์</h3>
				<p class="text-sm text-gray-500">ต้นกำเนิดจากอิตาลี</p>
			</a>
			<a
				href="/ingredients"
				class="rounded-xl border-2 border-[#f0e4d7] bg-white p-6 transition duration-300 hover:-translate-y-1 hover:border-[#ffd1dc] hover:shadow-lg"
			>
				<h3 class="mb-2 text-xl font-bold text-[#d64550]">🍓 ส่วนผสมหลัก</h3>
				<p class="text-sm text-gray-500">เคล็ดลับความอร่อย</p>
			</a>
			<a
				href="/process"
				class="rounded-xl border-2 border-[#f0e4d7] bg-white p-6 transition duration-300 hover:-translate-y-1 hover:border-[#ffd1dc] hover:shadow-lg"
			>
				<h3 class="mb-2 text-xl font-bold text-[#d64550]">👨‍🍳 กรรมวิธีทำ</h3>
				<p class="text-sm text-gray-500">ขั้นตอนการปั่น</p>
			</a>
			<a
				href="/gallery"
				class="rounded-xl border-2 border-[#f0e4d7] bg-white p-6 transition duration-300 hover:-translate-y-1 hover:border-[#ffd1dc] hover:shadow-lg"
			>
				<h3 class="mb-2 text-xl font-bold text-[#d64550]">📸 แกลเลอรี</h3>
				<p class="text-sm text-gray-500">รวมภาพของหวาน</p>
			</a>
		</div>
	</section>
</div>
