<template>
    <div class="input-header-field">
        <div class="input-section">
            <i class="fas fa-search icon"></i>
            <input class="inputField" type="text" placeholder="Search here ......" />
            <button @click="handleClick" class="button">
                {{ buttonText }}
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'InputHeaderField',
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
.input-section {
    display: flex;
    align-items: center;
    /* background-color: yellow; */
    border: 0.5px solid #ccc;
    border-radius: 8px;
    padding: 10px;
    position: relative;
}

.icon {
    margin-right: 10px;
}

.inputField {
    border: 1px solid #ccc;
    padding: 8px;
    font-size: 14px;
    margin-right: 10px;
    /* flex: 1; */
    width: 80%;
    border: none;
    outline: none;
    font-family: "Montserrat", serif !important;
}

.button {
    position: absolute;
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
    background-color: white;
    /* color: white; */
    border: none;
    border-radius: 4px;
    right: 1%;
    border: 1px solid #ccc;
    border-radius: 8px;

}

.button:hover {
    background-color: #0056b3;
}
</style>
