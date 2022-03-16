<template>
  <div id="app" class="container my-3">
    <h3>Tutorials CRUD API</h3>

    <div class="card mt-3">
      <div class="card-header"> GET requests </div>
      <div class="card-body">
        <div class="input-group input-group-sm">
          <button class="btn btn-sm btn-primary" @click="getAllData">Get All</button>

          <input type="text" ref="get_id" class="form-control ml-2" placeholder="Id" />
          <div class="input-group-append">
            <button class="btn btn-sm btn-primary" @click="getDataById">Get by Id</button>
          </div>

          <input type="text" ref="get_title" class="form-control ml-2" placeholder="Title" />
          <div class="input-group-append">
            <button class="btn btn-sm btn-primary" @click="getDataByTitle">Find By Title</button>
          </div>

          <button class="btn btn-sm btn-warning ml-2" @click="clearGetOutput">Clear</button>
        </div>   
        
        <div v-if="getResult" class="alert alert-secondary mt-2" role="alert"><pre>{{getResult}}</pre></div>
        </div>
      </div>

    <div class="card mt-3">
      <div class="card-header">POST Requests</div>
      <div class="card-body">
        <div class="form-group">
          <input type="text" class="form-control" ref="post_title" placeholder="Title" />
        </div>
        <div class="form-group">
          <input type="text" class="form-control" ref="post_description" placeholder="Description" />
        </div>
        <button class="btn btn-sm btn-primary" @click="postData">Post Data</button>
        <button class="btn btn-sm btn-warning ml-2" @click="clearPostOutput">Clear</button>

        <div v-if="postResult" class="alert alert-secondary mt-2" role="alert"><pre>{{postResult}}</pre></div>
      </div>
    </div>

    <div class="card mt-3">
        <div class="card-header">PUT Requests</div>
          <div class="card-body">
            <div class="form-group">
              <input type="text" class="form-control" ref="put_id" placeholder="Id" />
            </div>
            <div class="form-group">
              <input type="text" class="form-control" ref="put_title" placeholder="Title" />
            </div>
            <div class="form-group">
              <input type="text" class="form-control" ref="put_description" placeholder="Description" />
            </div>
            <div class="form-check mb-2">
              <input type="checkbox" class="form-check-input" ref="put_published" />
              <label class="form-check-label" for="put_published">Publish</label>
            </div>
            <button class="btn btn-sm btn-primary" @click="putData">Update Data</button>
            <button class="btn btn-sm btn-warning ml-2" @click="clearPutOutput">Clear</button>

            <div v-if="putResult" class="alert alert-secondary mt-2" role="alert"><pre>{{putResult}}</pre></div>
          </div>
        </div>


      <div class="card mt-3">
        <div class="card-header">DELETE Requests</div>
        <div class="card-body">
          <div class="input-group input-group-sm">
            <button class="btn btn-sm btn-danger" @click="deleteAllData">Delete All</button>

            <input type="text" ref="delete_id" class="form-control ml-2" placeholder="Id" />
            <div class="input-group-append">
              <button class="btn btn-sm btn-danger" @click="deleteDataById">Delete by Id</button>
            </div>

           <button class="btn btn-sm btn-warning ml-2" @click="clearDeleteOutput">Clear</button>
         </div>    
        
          <div v-if="deleteResult" class="alert alert-secondary mt-2" role="alert"><pre>{{deleteResult}}</pre></div>      
        </div>
      </div>

    </div>
</template>

<script>

import http from "./http-common";

export default {
  name: "App",
  data() {
    return {
      getResult: null,
      postResult: null,
      putResult: null,
      deleteResult: null,
    }
  },
  methods: {
    formatApiResponse(res) {
      return JSON.stringify(res, null, 2);
    },

    async getAllData() {
      try {
        const res = await http.get("/tutorials");

        const result = {
          status: res.status + "-" + res.statusText,
          headers: res.headers,
          data: res.data,
        };

        this.getResult = this.formatApiResponse(result);
      } catch(err) {
        this.getResult = this.formatApiResponse(err.response?.data) || err;
      }
    },

    async getDataById() {

    },

    async getDataByTitle() {

    },

    async postData() {

    },

    async putData() {

    },

    async deleteAllData() {

    },

    async deleteDataById() {

    },

    clearGetOutput() {
      this.getResult = null;

    },

    clearPostOutput() {
      this.postResult = null;
    },
    
    clearPutOutput() {
      this.putResult = null;
    },
    
    clearDeleteOutput() {
      this.deleteResult = null;
    } 
  }
}
</script>


<style>
#app {
  max-width: 600px;
  margin: auto;
}
</style>