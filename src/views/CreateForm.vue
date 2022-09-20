<template>
  <div class="container">
    <form class="row g-3 needs-validation" novalidate>
  <div class="col-md-4">
    <label for="validationCustom01" class="form-label">Nom manga</label>
    <input v-model='manga.name' type="text" class="form-control" id="validationCustom01" value="Mark" required>
    <div class="valid-feedback">
      Looks good!
    </div>
  </div>
  <div class="col-md-4">
    <label for="validationCustom02" class="form-label">Editeur</label>
    <input v-model='manga.editor' type="text" class="form-control" id="validationCustom02" value="Otto" required>
    <div class="valid-feedback">
      Looks good!
    </div>
  </div>
  <div class="col-md-3">
    <label for="validationCustom04" class="form-label">Manga Type</label>
    <select v-model='manga.type' class="form-select" id="validationCustom04" required>
      <option selected value="">Choose...</option>
      <option v-for="type in mangaType" :key='type'>{{type}}</option>
    </select>
    <div class="invalid-feedback">
      Please select a valid state.
    </div>
  </div>

  <div class="col-12">
    <div class="form-check">
      <input v-model='manga.ebook' class="form-check-input" type="checkbox" value="" id="invalidCheck" required>
      <label class="form-check-label" for="invalidCheck">
        Available in ebook
      </label>
     
    </div>
  </div>
  
  <div class="col-12">
    <button @click='handleSaveBtn' class="btn btn-primary" type="button">Create or Edit</button>
  </div>
</form>
  </div>

</template>

<script>
 
  export default {
    name: 'CreateForm',
    data:()=>({
        onEdit:false,
        mangaType:['Seinen','Josei','Shojo'],
        manga:{
          name:'',
          editor:'',
          type:'Seinen',
          ebook:true
        }
    }),
    methods:{
     async handleSaveBtn(){
        
        console.log('Je vais creer > ', this.manga)
        // > je vais faire mon POST sur mon api 
       
        if(this.onEdit){
          await this.editOneManga()
        }else{
          await this.createNewManga()
        }
      },
      setMangaType(){

      },
      async createNewManga(){
        console.warn('ici en create')
        console.log(this.manga)
      }

    },
    async created(){
      this.setMangaType()
    }
  }
  </script>