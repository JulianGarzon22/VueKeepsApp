<template>
<div>
<div class="container my-5">
    <div class="card text-left">
        <div class="card-body">
        <h4 class="card-title">Notas</h4>
        <form v-on:submit.prevent="addKeep(newKeep)">
        <div class="row">
            <div class="col-10">
                <div class="form-group">
                    <label for="keep">Nueva tarea</label>
                    <input v-model="newKeep" class="form-control" id="keep">
                </div>
            </div>
            <div class="col-2">
                <button class="btn btn-secondary" type="submit">Añadir</button>
            </div>
        </div>
        </form>
        </div>
    </div>
    <div class="card my-5 text-left">
        <div class="card-body">
            <h4 class="card-title">Listado</h4>
            <table class="table">
                <thead>
                    <tr>
                        <th scope="col">ID</th>
                        <th scope="col">Descripcion</th>
                        <th scope="col">Edit</th>
                        <th scope="col">Eliminar</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="keep in keeps" :key="keep.id">
                        <td scope="row">{{keep.id}}</td>
                        <td>
                            <span v-if="formUpdate">
                                {{keep.description}}
                            </span>
                            <span v-else>
                                <input v-model="newKeepUpdate" type="text">
                            </span>
                        </td>
                        <td>
                            <span v-if="formUpdate">
                                <button @click="showForm(keep)" class="btn btn-warning">Editar</button>
                            </span>
                            <span v-else>
                                <button @click="updateKeep(keep)" class="btn btn-warning">Guardar</button>
                            </span>
                        </td>
                        <td><button @click="deleteKeep(keep)" class="btn btn-danger">Eliminar</button></td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</div>
</div>
</template>

<script>
export default {
    data() {
        return {
            keeps: [
                {
                    id: 1,
                    editable: false,
                    description: 'Comprar leche mañana',
                },
                {
                    id: 2,
                    editable: false,
                    description: 'Google es gay',
                },
                {
                    id: 3,
                    editable: false,
                    description: 'Subscribe to pewdiepie',
                }
            ],
            newKeep: '',
            formUpdate: true,
            newKeepUpdate: '',
        }
    },
    methods: {
        addKeep(newKeep) {
            this.keeps.push(
                {
                    id: 5,
                    description: newKeep,
                    editable: false,
                }
            );
            this.newKeep = '';
        },
        deleteKeep(keep) {
            this.keeps.splice(find(keep.description = keep),1)
        },
        showForm(Keep) {
            this.newKeepUpdate = keep;
            this.formUpdate = true;
        },
        updateKeep(keep) {
            this.formUpdate = false;
        }
    }
}
</script>

<style scoped>

</style>