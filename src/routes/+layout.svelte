<script>
	import './layout.css';
	// Import Component Navbar ที่เราเพิ่งสร้างมาใช้งานผ่าน $lib (นามแฝงสำหรับโฟลเดอร์ src/lib)
	import Navbar from '$lib/components/Navbar.svelte';

	let { children } = $props();
</script>

<div class="min-h-screen bg-[#fdfbf7] font-sans text-[#4a3b32]">
	<!-- เรียกใช้งาน Navbar Component ตรงนี้ -->
	<Navbar />

	<!-- พื้นที่แสดงเนื้อหาของแต่ละหน้า -->
	<main class="mx-auto max-w-5xl p-6 md:p-12">
		{@render children()}
	</main>
</div>
