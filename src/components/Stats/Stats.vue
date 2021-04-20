<template>
<div class="mt-5 mx-auto">
  <div class="">
    <div @keyup.enter="addToBets" class="flex justify-around content-center mb-4 mx-auto md:w-3/4 lg:w-2/4">
      <!-- <input v-model="bet.date" type="date" class="border w-40 text-center mt-5"> -->
      <input v-model="bet.betPlayed" type="text" class="border w-40 text-center" placeholder="Mise jouée">
      <input v-model="bet.resultOfTheBet" type="text" class="border w-40 text-center" placeholder="Montant gagné">
      <button @click="addToBets" class="button-add border p-2 bg-gray-600 border-gray-400 text-white" :class="{'bg-yellow-300 border-yellow-500 text-green-800': bet.Played!==null && bet.resultOfTheBet!==null}">Ajouter</button>
    </div>

    <div class="flex justify-around mx-auto flex-wrap border-t border-yellow-500 xl:w-3/4">
      <div class="py-5 border-b lg:border-b-0 w-screen sm:w-auto">
        <div class="align-middle inline-block min-w-full">
          <div class="shadow overflow-hidden border-b border-gray-200 sm:rounded-lg">
            <table class="min-w-full divide-y divide-gray-200 ">
              <thead class="bg-gray-50">
                <tr>
                  <th scope="col" class="px-2 md:px-4 lg:px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">
                    Date
                  </th>
                  <th scope="col" class="px-2 md:px-4 lg:px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">
                    Mise Jouée
                  </th>
                  <th scope="col" class="px-2 md:px-4 lg:px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">
                    Montant gagné
                  </th>
                  <th scope="col" class="px-2 md:px-4 lg:px-6 py-3 text-center text-xs font-medium text-gray-500 uppercase tracking-wider">
                    Bénéfice / Perte
                  </th>
                  <th scope="col" class="relative px-2 md:px-4 lg:px-6 py-3">
                    <span class="sr-only">Edit</span>
                  </th>
                </tr>
              </thead>
                <tbody class="bg-white divide-y divide-gray-200">
                  <tr v-for="(elem, index) in bets" :key="index" >

                    <td class="px-2 md:px-4 lg:px-6 py-4 whitespace-nowrap text-center">
                      <span class="block text-sm"> {{elem.date}} </span>
                      <span class="text-xs block text-gray-400"> {{ elem.hour }} </span>
                    </td>
                    <td class="px-2 md:px-4 lg:px-6 py-4 whitespace-nowrap text-center">
                      <span> {{elem.betPlayed}} </span>
                    </td>
                    <td class="px-2 md:px-4 lg:px-6 py-4 whitespace-nowrap text-center">
                      <span>
                        {{elem.resultOfTheBet}} 
                      </span>
                    </td>

                    <td class="px-2 md:px-4 lg:px-6 py-4 whitespace-nowrap text-center">
                      <span class="px-2 py-1 inline-flex text-gray-500" :class="changeColorOfResult(elem.resultOfTheBet-elem.betPlayed)" >
                        {{ elem.resultOfTheBet-elem.betPlayed > 0 ? `+${elem.resultOfTheBet-elem.betPlayed}` : elem.resultOfTheBet-elem.betPlayed}}
                      </span>
                    </td>
                    <td class="px-2 md:px-4 lg:px-6 py-4 whitespace-nowrap text-right text-sm font-medium">
                      <button @click="deleteBetToList(index)" class="text-red-600 hover:text-indigo-900">X</button>
                    </td>
                  </tr>

                </tbody>
                <!-- <StatsDay :bets='bets'></StatsDay> -->

            </table>
          </div>
        </div>
      </div>


      <div class="w-3/4 sm:w-2/4 md:w-2/4 lg:w-1/4">
        <StatsDay
          :bets="bets" 
          :numberOfDayPlayed="numberOfDayPlayed" 
          :mountOfBetPlayed="mountOfBetPlayed" :mountOfResultOfTheBet="mountOfResultOfTheBet"
          :finalResult="finalResult"
          :betByDay="betByDay"
          :betWinByDay="betWinByDay"
          :resultByDay="resultByDay"
          :reducer="reducer"
          :changeColorOfResult="changeColorOfResult"
          ></StatsDay>
      </div>
    <!-- <div>
      <StatsMonth
        :bets="bets" 
        :numberOfDayPlayed="numberOfDayPlayed" 
        :mountOfBetPlayed="mountOfBetPlayed" :mountOfResultOfTheBet="mountOfResultOfTheBet"
        :finalResult="finalResult"
        :betByDay="betByDay"
        :betWinByDay="betWinByDay"
        :resultByDay="resultByDay"
        :reducer="reducer"
        :changeColorOfResult="changeColorOfResult"
      >
      </StatsMonth>
    </div> -->

    </div>
  </div>
</div>
</template>

<script>
// import Bankroll from '../Bankroll/Bankroll'
import StatsDay from './StatsDay';
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
      bets: [],
      numberOfDayPlayed: 0,
      mountOfBetPlayed: [],
      mountOfResultOfTheBet: [],
      finalResult: [],
      betByDay: null,
      betWinByDay: null,
      resultByDay: null,
    }
  },
  methods: {
    reducer(accumulator, currentValue) {
      return accumulator + currentValue
    },

    addToBets() {

      const tempBet = {...this.bet}
      const tempMountOfBetPlayed = [...this.mountOfBetPlayed]
      const tempFinalResult = [...this.finalResult]
      const tempMountOfResultOfTheBet = [...this.mountOfResultOfTheBet]

      // console.log("tempBet.betPlayed", tempBet.betPlayed)
      // console.log("tempBet.resultOfTheBet", tempBet.resultOfTheBet)

      if(tempBet.betPlayed != 0 && tempBet.betPlayed !== null && tempBet.resultOfTheBet !== null){

        const dayIsInBets = (day) => {
            return day.date === tempBet.date
        }

        const date = new Date()
        tempBet.date = date.toLocaleDateString()
        tempBet.hour = date.toLocaleTimeString()

        tempMountOfBetPlayed.push(parseFloat(tempBet.betPlayed))
        this.mountOfBetPlayed = tempMountOfBetPlayed

        tempMountOfResultOfTheBet.push(parseFloat(tempBet.resultOfTheBet))
        this.mountOfResultOfTheBet = tempMountOfResultOfTheBet

        const result = tempBet.resultOfTheBet - tempBet.betPlayed
        tempFinalResult.push(parseFloat(result))
        this.finalResult = tempFinalResult

        this.bets.find(dayIsInBets) ? this.numberOfDayPlayed : this.numberOfDayPlayed++

        const betByDay = this.mountOfBetPlayed.reduce((this.reducer), 0) / this.numberOfDayPlayed
        const betWinByDay = this.mountOfResultOfTheBet.reduce((this.reducer), 0) / this.numberOfDayPlayed
        const resultByDay = betWinByDay - betByDay

        // const betWinByDay = this.mountOfResultOfTheBet.reduce((acc, v) => {
        //   acc += v
        //   return acc
        // }, 0) / this.numberOfDayPlayed


        this.betByDay = betByDay
        this.betWinByDay = betWinByDay
        this.resultByDay = resultByDay

        this.bets = [...this.bets, tempBet].reverse()
        
        this.bet.betPlayed = null
        this.bet.resultOfTheBet = null
        
      }
    },
    deleteBetToList(index) {
      const tempBets = [...this.bets];
      tempBets.splice(index, 1)
      this.bets = tempBets
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
      StatsDay,
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
