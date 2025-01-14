<template>
    <div class="menu">
        <h3 v-if="release" style="padding-left: 12%;">Release</h3>
        <ul style="display: flex; justify-content: space-around;list-style: none;">
            <li class="list" v-for="(item, index) in headerData.menu" :key="item.title"
                :style="{ backgroundColor: release && index === 0 ? '#f1c232' : '', textAlign: release ? 'center' : 'left' }">
                {{ item.title }}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'MenuSection',
    props: {
        headerData: {
            type: Object,
            required: true, // Make sure headerData is passed as a prop
        },
        release: {
            type: Boolean,
            default: false,
        },
    },
    data() {
        return {
            buttonText: 'Click Me',
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
/* ul {
    padding: 0;
    margin: 0;
}

li {
    padding: 0;
    margin: 0;
} */
h3 {
    font-family: "Montserrat", serif !important;
}

.list {
    padding: 10px;
    border-radius: 8px;
    cursor: pointer;
    font-size: 16px;
    font-weight: 500;
    color: #333;
    transition: all 0.3s;
    /* background-color: rgb(178, 148, 14); */
    width: 60%;
    margin-right: 10px;
    font-family: "Montserrat", serif !important;


}
</style>
