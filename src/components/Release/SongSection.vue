<template>
    <div class="song-section">
        <div class="song-card" v-for="song in releaseData.songs" :key="song.id">
            <img :src="song.music" :alt="song.songName" class="song-image" />
            <div class="song-info">
                <h3 class="song-title">{{ song.songName }}</h3>
                <p class="song-artist">By {{ song.singer }}</p>
            </div>
        </div>
    </div>
</template>
<script>
import releaseData from '@/content/releases/Release';
export default {
    data() {
        return {
            releaseData
        };
    }
};
</script>
<style scoped>
.song-section {
    display: flex;
    gap: 20px;
    flex-wrap: wrap;
    /* padding: 30px; */
    font-family: "Montserrat", serif !important;
    /* justify-content: center; */
}

.song-card {
    width: 210px;
    border: 1px solid #ddd;
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    text-align: center;
    background-color: #fff;
}

.song-image {
    width: 100%;
    height: 150px;
    object-fit: cover;
}

.song-info {
    padding: 10px;
}

.song-title {
    font-size: 16px;
    font-weight: bold;
    margin: 0;
}

.song-artist {
    font-size: 14px;
    color: #555;
    margin: 5px 0 0;
}

/* Media Queries for Responsiveness */
@media (max-width: 768px) {
    .song-card {
        width: 45%;
    }
}

@media (max-width: 480px) {
    .song-card {
        width: 100%;
    }
}
</style>
