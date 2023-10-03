<template>
  <div class="row">
    <div class="col-md-6">
      <card>
        <h4 slot="header">Lista de usuarios</h4>
        <base-alert type="info">
          <span>This is a plain notification</span>
        </base-alert>
        <base-alert type="info" dismissible>
          <span>This is a plain notification</span>
        </base-alert>
        <base-alert type="info" dismissible with-icon>
          <span data-notify="icon" class="tim-icons icon-bell-55"></span>
          <span data-notify="message">This is a notification with close button and icon.</span>
        </base-alert>
        <base-alert type="info" dismissible with-icon>
          <span data-notify="icon" class="tim-icons icon-bell-55"></span>
          <span data-notify="message">This is a notification with close button and icon and have many lines. You can see that the icon and the close button are always vertically aligned. This is a beautiful notification. So you don't have to worry about the style.</span>
        </base-alert>
      </card>
    </div>
    <div class="col-md-6">
      <card>
        <h4 slot="header">Notifications states</h4>
        <base-alert type="primary" dismissible>
          <span><b> Primary - </b> This is a regular notification made with ".alert-primary"</span>
        </base-alert>
        <base-alert type="info" dismissible>
          <span><b> Info - </b> This is a regular notification made with ".alert-info"</span>
        </base-alert>
        <base-alert type="success" dismissible>
          <span><b> Success - </b> This is a regular notification made with ".alert-success"</span>
        </base-alert>
        <base-alert type="warning" dismissible>
          <span><b> Warning - </b> This is a regular notification made with ".alert-warning"</span>
        </base-alert>
        <base-alert type="danger" dismissible>
          <span><b> Danger - </b> This is a regular notification made with ".alert-danger"</span>
        </base-alert>
      </card>
    </div>
    <div class="col-md-12">
      <card>
        <div class="places-buttons">
          <div class="row">
            <div class="col-md-6 ml-auto mr-auto text-center">
              <h4 class="card-title">
                Notifications Places
                <p class="category">Click to view notifications</p>
              </h4>
            </div>
          </div>
          <div class="row">
            <div class="col-lg-8 ml-auto mr-auto">
              <div class="row">
                <div class="col-md-4">
                  <base-button type="primary" block @click="notifyVue('top', 'left')">Top Left</base-button>
                </div>
                <div class="col-md-4">
                  <base-button type="primary" block @click="notifyVue('top', 'center')">Top Center</base-button>
                </div>
                <div class="col-md-4">
                  <base-button type="primary" block @click="notifyVue('top', 'right')">Top Right</base-button>
                </div>
              </div>
            </div>
          </div>
          <div class="row">
            <div class="col-lg-8 ml-auto mr-auto">
              <div class="row">
                <div class="col-md-4">
                  <base-button type="primary" block @click="notifyVue('bottom', 'left')">Bottom Left</base-button>
                </div>
                <div class="col-md-4">
                  <base-button type="primary" block @click="notifyVue('bottom', 'center')">Bottom Center</base-button>
                </div>
                <div class="col-md-4">
                  <base-button type="primary" block @click="notifyVue('bottom', 'right')">Bottom Right</base-button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </card>
    </div>
  </div>
</template>
<script>
  import NotificationTemplate from './Notifications/NotificationTemplate';
  import { BaseAlert } from '@/components';
  export default {
    created:function(){
    this.createEntity();
    this.readEntity();
    },
    methods: {
    readEntity(){
    fetch('https://redb.qsystems.co/QS3100/QServlet?operation=queryEntityByTenancy&tna=2&key=29ee694f-0e5b-43e4-8fa4-3ba865f7d8dd')
    
    .then(respuesta=>respuesta.json())
    .then((datosRespuesta)=>{
    console.log(datosRespuesta)
    })
    .catch(console.log)
    },
    createEntity(){
    let operation="SaveEntity"
    let tna=6
    let key="11e2e476-717b-4898-ac02-693abdecdc9b"
    let nameEntity="Hospital ALMA"
    let phoneEntity="6018259654"
    let adressEntity="Kra 23 No. 85 - 67"
    fetch('https://redb.qsystems.co/QS3100/QServlet?operation='+operation+'&tna='+tna+'&key='+key+'&nameEntity='+nameEntity+'&phoneEntity='+phoneEntity+'&adressEntity='+adressEntity)
    
    .then(respuesta=>respuesta.json())
    .then((datosRespuesta=>{
    console.log(datosRespuesta);
    }))
    }
    }
    }

    
</script>
<style>
</style>
