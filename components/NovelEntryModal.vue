<template>
    <div>
        <b-button v-b-modal.novelEntryModal class="btn btn-info">Add Novel</b-button>

        <b-modal id="novelEntryModal" title="Novel Entry" ok-title="Save" @ok="onSubmit">
            <form action="#" ref="form">
                <b-form-group
                    label="Title"
                    label-for="title"
                    >
                    <b-form-input id="title" v-model="novel.title" trim></b-form-input>
                </b-form-group>

                <b-form-group
                    label="Author"
                    label-for="author"
                    >
                    <b-form-input id="author" v-model="novel.author" trim></b-form-input>
                </b-form-group>

                <b-form-group
                    label="Description"
                    label-for="description"
                    >
                    <b-form-input id="description" v-model="novel.description" trim></b-form-input>
                </b-form-group>

                <b-form-group
                    label="Genre"
                    label-for="genre"
                    >
                    <b-form-input id="genre" v-model="novel.genre" trim></b-form-input>
                </b-form-group>

                <b-form-group
                    label="Date"
                    label-for="acquired_on"
                    >
                    <b-form-input id="acquired_on" type="date" v-model="novel.acquired_on" trim></b-form-input>
                </b-form-group>

            </form>
        </b-modal>
    </div>
</template>

<script>
export default {
    data() {
        return {
            novel: {},
        }
    },
    methods: {
        async onSubmit() {
            this.$axios.post('http://localhost:8000/api/novels', this.novel)
            .then((res)=>{
                if(res.status==202) {
                    alert('Successfully added the story')
                    this.$emit('onAdd')
                }
            })
        }
    }
    
}
</script>