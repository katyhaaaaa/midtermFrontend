<template>
    <div>

        <b-modal id="deleteModal" title="Delete Novel" ok-title="Save" @ok="onDelete" ok-variant="danger">
            Are You Sure Want to delete this?
            <br>
            <br>
            <h1>{{novel.title}}</h1>
        </b-modal>

    </div>
</template>

<script>
export default {
    props: {
        novel: {}
    },
    methods: {
        async onDelete() {
            this.$axios.delete('http://localhost:8000/api/novels/' + this.novel.id)
            .then((res)=>{
                if(res.status==202) {
                    alert('Story is deleted Successfully')
                    this.$emit('onDeleted')
                }
            })
        }
    }
    
}
</script>