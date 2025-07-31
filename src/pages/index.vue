<template>
  <v-app>
    <v-navigation-drawer v-model="isDrawerOpen">
      <v-list>
        <v-list-subheader>Menu</v-list-subheader>
        <v-list-item prepend-icon="mdi-home">Home</v-list-item>
        <v-list-item prepend-icon="mdi-account">Usuário</v-list-item>
        <v-list-item to="/table" prepend-icon="mdi-table" link>Tabelas</v-list-item>


        <v-list-group value="Clientes">
          <template #activator="{ props }">
            <v-list-item v-bind="props" prepend-icon="mdi-account-circle">Clientes</v-list-item>
          </template>

          <v-list-item prepend-icon="mdi-currency-usd">Faturamento</v-list-item>
          <v-list-item prepend-icon="mdi-chart-line">Relatório</v-list-item>
        </v-list-group>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar flat class="bg-blue border-b">
      <v-app-bar-nav-icon @click="isDrawerOpen = !isDrawerOpen"></v-app-bar-nav-icon>
      <v-app-bar-title>Meu app</v-app-bar-title>


      <template #append>
        <v-btn class="text-none" stacked>
          <v-badge color="error" content="2">
            <v-icon>mdi-bell-outline</v-icon>
          </v-badge>
          <v-menu activator="parent">
            <v-card class="pa-3">
              <v-list>
                <vi-list-item>
                  <v-list-item-title>Meus favoritos</v-list-item-title>
                  <v-list-item-subtitle> Todas as compras realizadas nos ultimos meses.</v-list-item-subtitle>
                </vi-list-item>
              </v-list>

              <v-divider></v-divider>

              <v-list>
                <vi-list-item>
                  <v-list-item-title>Meus favoritos</v-list-item-title>
                  <v-list-item-subtitle> Todas as compras que foram entregues.</v-list-item-subtitle>
                </vi-list-item>
              </v-list>
            </v-card>
          </v-menu>
        </v-btn>


        <v-menu open-on-hover>
          <template #activator="{ props }">
            <v-avatar v-bind="props">
              <v-img cover
                src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRoWCusn6VbpkhcukHuYOvhMfVOUCiHJ818Yg&s"></v-img>
            </v-avatar>
          </template>

          <v-card min-width="200px">
            <v-list :lines="false" density="compact" nav>
              <v-list-item prepend-icon="mdi-account-outline">
                <v-list-item-title>Meu perfil</v-list-item-title>
              </v-list-item>

              <v-list-item prepend-icon="mdi-heart">
                <v-list-item-title>Meus favoritos</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-card>
        </v-menu>
      </template>
    </v-app-bar>
    <v-main>
      <v-container>
        <div class="d-flex justify-space-between">
          <h1>DashBoard</h1>
          <v-card-tilte>
            <v-btn
             color="surface-variant" 
             text="Adicionar Usuário" 
             variant="flat" 
             @click="isDialogOpen = true"></v-btn>
            <v-dialog 
            v-model="isDialogOpen" 
            width="auto">
              <v-card 
              min-width="900px"
              >
              <v-card-title>Adicionar usuário</v-card-title>
                <v-card-text>
                  <v-row>
                    <v-col>
                      <v-text-field label="Nome" variant="outlined"></v-text-field>
                    </v-col>
                    <v-col>
                      <v-text-field label="Email"></v-text-field>
                    </v-col>
                  </v-row>

                  <v-select label="Cargo"
                    :items="['Admin', 'Gerente', 'Visitante']"></v-select>
                </v-card-text>

                  <v-card-actions class="d-flex align-center justify-center">
                    <v-btn 
                    variant="tonal" 
                    color="error"
                    @click="dialogClose"
                     >Cancelar</v-btn>
                    <v-btn variant="tonal" color="success">Salvar</v-btn>
                  </v-card-actions>
              </v-card>
            </v-dialog>
          </v-card-tilte>
        </div>
        <v-row class="d-flex flex-column flex-sm-row">
          <v-col cols="12" xs="12" sm="6" md="4" lg="3">
            <v-card>
              <v-img class="align-end text-white pl-3 pb-3" src="../assets/image-card.jpg">
                Top 10 lugares para viajar
              </v-img>
              <v-card-subtitle class="mt-3">
                Na Europa
              </v-card-subtitle>
              <v-card-text>
                <div>Whitsunday Island, Whitsunday Islands</div>
              </v-card-text>
              <v-card-actions>
                <v-btn color="orange" text="Share"></v-btn>

                <v-btn color="orange" prepend-icon="$vuetify">Explore</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>

          <v-col cols="12" xs="12" sm="6" md="4" lg="3">
            <v-card w-33>
              <v-img class="align-end text-white pl-3 pb-3" src="../assets/image-card.jpg">
                Top 10 lugares para viajar
              </v-img>
              <v-card-subtitle class="mt-3">
                Na Europa
              </v-card-subtitle>
              <v-card-text>
                <div>Whitsunday Island, Whitsunday Islands</div>
              </v-card-text>
              <v-card-actions>
                <v-btn color="orange" text="Share"></v-btn>

                <v-btn color="orange" prepend-icon="$vuetify">Explore</v-btn>
              </v-card-actions>
            </v-card w-33>
          </v-col>

          <v-col cols="12" xs="12" sm="6" md="4" lg="3">
            <v-card>
              <v-img class="align-end text-white pl-3 pb-3" src="../assets/image-card.jpg">
                Top 10 lugares para viajar
              </v-img>
              <v-card-subtitle class="mt-3">
                Na Europa
              </v-card-subtitle>
              <v-card-text>
                <div>Whitsunday Island, Whitsunday Islands</div>
              </v-card-text>
              <v-card-actions>
                <v-btn color="orange" text="Share"></v-btn>

                <v-btn color="orange" prepend-icon="$vuetify">Explore</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>

          <v-col cols="12" xs="12" sm="6" md="4" lg="3">
            <v-card>
              <v-img class="align-end text-white pl-3 pb-3" src="../assets/image-card.jpg">
                Top 10 lugares para viajar
              </v-img>
              <v-card-subtitle class="mt-3">
                Na Europa
              </v-card-subtitle>
              <v-card-text>
                <div>Whitsunday Island, Whitsunday Islands</div>
              </v-card-text>
              <v-card-actions>
                <v-btn color="orange" text="Share"></v-btn>

                <v-btn color="orange" prepend-icon="$vuetify">Explore</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
import { ref } from 'vue';

const isDrawerOpen = ref(false)
const isDialogOpen = ref(false)

function dialogClose() {
  isDialogOpen.value = false
}
</script>
