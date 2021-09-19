<template>

    <div class="main">
   <div class="container box-job-list mx-auto px-2">
      <div class="box-title">
         <h1 class="text-center text-indigo-500">joblist</h1>
      </div>
      <div class="py-8">
         <div class="-mx-4 sm:-mx-8 px-4 sm:px-8 py-4 overflow-x-auto">
            <div class="inline-block min-w-full shadow rounded-lg overflow-hidden">
               <table class="min-w-full leading-normal">
                  <thead>
                     <tr>
                        <th scope="col"
                           class="px-5 py-3 bg-white  border-b border-gray-200 text-gray-800  text-left text-sm uppercase font-normal">
                           titolo
                        </th>
                        <th scope="col"
                           class="px-5 py-3 bg-white  border-b border-gray-200 text-gray-800  text-left text-sm uppercase font-normal">
                           descrizione
                        </th>
                        <th scope="col"
                           class="px-5 py-3 bg-white  border-b border-gray-200 text-gray-800  text-left text-sm uppercase font-normal">
                           inizio attività
                        </th>
                        <th scope="col"
                           class="px-5 py-3 bg-white  border-b border-gray-200 text-gray-800  text-left text-sm uppercase font-normal">
                           durata
                        </th>
                        <th scope="col"
                           class="px-5 py-3 bg-white  border-b border-gray-200 text-gray-800  text-left text-sm uppercase font-normal">
                           compenso orario
                        </th>
                        <th scope="col"
                           class="px-5 py-3 bg-white  border-b border-gray-200 text-gray-800  text-left text-sm uppercase font-normal">
                           autore
                        </th>
                     </tr>
                  </thead>
                  <tbody>
                     <tr v-for="job in jobList.data">
                        <JobList :user_id="job.user_id"
                                 :title="job.title"
                                 :description="job.description"
                                 :start_activity_date="job.start_activity_date"
                                 :duration_activity="job.duration_activity"
                                 :price="job.price"
                                 :author_name="job.author_name"/>
                     </tr>
                  </tbody>
               </table>
               <!--   <div class="px-5 bg-white py-5 flex flex-col xs:flex-row items-center xs:justify-between">
                  <div class="flex items-center">
                      <button type="button" class="w-full p-4 border text-base rounded-l-xl text-gray-600 bg-white hover:bg-gray-100">
                          &lt;
                      </button>

                      <button type="button" class="w-full px-4 py-2 border-t border-b text-base text-indigo-500 bg-white hover:bg-gray-100 ">

                      </button>

                      <a href="" type="button" class="w-full p-4 border-t border-b border-r text-base  rounded-r-xl text-gray-600 bg-white hover:bg-gray-100">
                          >
                      </a>
                  </div>
                  </div> -->
            </div>
         </div>
      </div>
   </div>
</div>

</template>

<script>

import JobList from "../components/JobList";
import axios from "axios";

export default {
    components: {JobList},

    data() {
        return {
            jobList: [],

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

.box-title h1 {
    text-transform: uppercase;
    font-size: 35px;
}


</style>
