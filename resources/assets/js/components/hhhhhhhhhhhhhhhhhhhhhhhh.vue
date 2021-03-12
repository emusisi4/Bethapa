<style scoped>
.bethapa-table-header {
    font-weight: bold;
    color: #806104;
    font-size: 1.1em;
    border-bottom: 1px solid rgb(3, 46, 10);
    margin-bottom: 20px;
    width: 100%;
}
.add-new {
    display: inline-block;
    float: right;
    font-size: 0.6em;
    /* padding: 0px; */
    background: #E86325;
    font-weight: bold;
    /* border: 1px solid black; */
    box-shadow: 0px 0px 0.5px black;
}
</style>

<template>

     <div class="card">
           
              <div class="card-header">
                <h3 class="card-title"><b> SETTINGS </b></h3>

               

               
              </div>
              <div class="bethapa-table-header"></div>
              <!-- /.card-header -->
              <div class="card-body table-responsive p-0">
              <div class="col-12 col-sm-12">
            <div class="card card-primary card-tabs">
              <div class="card-header p-0 pt-1">
                <ul class="nav nav-tabs" id="custom-tabs-one-tab" role="tablist">
                  <li class="nav-item">
                    <a class="nav-link active" id="custom-tabs-one-home-tab" data-toggle="pill" href="#custom-tabs-one-home" role="tab" aria-controls="custom-tabs-one-home" aria-selected="true">System Settings</a>
                  </li>
                  <li class="nav-item">
                    <a class="nav-link" id="custom-tabs-one-profile-tab" data-toggle="pill" href="#custom-tabs-one-profile" role="tab" aria-controls="custom-tabs-one-profile" aria-selected="false">Expenses</a>
                  </li>
                  <li class="nav-item">
                    <a class="nav-link" id="custom-tabs-one-messages-tab" data-toggle="pill" href="#custom-tabs-one-messages" role="tab" aria-controls="custom-tabs-one-messages" aria-selected="false">Messages</a>
                  </li>
                  <li class="nav-item">
                    <a class="nav-link" id="custom-tabs-one-settings-tab" data-toggle="pill" href="#custom-tabs-one-settings" role="tab" aria-controls="custom-tabs-one-settings" aria-selected="false">Settings</a>
                  </li>
                </ul>
              </div>
              <div class="card-body">
                <div class="tab-content" id="custom-tabs-one-tabContent">


                  <div class="tab-pane fade active show" id="custom-tabs-one-home" role="tabpanel" aria-labelledby="custom-tabs-one-home-tab">
                                 
<form @submit.prevent="SaveRoletoaddcomponent()">
                  
                  
                    <div class="form-group">
                  <label>Change role</label>
                    <select name ="roletoallow" v-model="form.roletoallow" id ="roletoallow" v-on:change="myClickEvent"  :class="{'is-invalid': form.errors.has('roletoallow')}">
                    <option value=" ">  </option>
                    <option v-for='data in brancheslist' v-bind:value='data.roleno'>{{ data.roleno }} - {{ data.name }}</option>

                    </select>
                    

                                <has-error :form="form" field="roletoallow"></has-error>

  <label>SELECTED  ROLE  :    </label>       <label> </label>

                                
                                </div>
                                  <button type="submit" id="submit" hidden="hidden" name= "submit" ref="myBtn" class="btn btn-primary btn-sm">Saveit</button>
                                </form>

                   
        <div class="row">
          <div class="col-md-5">
            <div class="card card-primary collapsed-card">
              <div class="card-header">
                <h3 class="card-title">Components Access</h3>

                <div class="card-tools">
                  <button type="button" class="btn btn-tool" data-card-widget="collapse"><i class="fas fa-plus"></i>
                  </button>
                </div>
                <!-- /.card-tools -->
              </div>
              <!-- /.card-header -->
              <div class="card-body" style="display: none;">
                
                 <div class="card-body table-responsive p-0">


    <div class="card">
             
               <div class ="bethapa-table-header"> <tr v-for="rolenameinactionsss in rolenameinaction.data" :key="rolenameinaction.id">
                <td>{{rolenameinactionsss.name}}. </td></tr> AUTHORISED COMPONENTS <button type="button" class="btn add-new btn-xs" @click="newModal" >Add More components </button></div>
              <!-- /.card-header -->
              <div class="card-body p-0">
                                               
                <table class="table table-striped">
                
                  <tbody>
                   <tr v-for="mydataObjectinfo in mydataObject.data" :key="mydataObjectinfo.id">
                <td>{{mydataObjectinfo.id}}. </td>
                       <td>{{mydataObjectinfo.componentto}}</td>
                     
                     <td>
                            
                    <button type="button" class="btn  bg-gradient-secondary btn-xs fas fa-trash-alt" @click="deleteRecord(mydataObjectinfo.id)"> Remove </button>
                      </td>
                    </tr>
                   
                  </tbody>
                </table>
              </div>
              <!-- /.card-body -->
            </div>


               
              </div>

                    
  




              </div>
              <!-- /.card-body -->
            </div>
            <!-- /.card -->
          </div>
          <!-- /.col -->
        
        </div>

         <div class="row">
          <div class="col-md-5">
            <div class="card card-primary collapsed-card">
              <div class="card-header">
                <h3 class="card-title">User Defefined Roles - Main Menus</h3>

                <div class="card-tools">
                  <button type="button" class="btn btn-tool" data-card-widget="collapse"><i class="fas fa-plus"></i>
                  </button>
                </div>
                <!-- /.card-tools -->
              </div>
              <!-- /.card-header -->
              <div class="card-body" style="display: none;">
                  <div class="card">
           <div class ="bethapa-table-header"> <tr v-for="rolenameinactionsss in rolenameinaction.data" :key="rolenameinaction.id">
                <td>{{rolenameinactionsss.name}}. </td></tr> AUTHORISED MAIN MENUS <button type="button" class="btn add-new btn-xs" @click="newModalmainmenu" >Add More Menus </button></div>
              <div class="card-body p-0">
                <br>
                

            
                <table class="table table-striped">
                
                  <tbody>
                   <tr v-for="mydataObjectinfomainmenu in mydataObjectmainmenu.data" :key="mydataObjectinfomainmenu.id">
                <td>{{mydataObjectinfomainmenu.component}}. </td>
                       <td>  <template v-if="mydataObjectmainmenu.maincomponent_submenus">	{{mydataObjectmainmenu.maincomponent_submenus.name}}</template></td>
                     
                     <td>
                            
                    <button type="button" class="btn  bg-gradient-danger btn-xs fas fa-trash-alt" @click="deleteRecord(mydataObjectinfomainmenu.id)"> Remove </button>
                      </td>
                    </tr>
                   
                  </tbody>
                </table>
              </div>
              <!-- /.card-body -->
            </div>
              </div>
              <!-- /.card-body -->
            </div>
            <!-- /.card -->
          </div>
          <!-- /.col -->
        
        </div>

   <div class="row">
          <div class="col-md-5">
            <div class="card card-primary collapsed-card">
              <div class="card-header">
                <h3 class="card-title">User Defefined Roles - Main Menus</h3>

                <div class="card-tools">
                  <button type="button" class="btn btn-tool" data-card-widget="collapse"><i class="fas fa-plus"></i>
                  </button>
                </div>
                <!-- /.card-tools -->
              </div>
              <!-- /.card-header -->
              <div class="card-body" style="display: none;">
                The body of the card
              </div>
              <!-- /.card-body -->
            </div>
            <!-- /.card -->
          </div>
          <!-- /.col -->
        
        </div>
                  </div>





                  <div class="tab-pane fade" id="custom-tabs-one-profile" role="tabpanel" aria-labelledby="custom-tabs-one-profile-tab">
                     Mauris tincidunt mi at erat gravida, eget tristique urna bibendum. Mauris pharetra purus ut ligula tempor, et vulputate metus facilisis. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Maecenas sollicitudin, nisi a luctus interdum, nisl ligula placerat mi, quis posuere purus ligula eu lectus. Donec nunc tellus, elementum sit amet ultricies at, posuere nec nunc. Nunc euismod pellentesque diam. 
                  </div>
                  <div class="tab-pane fade" id="custom-tabs-one-messages" role="tabpanel" aria-labelledby="custom-tabs-one-messages-tab">
                     Morbi turpis dolor, vulputate vitae felis non, tincidunt congue mauris. Phasellus volutpat augue id mi placerat mollis. Vivamus faucibus eu massa eget condimentum. Fusce nec hendrerit sem, ac tristique nulla. Integer vestibulum orci odio. Cras nec augue ipsum. Suspendisse ut velit condimentum, mattis urna a, malesuada nunc. Curabitur eleifend facilisis velit finibus tristique. Nam vulputate, eros non luctus efficitur, ipsum odio volutpat massa, sit amet sollicitudin est libero sed ipsum. Nulla lacinia, ex vitae gravida fermentum, lectus ipsum gravida arcu, id fermentum metus arcu vel metus. Curabitur eget sem eu risus tincidunt eleifend ac ornare magna. 
                  </div>
                  <div class="tab-pane fade" id="custom-tabs-one-settings" role="tabpanel" aria-labelledby="custom-tabs-one-settings-tab">
                     Pellentesque vestibulum commodo nibh nec blandit. Maecenas neque magna, iaculis tempus turpis ac, ornare sodales tellus. Mauris eget blandit dolor. Quisque tincidunt venenatis vulputate. Morbi euismod molestie tristique. Vestibulum consectetur dolor a vestibulum pharetra. Donec interdum placerat urna nec pharetra. Etiam eget dapibus orci, eget aliquet urna. Nunc at consequat diam. Nunc et felis ut nisl commodo dignissim. In hac habitasse platea dictumst. Praesent imperdiet accumsan ex sit amet facilisis. 
                  </div>
                </div>
              </div>
              <!-- /.card -->
            </div>
          </div>

                
              </div>
              

              <div class="card-footer clearfix">
                <ul class="pagination pagination-sm m-0 float-right">
                   
                </ul>
              </div>
              














 <!------ Modal for Pending Cash In ---->




<div class="modal fade" id="pendingcashIn" data-backdrop="static">
        <div class="modal-dialog">
          <div class="modal-content">
            <div class="modal-header">
              <h4 class="modal-title" v-show="!editmode">CASH IN</h4>
                
                 </div>
                      
<form @submit.prevent="approveCashin()">

            <div class="modal-body">
 
        
          <h3>Transfer Pending your Approval</h3>

                <div class ="bethapa-table-header"></div>
                  <h5>From : Office </h5>
                   <h5>Sender : </h5>
                   <h5>Date : </h5>
                   <h5>Amount : </h5>
                    <h5>Status : </h5>


 

        <div class="row">
          <div class="col-md-5">
            <div class="card card-primary collapsed-card">
              <div class="card-header">
                <h3 class="card-title">Expandable</h3>

                <div class="card-tools">
                  <button type="button" class="btn btn-tool" data-card-widget="collapse"><i class="fas fa-plus"></i>
                  </button>
                </div>
                <!-- /.card-tools -->
              </div>
              <!-- /.card-header -->
              <div class="card-body" style="display: none;">
                The body of the card
              </div>
              <!-- /.card-body -->
            </div>
            <!-- /.card -->
          </div>
          <!-- /.col -->
        
        </div>


            </div>
            <div class="modal-footer">
<div  v-if="pendingtransfer < 1" >
    
  <button v-show="!editmode" type="submit" class="btn btn-primary btn-sm">CONFIRM</button>

  </div>
  



                
       

      </div>
      
  </form>
          </div>
        
          <!-- /.modal-content -->
        </div>
        <!-- /.modal-dialog -->
</div>

































            
            
 <div class="modal fade" id="addNew">
        <div class="modal-dialog">
          <div class="modal-content">
            <div class="modal-header">
              <h4 class="modal-title" v-show="!editmode">Activate Components</h4>
                   <h4 class="modal-title" v-show="editmode">Update Record</h4>
              <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                <span aria-hidden="true">&times;</span>
              </button>
            </div>
                      
<form @submit.prevent="editmode ? updateRecord():createNewrecord()">

            <div class="modal-body">
 
<form @submit.prevent="SaveRecordbranch()">
  
  

                  <div class="form-group">
                  <label>ROLE</label>
                    <select name ="roleyouareaddingtocomponent" v-model="form.roleyouareaddingtocomponent" id ="roleyouareaddingtocomponent" v-on:change="myClickEvent2" class="form-control" :class="{'is-invalid': form.errors.has('roleyouareaddingtocomponent')}">
                    <option value=" ">  </option>
                    <option v-for='data in brancheslist' v-bind:value='data.roleno'>{{ data.roleno }} - {{ data.name }}</option>

                    </select>
                    

                                <has-error :form="form" field="roleyouareaddingtocomponent"></has-error>



                                
                                </div>

                                   <div class="form-group">
                  <label>COMPONENT</label>
                    <select name ="components" v-model="form.components" id ="components"  class="form-control" :class="{'is-invalid': form.errors.has('components')}">
                    <option value=" ">  </option>
                    <option v-for='data in componentslist' v-bind:value='data.sysname'>{{ data.sysname }} - {{ data.name }}</option>

                    </select>
                   

                                <has-error :form="form" field="components"></has-error>



                                
                                </div>
  
    <button type="submit" id="submit" hidden="hidden" name= "submit" ref="myBtn2" class="btn btn-primary btn-sm">Saveit</button>
                              
</form>
   






                
                 

            


            </div>
            <div class="modal-footer">
<div >
    
  <button v-show="!editmode" type="submit" class="btn btn-info btn-sm">Give Access</button>

  </div>
            <button v-show="editmode" type="submit" class="btn btn-success btn-sm">Update</button>



                
        <button  type="button" class="btn btn-danger btn-sm" data-dismiss="modal">Close</button>

      </div>
  </form>
          </div>
        
          <!-- /.modal-content -->
        </div>
        <!-- /.modal-dialog -->
      </div>





<div class="modal fade" id="addNewmainmenu">
        <div class="modal-dialog">
          <div class="modal-content">
            <div class="modal-header">
              <h4 class="modal-title" v-show="!editmode">Activate Mainmenu</h4>
                   <h4 class="modal-title" v-show="editmode">Update Record</h4>
              <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                <span aria-hidden="true">&times;</span>
              </button>
            </div>
                      
<form @submit.prevent="editmode ? updateRecord():createNewrecordmainmenu()">

            <div class="modal-body">
 
<form @submit.prevent="SaveRecordbranch()">
  
  

                  <div class="form-group">
                  <label>ROLE</label>
                    <select name ="roleyouareaddingtocomponent" v-model="form.roleyouareaddingtocomponent" id ="roleyouareaddingtocomponent" v-on:change="myClickEvent2" class="form-control" :class="{'is-invalid': form.errors.has('roleyouareaddingtocomponent')}">
                    <option value=" ">  </option>
                    <option v-for='data in brancheslist' v-bind:value='data.roleno'>{{ data.roleno }} - {{ data.name }}</option>

                    </select>
                    

                                <has-error :form="form" field="roleyouareaddingtocomponent"></has-error>



                                
                                </div>

                                   <div class="form-group">
                  <label>Main Menu</label>
                    <select name ="components" v-model="form.components" id ="components"  class="form-control" :class="{'is-invalid': form.errors.has('components')}">
                    <option value=" ">  </option>
                    <option v-for='data in mainmenulist' v-bind:value='data.id'>{{ data.id }} - {{ data.name }}</option>

                    </select>
                   

                                <has-error :form="form" field="components"></has-error>



                                
                                </div>
  
    <button type="submit" id="submit" hidden="hidden" name= "submit" ref="myBtn2" class="btn btn-primary btn-sm">Saveit</button>
                              
</form>
   






                
                 

            


            </div>
            <div class="modal-footer">
<div >
    
  <button v-show="!editmode" type="submit" class="btn btn-info btn-sm">Give Access</button>

  </div>
            <button v-show="editmode" type="submit" class="btn btn-success btn-sm">Update</button>



                
        <button  type="button" class="btn btn-danger btn-sm" data-dismiss="modal">Close</button>

      </div>
  </form>
          </div>
        
          <!-- /.modal-content -->
        </div>
        <!-- /.modal-dialog -->
      </div>





















            </div>
</template>

<script>
    export default {
        data(){
        return {
            editmode: false,
            mydataObject:{},
                clcash: null,
             
               
                brancheslist:{},
                rolenameinaction:{},
                  componentslist:{},
                    mainmenulist:{},
                  ///
                   mydataObjectmainmenu:{},
///dropdown
   


                form: new Form({
                                    id:'',
                                    branchname : '',
                                    location : '',
                                    contact : '',
                                    type : '',
                                    bio : '',
                                    photo : ''

            })
        }

        },
        methods:{
             formatPrice(value) {
        let val = (value/1).toFixed(0).replace('.', ',')
        return val.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",")
    },
    /// submiting the balancing record date and branch
  myClickEvent($event) { const elem = this.$refs.myBtn
            elem.click()
        },
         myClickEvent2($event) { const elem = this.$refs.myBtn2
            elem.click()
        },

          ////// drpdown
          

          /////////////////////////////////////////
// Our method to GET results from a Laravel endpoint
      getResults(page = 1) {
                        axios.get('api/currentbalancingrecords?page=' + page)
                          .then(response => {
                            this.mydataObject = response.data;
                          });
                      },
            updateRecord(){
    this.$Progress.start();
            /// viewing from the sonsole
            ///console.log('Edidint data');
/// calling the function to update the data
this.form.put('api/currentbalancingrecords/'+this.form.id)
  .then(()=> {
    // on success
   $('#addNew').modal('hide');
    swal.fire(
        'Update!',
        'Your file has been updated.',
        'success'
      )
      this.$Progress.finish();
    Fire.$emit('AfterAction');

  })


  .catch(()=>{
 this.$Progress.fail();
  });

            },
            editModal(mydataObject){
                this.editmode = true;
                 this.form.clear();
        this.form.reset();
        this.form.fill(mydataObject);
$('#addNew').modal('show');
            },
                newModalmainmenu(){
                      this.editmode = false;
                 this.form.clear();
        this.form.reset();
$('#addNewmainmenu').modal('show');
            },
            deleteRecord(id){
                swal.fire({
  title: 'Are you sure?',
  text: "You won't be able to revert this!",
  icon: 'warning',
  showCancelButton: true,
  confirmButtonColor: '#3085d6',
  cancelButtonColor: '#d33',
  confirmButtonText: 'Yes, delete it!'
}).then((result) => {
    if(result.value){
                                  this.form.delete('api/saveaccesstovuecomponent/'+id).then(()=>{

                                                                                swal.fire(
                                                                                  'Deleted!',
                                                                                  'Your file has been deleted.',
                                                                                  'success'
                                                                                )
                                                          Fire.$emit('AfterAction');
                                                      }).cathch(()=>{
                                                        
                                   swal.fire("Failed!", "There was Something Wrong.", "Warning");
                                                      });
    }
                     
})

            },
               newModal(){
                      this.editmode = false;
                 this.form.clear();
        this.form.reset();
$('#addNew').modal('show');
            },
            deleteRecord(id){
                swal.fire({
  title: 'Are you sure?',
  text: "You won't be able to revert this!",
  icon: 'warning',
  showCancelButton: true,
  confirmButtonColor: '#3085d6',
  cancelButtonColor: '#d33',
  confirmButtonText: 'Yes, delete it!'
}).then((result) => {
    if(result.value){
                                  this.form.delete('api/saveaccesstovuecomponent/'+id).then(()=>{

                                                                                swal.fire(
                                                                                  'Deleted!',
                                                                                  'Your file has been deleted.',
                                                                                  'success'
                                                                                )
                                                          Fire.$emit('AfterAction');
                                                      }).cathch(()=>{
                                                        
                                   swal.fire("Failed!", "There was Something Wrong.", "Warning");
                                                      });
    }
                     
})

            },
            loadDatarecords(){
   axios.get("api/authorisedcomponents").then(({ data }) => (this.mydataObject = data));

      axios.get("api/getmanmaderoles").then(({ data }) => (this.brancheslist = data));
      // axios.get("api/getrolenameinaction").then(({ data }) => (this.rolenameinaction = data));
      axios.get("api/getcomponentslistmissing").then(({ data }) => (this.componentslist = data));
       axios.get("api/getmainmenus").then(({ data }) => (this.mainmenulist = data));
     //  axios.get("api/getrolenameinaction").then(({ data }) => (this.thyrecord = data));
    axios.get("api/getrolenameinaction").then(({ data }) => (this.rolenameinaction = data));
 ///
  axios.get("api/authorisedmainmenus").then(({ data }) => (this.mydataObjectmainmenu = data));
  

            },
            createNewrecord(){

  this.$Progress.start();
this.form.post('api/saveaccesstovuecomponent')
.then(()=>{


Fire.$emit('AfterAction');

$('#addNew').modal('show');

Toast.fire({
  icon: 'success',
  title: 'Record Added Successfully'
});

  this.$Progress.finish();
})
.catch(()=>{

})




            },

 createNewrecordmainmenu(){

  this.$Progress.start();
this.form.post('api/savemainmenuaccess')
.then(()=>{


Fire.$emit('AfterAction');

$('#addNewmainmenu').modal('show');

Toast.fire({
  icon: 'success',
  title: 'Record Added Successfully'
});

  this.$Progress.finish();
})
.catch(()=>{

})




            },


  SaveRoletoaddcomponent (){

  
this.form.post('api/roletobalance');
 axios.get("api/authorisedcomponents").then(({ data }) => (this.mydataObject = data));
  axios.get("api/authorisedmainmenus").then(({ data }) => (this.mydataObjectmainmenu = data));
 axios.get("api/getcomponentslistmissing").then(({ data }) => (this.componentslist = data));



            },


  SaveRecordbranch (){

  
this.form.post('api/roleaddcomponent');
 axios.get("api/getcomponentslistmissing").then(({ data }) => (this.componentslist = data));
  axios.get("api/getcomponentslistmissing").then(({ data }) => (this.componentslist = data));
}



        }, 

           

      
        created() {
          this.loadDatarecords();



          
  axios.get("api/getcomponentslistmissing").then(({ data }) => (this.componentslist = data));
 Fire.$on('AfterAction', () =>{
this.loadDatarecords();
      });
        //  setInterval(() =>this.loadDatarecords(),3000);
        }
    }
</script>
