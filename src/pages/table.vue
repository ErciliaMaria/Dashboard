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
        <h1>Table</h1>
        <v-card flat class="border">
            <v-card-title>Ultimos pedidos</v-card-title>
            <v-table>
                <thead>
                    <tr>
                        <th>Pedidos</th>
                        <th>Quantidade</th>
                        <th>Valor</th>
                        <th>Ações</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Pedido 1</td>
                        <td>34</td>
                        <td>R$3,00</td>
                        <td>
                            <v-btn icon="mdi-pencil" variant="tonal" color="primary"/>
                        </td>
                    </tr>
                    <tr>
                        <td>Pedido 2</td>
                        <td>62</td>
                        <td>R$22,60</td>
                         <td>
                            <v-btn icon="mdi-pencil" variant="tonal" color="primary"/>
                        </td>
                    </tr>
                    <tr>
                        <td>Pedido 3</td>
                        <td>52</td>
                        <td>R$32,00</td>
                         <td>
                            <v-btn icon="mdi-pencil" variant="tonal" color="primary"/>
                        </td>
                    </tr>
                </tbody>
            </v-table>
        </v-card>
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
import { ref } from 'vue';

const isDrawerOpen = ref(false)
</script>
