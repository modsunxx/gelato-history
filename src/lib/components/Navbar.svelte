<script lang="ts">
	import { Play, Pause, SkipBack, SkipForward, Shuffle, Repeat, Heart } from 'lucide-svelte';
	import { onMount, tick } from 'svelte';
	import { SvelteSet } from 'svelte/reactivity';
	import jsmediatags from 'jsmediatags';

	// ตัวแปรควบคุมเครื่องเล่น
	let isPlaying = $state(false);
	let isShuffle = $state(false);
	let isLoop = $state(false);
	let audioRef = $state<HTMLAudioElement>();

	// 🌟 Playlist แบบใหม่: ดึงไฟล์จากโฟลเดอร์ใหม่ที่เราสร้างไว้
	const playlist = [
		{ file: '/midnight-sweet/midnight-sweet.wav', cover: '/midnight-sweet/midnight-sweet.jpeg' },
		{
			file: '/city-lights-vanilla/city-lights-vanilla.wav',
			cover: '/city-lights-vanilla/city-lights-vanilla.jpeg'
		},
		{ file: '/จุดหลอมเหลว/จุดหลอมเหลว.wav', cover: '/จุดหลอมเหลว/จุดหลอมเหลว.jpeg' },
		{
			file: '/last-order-คืนนี้/last-order-คืนนี้.wav',
			cover: '/last-order-คืนนี้/last-order-คืนนี้.jpeg'
		}
	];
	let currentTrackIndex = $state(0);

	// ดึงเฉพาะที่อยู่ไฟล์เสียงไปให้ <audio> เล่น[cite: 7]
	let currentAudioSrc = $derived(playlist[currentTrackIndex].file);

	// เก็บเพลงที่ถูกกดใจ (เก็บเป็น index ของ playlist)[cite: 7]
	let likedTracks = new SvelteSet<number>();
	let isLiked = $derived(likedTracks.has(currentTrackIndex));

	function toggleLike() {
		if (likedTracks.has(currentTrackIndex)) {
			likedTracks.delete(currentTrackIndex);
		} else {
			likedTracks.add(currentTrackIndex);
		}
	}

	// แปลงวินาที -> "นาที:วินาที" เช่น 90 -> "1:30"[cite: 7]
	function formatTime(seconds: number) {
		if (!seconds || Number.isNaN(seconds)) return '0:00';
		const m = Math.floor(seconds / 60);
		const s = Math.floor(seconds % 60);
		return `${m}:${s.toString().padStart(2, '0')}`;
	}

	// ข้อมูลเพลง[cite: 7]
	let songTitle = $state('กำลังโหลด...');
	let artistName = $state('...');
	let albumArt = $state<string | null>(null);

	// ควบคุมเวลาและแถบ Progress[cite: 7]
	let currentTime = $state(0);
	let duration = $state(0);
	let progressPercent = $derived(duration > 0 ? (currentTime / duration) * 100 : 0);

	// ฟังก์ชันโหลดข้อมูลเพลงแบบใหม่ (รับ Object เข้ามา)[cite: 7]
	function loadMetadata(track: { file: string; cover: string }) {
		const path = track.file;
		const fileName = path.split('/').pop()?.replace('.wav', '') || 'Gelato Song';
		songTitle = decodeURIComponent(fileName);
		artistName = 'Adipa create by suno';

		// 🌟 ใช้รูปภาพปกที่เราเตรียมไว้ทันที[cite: 7]
		albumArt = track.cover;

		try {
			jsmediatags.read(path, {
				onSuccess: (tag) => {
					const { title, artist } = tag.tags;
					// ถ้ามีชื่อเพลง/ศิลปินฝังมา ค่อยอัปเดตทับลงไป[cite: 7]
					if (title) songTitle = title;
					if (artist) artistName = artist;
				},
				onError: (error) => {
					console.log('ไฟล์นี้ไม่มี ID3 Tag หรืออ่านไม่ได้:', error.info);
				}
			});
		} catch (err) {
			console.error('jsmediatags ทำงานผิดพลาด:', err);
		}
	}

	onMount(() => {
		// โหลดเพลงแรกตอนเปิดเว็บ[cite: 7]
		loadMetadata(playlist[currentTrackIndex]);
	});

	// เล่น / หยุด[cite: 7]
	async function togglePlay() {
		if (audioRef) {
			if (isPlaying) {
				audioRef.pause();
			} else {
				await audioRef.play();
			}
			isPlaying = !isPlaying;
		}
	}

	// เปลี่ยนเพลง (หน้า/หลัง/สุ่ม)[cite: 7]
	async function changeTrack(step: number) {
		if (isShuffle) {
			let nextIndex;
			do {
				nextIndex = Math.floor(Math.random() * playlist.length);
			} while (nextIndex === currentTrackIndex && playlist.length > 1);
			currentTrackIndex = nextIndex;
		} else {
			currentTrackIndex = (currentTrackIndex + step + playlist.length) % playlist.length;
		}

		currentTime = 0;
		// ส่ง Object เพลงใหม่เข้าไป[cite: 7]
		loadMetadata(playlist[currentTrackIndex]);

		await tick();
		if (isPlaying && audioRef) {
			audioRef.play();
		}
	}

	// เมื่อเพลงเล่นจบ[cite: 7]
	function onSongEnded() {
		if (isLoop && audioRef) {
			audioRef.currentTime = 0;
			audioRef.play();
		} else {
			changeTrack(1);
		}
	}

	// ฟังก์ชันสำหรับคลิกที่หลอดเวลาเพื่อกรอเพลง[cite: 7]
	function seekMusic(event: MouseEvent) {
		if (!audioRef || duration === 0) return;
		const progressBar = event.currentTarget as HTMLElement;
		const rect = progressBar.getBoundingClientRect();
		const clickX = event.clientX - rect.left;
		const newTime = (clickX / rect.width) * duration;
		audioRef.currentTime = newTime;
		currentTime = newTime;
	}
</script>

<!-- eslint-disable svelte/no-navigation-without-resolve -->
<header class="relative overflow-hidden bg-[#ffd1dc] pt-6 pb-12 shadow-sm">
	<div
		class="pointer-events-none absolute inset-0 opacity-20"
		style="background-image: radial-gradient(#d64550 2.5px, transparent 2.5px); background-size: 24px 24px;"
	></div>

	<!-- อัปเดต: Navbar ปรับ Layout สำหรับมือถือให้เป็นกล่องมนธรรมดา และเว้นระยะห่างปุ่มให้กดง่ายขึ้น -->
	<nav
		class="relative z-20 mx-auto mb-8 flex w-[90%] max-w-3xl flex-wrap justify-center gap-x-3 gap-y-2 rounded-2xl bg-white/80 px-4 py-4 text-sm shadow-sm backdrop-blur-md sm:text-base md:gap-8 md:rounded-full md:px-8 md:text-lg"
	>
		<a href="/" class="p-1.5 font-bold text-[#7a6355] transition hover:text-[#d64550]">หน้าแรก</a>
		<a href="/history" class="p-1.5 font-bold text-[#7a6355] transition hover:text-[#d64550]"
			>ประวัติศาสตร์</a
		>
		<a href="/ingredients" class="p-1.5 font-bold text-[#7a6355] transition hover:text-[#d64550]"
			>ส่วนผสม</a
		>
		<a href="/process" class="p-1.5 font-bold text-[#7a6355] transition hover:text-[#d64550]"
			>กรรมวิธีทำ</a
		>
		<a href="/gallery" class="p-1.5 font-bold text-[#7a6355] transition hover:text-[#d64550]"
			>แกลเลอรี</a
		>
	</nav>

	<audio
		bind:this={audioRef}
		src={currentAudioSrc}
		ontimeupdate={(e) => (currentTime = e.currentTarget.currentTime)}
		onloadedmetadata={(e) => (duration = e.currentTarget.duration)}
		onended={onSongEnded}
		class="hidden"
	></audio>

	<!-- อัปเดต: กรอบ Music Player ปรับความกว้างในมือถือไม่ให้ชิดขอบจอเกินไป -->
	<div
		class="relative z-10 mx-auto flex w-[90%] max-w-2xl flex-col items-center gap-6 rounded-3xl border-[3px] border-white/50 bg-white p-6 shadow-lg backdrop-blur-md md:flex-row md:gap-8 md:rounded-4xl"
	>
		<div
			class="flex h-32 w-32 shrink-0 items-center justify-center overflow-hidden rounded-2xl border-4 border-[#ffb6c1] bg-[#fff0f3] shadow-inner"
		>
			{#if albumArt}
				<img src={albumArt} alt="Album Art" class="h-full w-full object-cover" />
			{:else}
				<span class="text-center text-xs font-bold text-[#d64550]">🍦<br />No Cover</span>
			{/if}
		</div>

		<div class="w-full grow">
			<div class="mb-4 flex items-start justify-between">
				<div class="overflow-hidden pr-4">
					<h3 class="truncate text-xl leading-tight font-bold text-[#5a3d31]" title={songTitle}>
						{songTitle}
					</h3>
					<p class="truncate text-sm text-[#7a6355]">{artistName}</p>
				</div>
				<button
					onclick={toggleLike}
					class="shrink-0 text-[#d64550] transition hover:scale-110"
					aria-label={isLiked ? 'เอาออกจากรายการโปรด' : 'เพิ่มในรายการโปรด'}
				>
					<Heart size={28} fill={isLiked ? 'currentColor' : 'none'} />
				</button>
			</div>

			<!-- svelte-ignore a11y_click_events_have_key_events -->
			<!-- svelte-ignore a11y_no_static_element_interactions -->
			<div
				class="relative mb-1 flex h-2 w-full cursor-pointer items-center rounded-full bg-[#ffe6eb] shadow-inner"
				onclick={seekMusic}
			>
				<div class="relative h-full rounded-full bg-[#d64550]" style="width: {progressPercent}%">
					<div
						class="pointer-events-none absolute top-1/2 right-0 h-4 w-4 translate-x-1/2 -translate-y-1/2 rounded-full border-2 border-[#d64550] bg-white shadow-sm"
					></div>
				</div>
			</div>

			<div class="mb-3 flex justify-between px-1 text-xs font-medium text-[#7a6355]">
				<span>{formatTime(currentTime)}</span>
				<span>{formatTime(duration)}</span>
			</div>

			<div class="mb-2 flex items-center justify-between px-4 text-[#7a6355]">
				<button
					onclick={() => (isShuffle = !isShuffle)}
					class="transition {isShuffle ? 'text-[#d64550]' : 'hover:text-[#d64550]'}"
				>
					<Shuffle size={20} />
				</button>

				<button onclick={() => changeTrack(-1)} class="transition hover:text-[#d64550]">
					<SkipBack size={24} fill="currentColor" />
				</button>

				<button
					onclick={togglePlay}
					class="flex h-12 w-12 items-center justify-center rounded-full bg-[#d64550] text-white shadow-md transition hover:scale-105 hover:bg-[#c23b45]"
				>
					{#if isPlaying}
						<Pause size={24} fill="currentColor" />
					{:else}
						<Play size={24} fill="currentColor" class="translate-x-0.5" />
					{/if}
				</button>

				<button onclick={() => changeTrack(1)} class="transition hover:text-[#d64550]">
					<SkipForward size={24} fill="currentColor" />
				</button>

				<button
					onclick={() => (isLoop = !isLoop)}
					class="transition {isLoop ? 'text-[#d64550]' : 'hover:text-[#d64550]'}"
				>
					<Repeat size={20} />
				</button>
			</div>
		</div>
	</div>
</header>
