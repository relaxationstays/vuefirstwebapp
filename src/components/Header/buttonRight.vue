<template>
    <div class="rightsection">
        <i class="fas fa-cog icon"></i>
        <i class="fas fa-bell icon"></i>
        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSmgN_DxQvEkX-8Ab-pkveOHdo6PaZ0zU68ig&s"
            alt="Profile Picture" class="profile-pic" style="width: 30px; height: 30px; border-radius: 50%;">
    </div>
</template>
<script>
export default {
    name: 'RightButton',
    props: {
        headerData: {
            type: Object,
            required: true, // Make sure headerData is passed as a prop
        },
    },
    data() {
        return {
            buttonText: 'Clt + K',
        };
    },
    methods: {
        handleClick() {
            alert('Button clicked!');
        },
    },
};
</script>
<style scoped>
.rightsection {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    border-radius: 8px;
    padding: 10px;
    position: relative;
    font-size: 20px;
}

.icon {
    margin-right: 20px;
}
</style>
