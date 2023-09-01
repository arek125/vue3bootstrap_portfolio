<script setup lang="ts">

import {ref} from 'vue'
const formValid = ref<boolean>(true)
const formSend = ref<boolean>(false)
const formCloseButton = ref<any>(null)

const form = ref({
    name: "",
    surname:"",
    email:"",
    accept: false
})

const mailRegex = new RegExp('[a-z0-9]+@[a-z]+.[a-z]{2,3}');

const sendForm = ()=>{
    if(form.value.name && form.value.surname && mailRegex.test(form.value.email) && form.value.accept){
        formValid.value = true
        console.log(JSON.stringify(form.value))
        clearForm()
        formSend.value = true
        setTimeout(() => {
            formSend.value = false
            formCloseButton.value.click()
        }, 5000)
    }else
        formValid.value = false
    
}

const clearForm = ()=> {
    form.value.name = ""
    form.value.surname = ""
    form.value.email = ""
    form.value.accept = false
}


</script>

<template>
<div>
    <div class="modal fade" id="contactModalCenter" tabindex="9" data-bs-backdrop="static" aria-labelledby="contactModalCenterModalCenterTitle" style="display: none;" aria-hidden="true">
        <div class="modal-dialog modal-lg modal-dialog-centered">
            <div class="modal-content">
                <div class="d-flex justify-content-end">
                    <button type="button" class="btn-close" ref="formCloseButton" data-bs-dismiss="modal" aria-label="Close" style="margin: 10px 30px;"></button>
                </div>
                <div class="modal-body d-flex justify-content-center" style="padding: 0px 150px 25px;">
                    <div>
                        <div class="mb-3 formSection">
                            <label for="FormControlInput1" class="form-label">IMIĘ<span class="redText">*</span></label>
                            <input type="text" v-model="form.name" class="form-control" id="FormControlInput1" placeholder=" - wpisz - ">
                        </div>
                        <div class="mb-3 formSection">
                            <label for="FormControlInput2" class="form-label">NAZWISKO<span class="redText">*</span></label>
                            <input type="text" v-model="form.surname" class="form-control" id="FormControlInput2" placeholder=" - wpisz - ">
                        </div>
                        <div class="mb-3 formSection">
                            <label for="FormControlInput3" class="form-label">ADRES E-MAIL<span class="redText">*</span></label>
                            <input type="email" v-model="form.email" class="form-control" id="FormControlInput3" placeholder=" - wpisz - ">
                        </div>
                        <div class="mb-3 formSection"><span class="redText">*</span> - pola wymagane</div>
                        <div class="form-check mb-3 formSection">
                            <input class="form-check-input" v-model="form.accept" type="checkbox" value="" id="flexCheckDefault">
                            <label class="form-check-label" for="flexCheckDefault">
                                Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s
                            </label>
                        </div>
                        <button type="button" @click="sendForm" class="btn btn-primary contactButton">WYŚLIJ</button>
                        <span class="redText mt-5" v-show="!formValid">Proszę uzupełnić wymagane pola !</span>
                        <span class="greenText mt-5" v-show="formSend">Formularz został wysłany !</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<style lang="scss">
.contactButton{
    color: white !important;
    width: 100%;
}
.contactButton:hover{
    color: white !important;
    letter-spacing: 0.3em;
}
.redText {
    color: var(--bs-primary);
}
.greenText {
    color: green;
}
.form-label{
    letter-spacing: 0.2em;
    color: var(--bs-secondary);
    font-size: small;
}
.form-control::placeholder{
    color: var(--bs-secondary) !important;
    font-size: small;
    letter-spacing: 0.2em;
}
.formSection{
    text-align: left
}
</style>