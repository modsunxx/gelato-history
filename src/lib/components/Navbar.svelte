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

	// 🌟 Playlist แบบใหม่: เก็บทั้งที่อยู่ไฟล์เพลงและที่อยู่รูปภาพปก[cite: 2]
	const playlist = [
		{ file: "/audio/A Cruel Angel's Thesis.mp3", cover: '/images/eva.png' },
		{ file: '/audio/Crossing Field.mp3', cover: '/images/sao.png' },
		{ file: '/audio/Styx Helix.mp3', cover: '/images/rezero.png' },
		{ file: '/audio/Unravel.mp3', cover: '/images/tokyo.png' }
	];
	let currentTrackIndex = $state(0);

	// ดึงเฉพาะที่อยู่ไฟล์เสียงไปให้ <audio> เล่น[cite: 2]
	let currentAudioSrc = $derived(playlist[currentTrackIndex].file);

	// เก็บเพลงที่ถูกกดใจ (เก็บเป็น index ของ playlist)[cite: 2]
	let likedTracks = new SvelteSet<number>();
	let isLiked = $derived(likedTracks.has(currentTrackIndex));

	function toggleLike() {
		if (likedTracks.has(currentTrackIndex)) {
			likedTracks.delete(currentTrackIndex);
		} else {
			likedTracks.add(currentTrackIndex);
		}
	}

	// แปลงวินาที -> "นาที:วินาที" เช่น 90 -> "1:30"[cite: 2]
	function formatTime(seconds: number) {
		if (!seconds || Number.isNaN(seconds)) return '0:00';
		const m = Math.floor(seconds / 60);
		const s = Math.floor(seconds % 60);
		return `${m}:${s.toString().padStart(2, '0')}`;
	}

	// ข้อมูลเพลง[cite: 2]
	let songTitle = $state('กำลังโหลด...');
	let artistName = $state('...');
	let albumArt = $state<string | null>(null);

	// ควบคุมเวลาและแถบ Progress[cite: 2]
	let currentTime = $state(0);
	let duration = $state(0);
	let progressPercent = $derived(duration > 0 ? (currentTime / duration) * 100 : 0);

	// ฟังก์ชันโหลดข้อมูลเพลงแบบใหม่ (รับ Object เข้ามา)[cite: 2]
	function loadMetadata(track: { file: string; cover: string }) {
		const path = track.file;
		const fileName = path.split('/').pop()?.replace('.mp3', '') || 'Gelato Song';
		songTitle = decodeURIComponent(fileName);
		artistName = 'Music Box';

		// 🌟 ใช้รูปภาพปกที่เราเตรียมไว้ทันที[cite: 2]
		albumArt = track.cover;

		try {
			jsmediatags.read(path, {
				onSuccess: (tag) => {
					const { title, artist } = tag.tags;
					// ถ้ามีชื่อเพลง/ศิลปินฝังมา ค่อยอัปเดตทับลงไป[cite: 2]
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
		// โหลดเพลงแรกตอนเปิดเว็บ[cite: 2]
		loadMetadata(playlist[currentTrackIndex]);
	});

	// เล่น / หยุด[cite: 2]
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

	// เปลี่ยนเพลง (หน้า/หลัง/สุ่ม)[cite: 2]
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
		// ส่ง Object เพลงใหม่เข้าไป[cite: 2]
		loadMetadata(playlist[currentTrackIndex]);

		await tick();
		if (isPlaying && audioRef) {
			audioRef.play();
		}
	}

	// เมื่อเพลงเล่นจบ[cite: 2]
	function onSongEnded() {
		if (isLoop && audioRef) {
			audioRef.currentTime = 0;
			audioRef.play();
		} else {
			changeTrack(1);
		}
	}

	// ฟังก์ชันสำหรับคลิกที่หลอดเวลาเพื่อกรอเพลง[cite: 2]
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

	<nav
		class="relative z-10 mx-auto mb-8 flex max-w-3xl flex-wrap justify-center gap-8 rounded-full bg-white/70 p-3 text-lg shadow-sm backdrop-blur-md"
	>
		<a href="/" class="font-bold text-[#7a6355] transition hover:text-[#d64550]">หน้าแรก</a>
		<a href="/history" class="font-bold text-[#7a6355] transition hover:text-[#d64550]"
			>ประวัติศาสตร์</a
		>
		<a href="/ingredients" class="font-bold text-[#7a6355] transition hover:text-[#d64550]"
			>ส่วนผสม</a
		>
		<a href="/process" class="font-bold text-[#7a6355] transition hover:text-[#d64550]"
			>กรรมวิธีทำ</a
		>
		<a href="/gallery" class="font-bold text-[#7a6355] transition hover:text-[#d64550]">แกลเลอรี</a>
	</nav>

	<audio
		bind:this={audioRef}
		src={currentAudioSrc}
		ontimeupdate={(e) => (currentTime = e.currentTarget.currentTime)}
		onloadedmetadata={(e) => (duration = e.currentTarget.duration)}
		onended={onSongEnded}
		class="hidden"
	></audio>

	<div
		class="relative z-10 mx-auto flex max-w-2xl flex-col items-center gap-8 rounded-4xl border-[3px] border-white/50 bg-white p-6 shadow-lg backdrop-blur-md md:flex-row"
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
