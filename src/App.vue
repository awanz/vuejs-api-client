<template>
    <Title title="Tempat Wisata di Indonesia"/>
    <div>
        <form @submit.prevent="save">
            <input type="text" v-model="form.id">
            <input type="text" v-model="form.title">
            <textarea v-model="form.description"></textarea>
            <input type="text" v-model="form.location">
            <button type="submit">Save</button>
        </form>
        <TourList v-if="tours.length>0" :tours="tours"/>
        <ul>
            <li v-for="tour in tours" :key="tour.id">
                {{ tour.title }} <br>
                {{ tour.description }}
            </li>
        </ul>
        <button @click="load">Load</button>
    </div>
</template>

<script>

    import axios from 'axios'
    import Title from './components/Title.vue'
    import TourList from './components/TourList.vue'

    export default {
        name: 'App',
        components:{
            Title,
            TourList,
        },
        data() {
            return {
                form:{
                    id: '',
                    title: '',
                    description: '',
                    location: '',
                },
                tours: []
            }
        },


        async mounted() {
            this.load()
        },

        methods: {
            async load(){
                const response = await axios.get('https://secure-crag-55699.herokuapp.com/tours')
                this.tours = response.data
            },
            
            async save(){
                try{
                    //const response = await axios.post('https://secure-crag-55699.herokuapp.com/tour', this.form)
                    //this.tours = response.data
                    //console.log(this.tours)
                    axios.post('https://secure-crag-55699.herokuapp.com/tour', {
                        id: '99',
                        title: 'awan',
                        description: 'Flintstone',
                        location: 'Manonjaya'
                    })
                    .then(function (response) {
                        console.log(response);
                    })
                    .catch(function (error) {
                        console.log(error);
                    });
                    console.log("akhir")

                    this.id = ''
                    this.title = ''
                    this.description = ''
                    this.location = ''
                }catch (e){
                    console.log(e)
                }
                
            }
        },
    }
</script>