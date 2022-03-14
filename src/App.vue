<template>
    <div class="form">
        <img alt="Vue logo" src="./assets/logo.png" />
        <h1>Lista de tareas</h1>
        <form @submit.prevent="submit()">
            <input
                type="text"
                placeholder="Ingrese tareas para hacer"
                v-model="input"
            />
            <button type="submit">Añadir</button>
        </form>
        <hr />
        <ul v-if="tareas.length">
                <li v-for="(tarea, index) in tareas" :key="index">
                    <span>{{ tarea }}</span>
                    <button @click="eliminar(index)">Eliminar</button>
                </li>
            </ul>
    </div>
</template>

<script>
export default {
    data(){
        return {
            input: undefined,
            tareas: [],
        }
    }, 
    methods: {
        submit() {
			this.tareas.push(this.input);
			return (this.input = undefined);
		},

		eliminar(val) {
			this.tareas = this.tareas.filter((item, index) => index !== val);
		},
    },
};
</script>

<style lang="scss">
    .form {
        display: flex;
        flex-direction: column;
        align-items: center;

        ul {
            padding: 0;
        }

    }
</style>
