<template>
    <div class="component">
        <h1>The User Component</h1>
        <p>I'm an awesome User!</p>
        <button @click="changeMyname">Change my name</button>
        <p>USer Name {{ name }}</p>
        <p>USer Age {{ age }}</p>
        <hr>
        <div class="row">
            <div class="col-xs-12 col-sm-6">
                <app-user-detail 
                    :myName="name"
                    @nameWasReset="name = $event"
                    :resetFn="resetName"
                    :userAge="age"></app-user-detail>
            </div>
            <div class="col-xs-12 col-sm-6">
                <app-user-edit 
                    :userAge="age"
                    @ageWasEdited="age = $event"></app-user-edit>
            </div>
        </div>
    </div>
</template>

<script>
    import UserDetail from './UserDetail.vue';
    import UserEdit from './UserEdit.vue';

    export default {
      props: [name],
      data() {
        return {
          name: 'Maximilian',
          age: 27
        }
      },
      methods: {
        changeMyname() {
          this.name = 'Anna'
        },
        resetName() {
          this.name = 'Maximilian'
        }
      },
        components: {
            appUserDetail: UserDetail,
            appUserEdit: UserEdit
        },
    }
</script>

<style scoped>
    div {
        background-color: lightblue;
    }
</style>
