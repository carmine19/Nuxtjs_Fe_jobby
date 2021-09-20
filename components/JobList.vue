<template>


    <div class="container box-job-list mx-auto px-2 mt-10">
   <div class="box-title">
      <h1 class="text-center text-indigo-500">joblist</h1>
   </div>
   <div class="py-8">
      <div class="-mx-4 sm:-mx-8 px-4 sm:px-8 py-4 overflow-x-auto">
         <div class="inline-block min-w-full shadow rounded-lg overflow-hidden">
            <table class="min-w-full leading-normal">
               <thead>
                  <tr>
                     <th class="px-5 py-3 bg-white  border-b border-gray-200 text-gray-800  text-left text-sm uppercase font-normal"
                        scope="col">
                        titolo
                     </th>
                     <th class="px-5 py-3 bg-white  border-b border-gray-200 text-gray-800  text-left text-sm uppercase font-normal"
                        scope="col">
                        descrizione
                     </th>
                     <th class="px-5 py-3 bg-white  border-b border-gray-200 text-gray-800  text-left text-sm uppercase font-normal"
                        scope="col">
                        inizio attività
                     </th>
                     <th class="px-5 py-3 bg-white  border-b border-gray-200 text-gray-800  text-left text-sm uppercase font-normal"
                        scope="col">
                        durata
                     </th>
                     <th class="px-5 py-3 bg-white  border-b border-gray-200 text-gray-800  text-left text-sm uppercase font-normal"
                        scope="col">
                        compenso orario
                     </th>
                     <th class="px-5 py-3 bg-white  border-b border-gray-200 text-gray-800  text-left text-sm uppercase font-normal"
                        scope="col">
                        autore
                     </th>
                  </tr>
               </thead>
               <tbody>
                  <tr v-for="(job, index) in jobList.data" :key="index">
                     <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
                        <div class="flex items-center">
                           <div class="flex-shrink-0">
                              <a class="block relative" href="#">
                              </a>
                           </div>
                           <div class="ml-3">
                              <p class="text-gray-900 whitespace-no-wrap">
                                 {{ job.title }}
                              </p>
                           </div>
                        </div>
                     </td>
                     <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
                        <p class="text-gray-900 whitespace-no-wrap">
                           {{ job.description.substring(0, 25) + '...' }}
                        </p>
                     </td>
                     <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
                        <p class="text-gray-900 whitespace-no-wrap">
                           {{ job.start_activity_date }}
                        </p>
                     </td>
                     <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
                        <span
                           class="relative inline-block px-3 py-1 font-semibold text-green-900 leading-tight">
                        <span aria-hidden="true"
                           class="absolute inset-0 bg-green-200 opacity-50 rounded-full">
                        </span>
                        <span class="relative">
                        {{ job.duration_activity }} <span>{{ job.duration_activity < 1 ? 'm' : 'h' }}</span>
                        </span>
                        </span>
                     </td>
                     <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
                        <a class="text-indigo-600 hover:text-indigo-900" href="#">
                        {{ job.price }} <span>€</span>
                        </a>
                     </td>
                     <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
                        <NuxtLink :to=" /author/ + job.author_id" class="btn btn-primary" tag="a">{{
                           job.author_name
                           }}
                        </NuxtLink>
                     </td>
                  </tr>
               </tbody>
            </table>
         </div>
      </div>
   </div>
</div>



</template>

<script>
import axios from "axios";
export default {
    name: "JobList",

    data() {
        return {
            jobList: [], page: '',
        }
    },
    methods: {
         getJob() {
            axios.get('http://127.0.0.1:8000/api/jobs')
                .then((response) => {
                    console.log(response.data)
                    this.jobList = response.data
                }).catch(error => console.log(error));
        },

    },

    created() {
        this.getJob()
    }
}
</script>

<style scoped>

.text-green-900 {
    font-size: 10px;
}

.box-title h1 {
    text-transform: uppercase;
    font-size: 35px;
}
</style>
