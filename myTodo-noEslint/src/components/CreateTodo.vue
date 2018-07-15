<template>
    <div class="content">
        <button class="w3-button w3-xlarge w3-circle w3-red w3-card-4 newForm" v-on:click="newForm()" v-show="!isCreating">+</button>
        <div class="card" v-show="isCreating">
            <div class="content">
                <div class="form">
                    <div class="field">
                        <label>Titile</label>
                        <input type="text" class="form-input" v-model="titleText" ref="title" defaultValue=""></input>
                    </div>
                    <div class="field">
                        <label>Project</label>
                        <input type="text" class="form-input" v-model="projectText" ref="project" defaultValue=""></input>
                    </div>
                    <div class="functions">
                        <button class="carry-out" v-on:click="createForm()">Create</button>
                        <button class="carry-out" v-on:click="cancelCreateForm()">Cancel</button>
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>
<script>
export default {
    data() {
        return {
            titleText: '',
            projectText: '',
            isCreating: false,
        };
    },
    methods: {
        newForm() {
            this.isCreating = true;
        },
        cancelCreateForm() {
            this.isCreating = false;
        },
        createForm() {
            if(this.titleText.length > 0 && this.projectText.length > 0) {
                const title = this.titleText;
                const project = this.projectText;
                this.$emit('create-todo', {
                    title,
                    project,
                    done: false,
                });
            this.titleText = '';
            this.projectText = '';
            this.isCreating = false;
            }
        },
    },
};
</script>
<style>
.newForm {
    float: left;
    width: 90px;
    height: 90px;
    margin-top: 20px;
    margin-left: 7%;
}
.form-input {
    width: 100px;
}
</style>
