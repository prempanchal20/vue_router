<template>
    <div>
        <vee-form class="modal" :validation-schema="schema">
            <div class="modal-content">

                <h2 v-if="!isAddModel">Edit car</h2>
                <h2 v-else>Add car</h2>
                
                <div class="car-details">
                    <label for="name">Car Name: </label>
                    <vee-field type="text" id="car-name" name="name" placeholder="enter car name" v-model="carData.name" />
                    <ErrorMessage class="error-text" name="name" />

                    <label for="details">Car Description:</label>
                    <vee-field id="car-details" name="details" as="textarea" rows="4" cols="50"
                        placeholder="enter car description" v-model="carData.details">
                    </vee-field>

                    <ErrorMessage class="error-text" name="details" />

                    <label for="price">Car Price:</label>
                    <vee-field type="number" id="price" name="price" placeholder="enter car price"
                        v-model="carData.price" />
                    <ErrorMessage class="error-text" name="price" />

                    <label for="url">Car Image:</label>
                    <vee-field name="url" type="url" id="car-url" placeholder="enter Image URL" v-model="carData.image" />
                    <ErrorMessage class="error-text" name="url" />

                    <div class="button">
                        <button type="reset" class="reset" @click="onCancel">Cancel</button>

                        <button type="submit" class="submit" v-if="isAddModel" v-on:click.prevent="getFormData">
                            Submit
                        </button>

                        <button type="submit" class="submit" v-on:click.prevent="alertUpdateData" v-else>
                            Update
                        </button>
                    </div>
                </div>
            </div>
        </vee-form>
    </div>
</template>

<script>
import GalleryCard from "./GalleryCard.vue";
import { ErrorMessage } from "vee-validate";

export default {
    name: "CarForm",
    components: {
        GalleryCard,
    },

    data() {
        return {
            schema: {
                name: "required",
                details: "required|min:30|max:120",
                url: "required|url",
                price: "required",
            },

            carData: {
                name: this.editCar.name || "",
                price: this.editCar.price || "",
                image: this.editCar.image || "",
                details: this.editCar.details || "",
                id: this.editCar.id,
            },
        };
    },

    props: {
        editModel: {
            type: Boolean,
        },

        editCar: {
            type: Object,
        },

        isAddModel: {
            type: Boolean,
        },

        editData: {
            type: Boolean,
        },
    },

    methods: {
        onCancel() {
            this.$emit("onCancel");
        },

        getFormData() {
            this.$emit('getFormData',this.carData);
        },

        alertUpdateData(){
            this.$emit('alertUpdateData',this.carData);
        },
    },
};
</script>

<style scoped>
* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    text-decoration: none;
    list-style: none;
    color: white;
}

.car-details {
    display: grid;
}

.modal {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: #151418;
    border-radius: 10px;
}

.modal-content {
    background-color: rgba(0, 0, 0, 0.5);
    margin: 10% auto;
    padding: 20px;
    border: 1px solid #888;
    width: 50%;
    border-radius: 20px;
}

.close {
    color: #aaa;
    float: right;
    font-size: 28px;
    font-weight: bold;
}

.close:hover,
.close:focus {
    color: black;
    text-decoration: none;
    cursor: pointer;
}

.form {
    display: flex;
    flex-direction: column;
}

label {
    margin-top: 10px;
}

input[type="text"],
input[type="number"],
input[type="url"],
textarea {
    padding: 10px;
    margin-top: 5px;
    margin-bottom: 10px;
    border-radius: 5px;
    border: none;
    color: black;
}

button[type="submit"] {
    background-color: #4caf50;
    color: white;
    padding: 10px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    margin-top: 10px;
    width: 30%;
    margin-right: 10%;
}

button[type="reset"] {
    background-color: rgb(209, 91, 91);
    color: white;
    padding: 10px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    margin-top: 10px;
    width: 30%;
    margin-right: 10%;
}

.button {
    display: flex;
    justify-content: space-evenly;
    position: relative;
    top: 3px;
}

h2 {
    color: white;
    text-align: center;
}

.error-text {
    color: rgb(219, 81, 81);
}

@media only screen and (max-width: 958px) and (min-width: 350px) {
    .modal-content {
        margin-top: 30%;
        width: 80%;
    }
}
</style>
