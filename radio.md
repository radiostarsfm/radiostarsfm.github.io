---
layout: default
title: Radio Live
---

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

<style>
    /* Mengisolasi desain agar tidak merusak layout utama */
    .radio-wrapper {
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 30px 15px;
        width: 100%;
        box-sizing: border-box;
    }

    .player-container {
        background: linear-gradient(145deg, #1e1e1e, #2a2a2a);
        border-radius: 24px;
        padding: 40px 30px;
        box-shadow: 0 15px 35px rgba(0, 0, 0, 0.5);
        width: 100%;
        max-width: 360px;
        text-align: center;
        border: 1px solid #333;
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        color: #ffffff;
        z-index: 10;
        position: relative;
    }

    /* Animasi Status Live */
    .player-container .live-indicator {
        display: inline-flex;
        align-items: center;
        gap: 8px;
        background: rgba(255, 0, 68, 0.1);
        color: #ff0044;
        padding: 6px 16px;
        border-radius: 50px;
        font-size: 12px;
        font-weight: 700;
        letter-spacing: 1px;
        margin-bottom: 25px;
        border: 1px solid #ff0044;
    }

    .player-container .pulse-dot {
        width: 8px;
        height: 8px;
        background-color: #ff0044;
        border-radius: 50%;
        animation: pulse 1.5s infinite;
    }

    @keyframes pulse {
        0% { box-shadow: 0 0 0 0 rgba(255, 0, 68, 0.7); }
        70% { box-shadow: 0 0 0 10px rgba(255, 0, 68, 0); }
        100% { box-shadow: 0 0 0 0 rgba(255, 0, 68, 0); }
    }

    .player-container h2.radio-title {
        margin: 0;
        font-size: 26px;
        font-weight: 800;
        letter-spacing: 0.5px;
        color: #ffffff;
        line-height: 1.2;
    }

    .player-container p.radio-subtitle {
        color: #a0a0a0;
        font-size: 14px;
        margin-top: 8px;
        margin-bottom: 35px;
    }

    /* Custom Play Button */
    .player-container .play-btn {
        background: #1db954;
        color: white;
        border: none;
        width: 90px;
        height: 90px;
        border-radius: 50%;
        font-size: 35px;
        cursor: pointer;
        transition: all 0.3s ease;
        display: flex;
        justify-content: center;
        align-items: center;
        margin: 0 auto;
        box-shadow: 0 8px 25px rgba(29, 185, 84, 0.4);
    }

    .player-container .play-btn:hover {
        transform: scale(1.08);
        background: #1ed760;
        box-shadow: 0 12px 30px rgba(29, 185, 84, 0.6);
    }

    .player-container .play-btn:active {
        transform: scale(0.95);
    }

    /* Slider Volume Custom */
    .player-container .volume-wrapper {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 15px;
        margin-top: 30px;
        padding: 0 10px;
    }

    .player-container .volume-wrapper i {
        color: #a0a0a0;
        font-size: 18px;
        width: 20px;
        transition: color 0.3s ease;
    }

    .player-container .volume-slider {
        -webkit-appearance: none;
        width: 70%;
        height: 6px;
        background: #444;
        border-radius: 5px;
        outline: none;
    }

    .player-container .volume-slider::-webkit-slider-thumb {
        -webkit-appearance: none;
        appearance: none;
        width: 16px;
        height: 16px;
        border-radius: 50%;
        background: #1db954;
        cursor: pointer;
        box-shadow: 0 0 10px rgba(29, 185, 84, 0.5);
        transition: transform 0.2s;
    }

    .player-container .volume-slider::-webkit-slider-thumb:hover {
        transform: scale(1.2);
    }

    /* Area Media Sosial */
    .player-container .divider {
        height: 1px;
        background: #333;
        margin: 30px 0 25px 0;
    }

    .player-container .social-title {
        font-size: 12px;
        color: #888;
        text-transform: uppercase;
        letter-spacing: 1px;
        margin-bottom: 15px;
        display: block;
    }

    .player-container .social-menu {
        display: flex;
        gap: 15px;
        justify-content: center;
    }

    .player-container .social-btn {
        display: flex;
        align-items: center;
        gap: 8px;
        text-decoration: none;
        padding: 12px 20px;
        border-radius: 12px;
        font-size: 14px;
        font-weight: 600;
        color: white;
        transition: all 0.2s ease;
        flex: 1;
        justify-content: center;
    }

    .player-container .social-btn:hover {
        filter: brightness(1.2);
        transform: translateY(-2px);
        color: white;
        text-decoration: none;
    }

    .player-container .btn-tiktok {
        background: #000000;
        border: 1px solid #333;
    }

    .player-container .btn-spotify {
        background: #1db954;
    }
</style>

<div class="radio-wrapper">
    <div class="player-container">
        <div class="live-indicator">
            <div class="pulse-dot"></div>
            LIVE ON AIR
        </div>

        <h2 class="radio-title">RadioStars FM</h2>
        <p class="radio-subtitle">Musik & Informasi Terbaik</p>

        <audio id="radioStream" preload="none">
            <source src="https://asv.alhastream.com:3010/radio" type="audio/mpeg">
        </audio>

        <button class="play-btn" id="playBtn" onclick="togglePlay()">
            <i class="fa-solid fa-play" id="playIcon" style="margin-left: 5px;"></i>
        </button>

        <div class="volume-wrapper">
            <i class="fa-solid fa-volume-high" id="volIcon"></i>
            <input type="range" id="volumeSlider" class="volume-slider" min="0" max="1" step="0.01" value="1">
        </div>

        <div class="divider"></div>

        <span class="social-title">Temukan Kami Di</span>
        <div class="social-menu">
            <a href="https://tiktok.com/@AkunTikTokAnda" target="_blank" class="social-btn btn-tiktok">
                <i class="fa-brands fa-tiktok"></i> TikTok
            </a>
            <a href="https://open.spotify.com/user/AkunSpotifyAnda" target="_blank" class="social-btn btn-spotify">
                <i class="fa-brands fa-spotify"></i> Spotify
            </a>
        </div>
    </div>
</div>

<script>
    const audioEl = document.getElementById('radioStream');
    const playBtn = document.getElementById('playBtn');
    const playIcon = document.getElementById('playIcon');
    const volumeSlider = document.getElementById('volumeSlider');
    const volIcon = document.getElementById('volIcon');
    let isPlaying = false;

    // Fungsi Play/Pause
    function togglePlay() {
        if (isPlaying) {
            audioEl.pause();
            audioEl.src = audioEl.src; // Anti-delay buffer
            playIcon.className = "fa-solid fa-play";
            playIcon.style.marginLeft = "5px"; 
            isPlaying = false;
        } else {
            // Error handling ditambah agar ketahuan jika stream gagal dimuat
            audioEl.play().then(() => {
                playIcon.className = "fa-solid fa-pause";
                playIcon.style.marginLeft = "0";
                isPlaying = true;
            }).catch(function(error) {
                console.error("Gagal memutar audio:", error);
                alert("Gagal memutar stream. Pastikan link streaming mendukung HTTPS/SSL.");
            });
        }
    }

    // Fungsi Pengatur Volume
    volumeSlider.addEventListener('input', function() {
        audioEl.volume = this.value;
        
        // Mengubah ikon sesuai tingkat volume
        if (this.value == 0) {
            volIcon.className = 'fa-solid fa-volume-xmark';
            volIcon.style.color = '#ff0044'; // Merah jika mute
        } else if (this.value < 0.5) {
            volIcon.className = 'fa-solid fa-volume-low';
            volIcon.style.color = '#a0a0a0';
        } else {
            volIcon.className = 'fa-solid fa-volume-high';
            volIcon.style.color = '#a0a0a0';
        }
    });
</script>
