<template>
<div class="mt-5 w-2/4 mx-auto pb-4">
  <div class="flex flex-col">
    <div class="-my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
      <div class="py-2 align-middle inline-block min-w-full sm:px-6 lg:px-8">
        <div class="shadow overflow-hidden border-b border-gray-200 sm:rounded-lg">
          <table class="min-w-full divide-y divide-gray-200 ">
            <thead class="bg-gray-50">
              <tr>
                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">
                  Date
                </th>
                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">
                  Mise Jouée
                </th>
                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">
                  Montant gagné
                </th>
                <th scope="col" class="px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">
                  Bénéfice / Perte
                </th>
                <th scope="col" class="relative px-6 py-3">
                  <span class="sr-only">Edit</span>
                </th>
              </tr>
            </thead>
              <tbody class="bg-white divide-y divide-gray-200">
                <tr v-for="(elem, index) in bets" :key="index" >

                  <td class="px-6 py-4 whitespace-nowrap text-center">
                    <span class="block text-sm"> {{elem.date}} </span>
                    <span class="text-xs block text-gray-400"> {{ elem.hour }} </span>
                  </td>
                  <td class="px-6 py-4 whitespace-nowrap text-center">
                    <span> {{elem.betPlayed}} </span>
                  </td>
                  <td class="px-6 py-4 whitespace-nowrap text-center">
                    <span>
                      {{elem.resultOfTheBet}} 
                    </span>
                  </td>

                  <td class="px-6 py-4 whitespace-nowrap text-center">
                    <span class="px-2 py-1 inline-flex text-gray-500" :class="changeColorOfResult(elem.resultOfTheBet-elem.betPlayed)" >
                      {{elem.resultOfTheBet-elem.betPlayed>0 ? `+${elem.resultOfTheBet-elem.betPlayed}` : elem.resultOfTheBet-elem.betPlayed}}
                    </span>
                  </td>
                  <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">
                    <button @click="deleteBetToList(index)" class="text-red-600 hover:text-indigo-900">X</button>
                  </td>
                </tr>

                <!-- More items... -->
              </tbody>

          </table>
        </div>
      </div>
    </div>

    <div  @keyup.enter="addToBets" class="flex justify-around mt-5 border-t border-yellow-500 content-center">
      <!-- <input v-model="bet.date" type="date" class="border w-40 text-center mt-5"> -->
      <input v-model="bet.betPlayed" type="text" class="border w-40 text-center mt-5" placeholder="Mise jouée">
      <input v-model="bet.resultOfTheBet" type="text" class="border w-40 text-center mt-5" placeholder="Montant gagné">
      <button @click="addToBets" class="button-add border p-2 mt-5 bg-gray-600 border-gray-400 text-white" :class="{'bg-yellow-300 border-yellow-500 text-green-800': bet.Played!==null && bet.resultOfTheBet!==null}">Ajouter</button>
    </div>
    <!-- <div>
      <Bankroll></Bankroll>
    </div> -->

  </div>
</div>
</template>

<script>
// import Bankroll from '../Bankroll/Bankroll'
// import StatsDay from './StatsDay';
// import StatsMonth from './StatsMonth';
// import StatsYear from './StatsYear';


export default {
  data() {
    return {
      bet: {
        date: null,
        hour: null,
        betPlayed: null,
        resultOfTheBet: null,
      },
      bets: []
    }
  },
  methods: {
    addToBets() {

      const tempBet = {...this.bet};

      if(tempBet.betPlayed !== null && tempBet.resultOfTheBet !== null){

        const date = new Date();
        tempBet.date = date.toLocaleDateString();
        tempBet.hour = date.toLocaleTimeString();

        this.bets = [...this.bets, tempBet];
        this.bet.betPlayed = null;
        this.bet.resultOfTheBet = null;
      }
    },
    deleteBetToList(index) {
      const tempBets = [...this.bets];
      tempBets.splice(index, 1);
      this.bets = tempBets;
    },
    changeColorOfResult(value) {
      if(value < 0) {
        return (
          'text-red-500'
        )
      }else if(value > 0) {
        return (
          'text-green-600'
        )
      }
    }
  },
  components: {
      // StatsDay,
      // StatsMonth,
      // StatsYear,
      // Bankroll
  }
}
</script>

<style>
input:focus {
  outline-color: #FBBF24;
}
.button-add:focus {
  outline: none;
;
}
</style>
