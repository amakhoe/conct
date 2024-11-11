<template>
  <TopNav />
<NavBar />
      <section class="py-24 bg-primary">
      <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
        <div class="grid lg:grid-cols-2 grid-cols-1 gap-x-24">
            <div class="flex items-center lg:mb-0 mb-10">
                <div class="">
                    <h4 class="text-white tracking-wider text-base font-bold leading-6 mb-4 lg:text-left text-center">Contact Us</h4>
                    <h2 class="text-white font-manrope text-4xl font-bold leading-10 mb-9 lg:text-left text-center">Reach Out To Us</h2>
                    <form action="" @submit.prevent="submitForm" class="bg-white rounded p-10 mt-5 mb-6">                
                      <div class="mb-4">
                        <label class="font-bold">Nome</label>
                        <input v-model="formData.name" type="text" 
                         class="w-full h-14 shadow-sm text-gray-600 placeholder-text-400 text-lg font-normal leading-7 rounded border border-gray-300 focus:outline-none py-2 px-4 mb-8" placeholder="Nome">
                       
                         <span v-for="error in v$.name.$errors" :key="error.$uid" 
                        class="text-red-500 mt-2 text-sm">{{ error.$message }}</span>
                      </div>
                      <div class="mb-4">
                        <label class="font-bold">Email</label>  
                        <input v-model="formData.email" type="email" class="w-full h-14 shadow-sm text-gray-600 placeholder-text-400 text-lg font-normal leading-7 rounded border border-gray-300 focus:outline-none py-2 px-4 mb-8" placeholder="Email">
                        <div class="mt-1">
                          <span v-for="error in v$.email.$errors" :key="error.$uid" class="text-red-500 text-sm">{{ error.$message }}</span>
                        </div> 
                        
                         
                        </div>
                        <div class="mb-2">
                          <label class="font-bold mt-2">Texto</label> 
                         <textarea v-model="formData.texto" name="" id="text" 
                         class="w-full h-48 shadow-sm resize-none text-gray-600 placeholder-text-400 text-lg font-normal leading-7 rounded-2xl border border-gray-300 focus:outline-none px-4 py-4 mb-8" placeholder="Deixe tua mensagem"></textarea>
                         <span v-for="error in v$.texto.$errors" :key="error.$texto" class="text-red-500 mt-2 text-sm">{{ error.$message }}</span>
                         </div>
                         <button class="w-full h-12 text-center text-white text-base font-semibold leading-6 rounded-full bg-indigo-600 shadow transition-all duration-700 hover:bg-indigo-800">Submit</button>
                    </form>
                    <label class="text-white">For any question Contact our 24/7 <span class="text-pink-500">client line</span></label>
                </div>
            </div>
      </div>
    </div>
</section>
<RodApe />                                        
</template>

<script setup>
import NavBar from '@/components/NavBar.vue';
import TopNav from '@/components/TopNav.vue';
import RodApe from '@/components/RodApe.vue';

import useVuelidate from '@vuelidate/core';
import { required } from '@vuelidate/validators';
import { reactive } from 'vue';




const formData = reactive({
  name: "",
  email: "",
  texto: "",
});

const rules = {
  name: {required},
  email: {required},
  texto: {required}
};

const v$ = useVuelidate(rules, formData);

const submitForm = async () => {
  const result = await v$.value.$validate();
  if (result) {
    alert("success, formulario enviado com sucesso")
  }
  else {
    alert("error, formulario nao enviado")
  }
}





</script>

