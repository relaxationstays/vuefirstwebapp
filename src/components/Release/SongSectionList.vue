<template>
    <div>
        <h3>
            Our Top Releasing Listening Songs
        </h3>
    </div>
    <div class="song-section">

        <div class="song-card" v-for="song in releaseData.songs.slice(0, 8)" :key="song.id">
            <img :src="song.music" :alt="song.songName" class="song-image" />
            <div class="song-info">
                <p class="song-name">{{ song.songName }}</p>
                <p class="song-singer">By {{ song.singer }}</p>
                <p class="song-stats"><i class="fas fa-music"></i> 8k</p>
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
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 20px;
    font-family: "Montserrat", serif !important;
}

.song-card {
    border: 1px solid #ddd;
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    background-color: #fff;
    display: flex;
    /* align-items: center; */
    gap: 10px;
    /* padding: 10px; */
}

.song-image {
    width: 80px;
    height: 80px;
    object-fit: cover;
    border-radius: 8px;
}

.song-info {
    flex-grow: 1;
    text-align: left;
    display: flex;
    gap: 10px;
    /* justify-content: center; */
    align-items: center;
    padding-left: 20px;
}

h3 {
    font-family: "Montserrat", serif !important;
}

.song-name {
    font-weight: 600;
    margin: 0 0 5px 0;
}

.song-singer {
    font-weight: 400;
    margin: 0 0 5px 0;
    color: #555;
}

.song-stats {
    font-weight: 400;
    color: #999;
    margin: 0;
}

/* Responsive Adjustments */
@media (min-width: 768px) {
    .song-section {
        grid-template-columns: repeat(2, 1fr);
    }
}
</style>
