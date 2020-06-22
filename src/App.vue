<template>


  <div id="app">

    <md-card>
      <md-card-header>
        <div class="md-title">
          Stock Price Calculator
        </div>
        <div class="md-subhead">
          by Abdullah
        </div>
      </md-card-header>
      <form>
        <div>
        <md-field>
          <label>Stock Price</label>
          <span class="md-prefix">$</span>
          <md-input v-model="initialPrice" type="number"></md-input>
        </md-field>
        <md-button class="md-raised" type="reset">RESET</md-button>
      </div>
      </form>
      <div>
        <md-autocomplete v-model="numberOfContracts" :md-options="contracts" :md-open-on-focus="false" type="number">
          <label>Number of Contracts</label>
        </md-autocomplete>
      </div>
    </md-card>

    <div class="md-layout">
      <div class="md-layout-item just-for-demo">
        <md-card>
          <div>
            <md-card-header>
            <div class="md-title">
              Target
            </div>
          </md-card-header>
          <form>
            <div>
              <md-autocomplete v-model="initialPercentGain" :md-options="percentGain" :md-open-on-focus="true" type="number">
                <label>Percent Gain</label>
                <span class="md-suffix">%</span>
              </md-autocomplete>
            </div>
            <div>
              <md-autocomplete v-model="initialPercentLoss" :md-options="percentLoss" :md-open-on-focus="true" type="number">
                <label>Percent Loss</label>
                <span class="md-suffix">%</span>
              </md-autocomplete>
            </div>
            <div>
              <md-field>
                <label>Total Gain Goal</label>
                <span class="md-prefix">$</span>
                <md-input v-model="initialGainGoal" type="number"></md-input>
              </md-field>
            </div>
            <div>
              <md-field>
                <label>Total Loss Goal</label>
                <span class="md-prefix">$</span>
                <md-input v-model="initialLossGoal" type="number"></md-input>
              </md-field>
            </div>
          </form>
          </div>
          
          
        </md-card>
      </div>
      
      <div class="md-layout-item just-for-demo">
        <md-card>
          <md-card-header>
            <div class="md-title">
              Profit
            </div>
          </md-card-header>
          <div>
            <md-field>
              <label>Total Percent Gain Limit</label>
              <span class="md-prefix">$ {{(((parseFloat(initialPrice) * parseFloat(initialPercentGain)) / parseFloat(100)) + parseFloat(initialPrice)).toFixed(2)}}</span>
              <md-input v-model="percentGainLimit" type="number" readonly></md-input>
            </md-field>
          </div>
          <div>
            <md-field>
              <label>Total Percent Stop Loss</label>
              <span class="md-prefix">$ {{(parseFloat(initialPrice) - ((parseFloat(initialPrice) * parseFloat(initialPercentLoss)) / parseFloat(100))).toFixed(2)}}</span>
              <md-input v-model="percentStopLoss" type="number" readonly></md-input>
            </md-field>
          </div>
          <div>
            <md-field>
              <label>Total Gain Limit</label>
              <span class="md-prefix">$ {{(((parseFloat(initialPrice) * parseFloat(numberOfContracts)) + parseFloat(initialGainGoal)) / parseFloat(numberOfContracts)).toFixed(2)}}</span>
              <md-input v-model="gainLimit" type="number" readonly></md-input>
            </md-field>
          </div>
          <div>
            <md-field>
              <label>Total Loss Limit</label>
              <span class="md-prefix">$ {{(((parseFloat(initialPrice) * parseFloat(numberOfContracts)) - parseFloat(initialLossGoal)) / parseFloat(numberOfContracts)).toFixed(2)}}</span>
              <md-input v-model="stopLimit" type="number" readonly></md-input>
            </md-field>
          </div>
        </md-card>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data: () => ({
    initialGainGoal: 100,
    initialLossGoal: 50,
    percentGainLimit: ".",
    percentStopLoss: ".",
    gainLimit: ".",
    stopLimit: ".",
    initialPrice: 0,
    numberOfContracts: 1,
    contracts: [
      1,
      2,
      3,
      4,
      5,
      6,
      7,
      8,
      9,
      10,
      11,
      12,
      13,
      14,
      15
    ],
    initialPercentGain: 15,
    percentGain:[
      5,
      10,
      15,
      20,
      25,
      30,
      35,
      40,
      45,
      50,
      55,
      60,
      65,
      70,
      75,
      80,
      85,
      90,
      95,
      100
    ],
    initialPercentLoss: 5,
    percentLoss: [
      5,
      10,
      15,
      20,
      25,
      30,
      35,
      40,
      45,
      50,
      55,
      60,
      65,
      70,
      75,
      80,
      85,
      90,
      95,
      100
    ]
  })

}

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
