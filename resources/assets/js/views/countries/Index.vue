<template>
    <div class="row">
        <div class="col-md-12">
            <div class="panel panel-default">
                <div class="panel-heading">
                    <div class="row">
                        <div class="col-md-6">
                            {{ store.title }}
                        </div>
                        <div class="col-md-6 text-right">
                            <create-button :name="'countries-create'"></create-button>
                        </div>
                    </div>
                </div>
                <div class="panel-body">
                    <crud-index :columns="columns" :loading="loading" :store="store">
                        <tr v-for="item in items">
                            <td>{{ item.id }}</td>
                            <td>
                                <router-link :to="{ name: 'countries-edit', params: { id: item.id }}">
                                    {{ item.name }}
                                </router-link>
                            </td>
                            <td>{{ item.users_count }}</td>
                            <td>{{ item.created_at }}</td>
                        </tr>
                    </crud-index>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import Crud from '../../components/Crud/Crud'
    import CrudIndex from '../../components/Crud/Index.vue'
    import CreateButton from "../../components/Crud/CreateButton.vue";

    export default {
        mixins: [Crud],
        components: {
            CreateButton,
            CrudIndex
        },
        data() {
            return {
                module: 'countries',
                columns: [
                    {id: 0, name: 'ID', width: 5},
                    {id: 1, name: 'Name', width: 30},
                    {id: 3, name: 'Users', width: 15},
                    {id: 4, name: 'Created at', width: 50},
                ]
            }
        },
        mounted() {
        }
    }
</script>
