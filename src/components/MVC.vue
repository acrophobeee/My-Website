<template>

<v-col cols="12" >
        <v-row class="fill-height" align="center" justify="center">
            <v-col cols="6" md="4">
                <v-img
                    max-height="500"
                    max-width="500"
                    src="p2.png"
                ></v-img>

            </v-col>
            <v-col cols="6" md="4">
                <v-img
                    max-height="500"
                    max-width="500"
                    src="model-uml.png"
                ></v-img>
            </v-col>
            
            
        </v-row>
      </v-col>
      <v-row class="fill-height" align="center" justify="center">
      <v-col cols="12" md="4">
               
               <p>The design of our Plants vs Zombies game is architected after the modern MVC approach. In this design architecture the Controller is the component in-between the View and the Models. Being the component in the middle, the controller is able to orchestrate changes to the model from user actions on the view. The controller then has the ability to tell the view how to update itself and what data models to update on.

                   An example of this flow can be seen when a user clicks on a plant.</p>
               <br/>
               <p>   The GameView on initialization has set the GameController as the action listener for the buttons.
                The GameViewController receives the ActionEvent and acts on it.
                 In the case of a plant it will ask the user for more inputs for the location of the plant.
                  Afterward the controller updates the model with the new plant on the Game's grid.
                  The controller is now able to tell the view to rerender with the new game grid. </p> 
                 

           </v-col>
        </v-row>
</template>

<script>
export default {
}
</script>