<template>
    <form @submit.prevent="submit">
    <div class="field">
      <label class="label" for="broadcast">Broadcast</label>
      <input class="input" type="text" name="broadcast" v-model="data.message"/>
      <p class="is-size-7">Description</p>
    </div>
    <button type="submit" class="button success">Create Event</button>
    <p>{{ message }}</p>
</form>
</template>
<script>
export default {
    mounted() {
        this.$echo.channel('test').listen('TestEvent', (e) => {
            this.message = e.message
        })
    },
    data(){
        return{
            data:{
                message: ''
            },
            message: ''
        }
    },
    methods: {
        async submit() {
            let d = await this.$axios.$post('/api/event',this.data).catch(e => {
                console.log(e)
            });
            this.data.message = ''
            
        }
    }
}
</script>