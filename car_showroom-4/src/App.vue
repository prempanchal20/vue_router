<template>
    <div class="fonts" :style="{ fontFamily: 'Poppins, sans-serif' }">
        <Navbar />
        <RouterView />
    </div>
</template>


<script>
// import axios from "axios";
export default {
    name: "App",

    // created() {
    //     this.carsData
    // },

    data() {
        return {
            data: "",
            editModel: false,
            isAddModel: true,
        };
    },

    //----------------Axios APIs - GET, Post, Put, Delete----------------//

    // // GET Method - Axios API
    // carsData() {
    //     axios.get(
    //         "https://testapi.io/api/dartya/resource/cardata"
    //     ).then(response => {
    //         this.data = response.data.data
    //     })
    // },

    // Post Method - Axios API
    // getFormData(carData) {
    //     axios.post(
    //         "https://testapi.io/api/dartya/resource/cardata", carData
    //     ).then(response => console.log(response));
    //     alert(`"Created Data"\n
    //                  "Car Name is-" ${carData.name}, 
    //                  "Car Description is- " ${carData.details}, 
    //                  "Car Price is- " ${carData.price}, 
    //                  "Car URL is- " ${carData.image}`);
    //     this.carsData()
    //     this.onCancel()
    // },


    // Put Method - Axios API
    // async alertUpdateData(carData) {
    //     await axios.put(
    //         `https://testapi.io/api/dartya/resource/cardata/${carData.id}`,
    //         {
    //             name: carData.name,
    //             price: carData.price,
    //             image: carData.image,
    //             details: carData.details,
    //         }
    //     ).then((response) => console.log(response));

    //     // Edit Data Alert
    //     alert(`"Edited Data"\n
    //                 "Car Name is-" ${carData.name}, 
    //                 "Car Description is- " ${carData.details}, 
    //                 "Car Price is- " ${carData.price}, 
    //                 "Car URL is- " ${carData.image}`);
    //     this.carsData()
    //     this.onCancel()
    // },

    // DELETE Method - Axios API
    // async deleteData(itemId, itemName) {
    //     // Delete Data Alert
    //     const deleteAlert = window.confirm(
    //         `Are You Sure Want to Delete ${itemName}`
    //     );

    //     if (deleteAlert == true) {
    //         await axios
    //             .delete(`https://testapi.io/api/dartya/resource/cardata/${itemId}`)
    //             .then((response) => console.log(response));
    //         this.carsData();
    //     }
    // },

};
</script>

<style>
.menu {
    position: absolute;
    top: 80px;
    right: 10px;
}

.menu button {
    border: 1px solid white;
    padding: 10px 20px;
    border-radius: 10px;
    cursor: pointer;
}

.menu button {
    background-color: transparent;
    color: white;
    font-size: 20px;
}
</style>
