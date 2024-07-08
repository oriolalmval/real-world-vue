<template>
    <div class="eventDetail">
        <h1 v-if="event">{{ event.title }}</h1>
        <p v-if="event">{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
        <p v-if="event">{{ event.description }}</p>
        <p v-if="!event">Loading...</p>
    </div>
</template>

<script>
import EventService from '@/services/EventService';

export default {
    props: ['id'],
    data() {
        return {
            event: null
        }
    },
    created() {
        const id = this.$route.params.id;
        EventService.getEvent(this.id)
            .then(response => {
                this.event = response.data;
            })
            .catch(error => {
                console.log('There was an error!', error);
            });
    }
}
</script>

<style scoped>
.eventDetail {
/* algo */
}
</style>
