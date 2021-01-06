<template>
    <div>
        <ul>
            <li v-for="tour in tours" :key="tour.id">
                {{ tour.title }} <br>
                {{ tour.description }}
            </li>
        </ul>
    </div>
</template>


<script>
export default {
    probs:{
        tours: Array
    }
}
</script>