<template>
    <div>
        <NavBar />

        <div class="container">
            <EditModal :novel="selectedNovel" />
            <DeleteModal :novel="selectedNovel" @onDeleted="getAll" />
            
            <h1>
                <NovelEntryModal class="float-right" @onAdd="getAll" />
                Novel
            </h1>

            <table class="table table-boredered">
                <thead>
                    <tr class="bg-info text-white">
                        <th>Title</th>
                        <th>Author</th>
                        <th>Description</th>
                        <th>Genre</th>
                        <th>Date</th>
                        <th>&nbsp;</th>
                        <th>&nbsp;</th>
                    </tr>
                </thead>

                <tbody>
                    <tr v-for="novel in novels" :key="novel.id">
                        <td>{{novel.title}}</td>
                        <td>{{novel.author}}</td>
                        <td>{{novel.description}}</td>
                        <td>{{novel.genre}}</td>
                        <td>{{novel.acquired_on}}</td>
                        <td>
                            <b-button @click="onEdit(novel)" variant="info" size="sm">Edit</b-button>
                        </td>
                        <td>
                            <b-button @click="onDelete(novel)" variant="danger" size="sm">Delete</b-button>
                        </td>
                    </tr>
                </tbody>

            </table>

        </div>

    </div>
</template>

<script>
export default {
    data() {
        return {
            novels: [],
            selectedNovel: {}
        }
    },
    methods: {
        async getAll() {
            await this.$axios.get('http://localhost:8000/api/novels')
            .then((res)=>{
                if(res.status==200) {
                    this.novels = res.data
                    console.log(this.novels)
                }
            })
        },
        onEdit(selectedNovel) {
            this.selectedNovel = selectedNovel;
            this.$bvModal.show('editModal')
        },
        onDelete(selectedNovel) {
            this.selectedNovel = selectedNovel;
            this.$bvModal.show('deleteModal')
        }
    },
    created() {
        this.getAll()
    }
}
</script>