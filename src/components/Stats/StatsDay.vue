<template>
<!-- <div class=""> -->
  <!-- <div class=""> -->
    <!-- <div class="-my-2 overflow-x-auto sm:-mx-6 lg:-mx-8"> -->
      <!-- <div class="py-4 align-middle inline-block min-w-full sm:px-1 lg:px-8"> -->
        <div class="border-b border-gray-200 sm:rounded-lg w-full">
          <table class="min-w-full divide-y divide-gray-200 ">
            <caption class="py-5 uppercase tracking-wider">Résultat jour par jour</caption>
            <tbody class="bg-white divide-y divide-gray-200">
              <tr>
                <td class="px-1 py-2 text-center text-xs font-medium text-gray-500 uppercase tracking-wider bg-yellow-200 border-r">
                  Nombre de jours joués
                </td>
                <td class="px-1 py-2 text-center text-xs font-medium text-gray-500 uppercase tracking-wider bg-yellow-200">
                  Nombre de paris joués
                </td>
              </tr>
              <tr>
                <td class="px-1 py-1 whitespace-nowrap text-center border-r">
                  {{ numberOfDayPlayed }}
                </td>
                <td class="px-1 py-1 whitespace-nowrap text-center">
                  {{bets.length}}
                </td>
              </tr>
              <tr>
                <td colspan="2" class="px-1 py-2 text-center text-xs font-medium text-gray-500 uppercase tracking-wider bg-yellow-200">
                  Moyenne de paris par jour
                </td>
              </tr>
              <tr>
                <td colspan="2" class="border-black border-b-2 px-1 py-1 whitespace-nowrap text-center">
                  {{bets.length === 0 ? 0 : (bets.length)/(numberOfDayPlayed) }}
                </td>
              </tr>

              <tr>
                <td class="px-1 py-2 text-center text-xs font-medium text-gray-500 uppercase tracking-wider bg-yellow-200 border-r">
                  Mise totale jouée
                </td>
                <td class="px-1 py-2 text-center text-xs font-medium text-gray-500 uppercase tracking-wider bg-yellow-200 border-r">
                  Gain 
                </td>
              </tr>
              <tr>
                <td class="px-1 py-1 whitespace-nowrap text-center border-r">
                  {{ mountOfBetPlayed.length ? mountOfBetPlayed.reduce((reducer), 0) : 0 }}
                </td>
                <td class="px-1 py-1 whitespace-nowrap text-center border-r">
                  {{ mountOfResultOfTheBet.length ? mountOfResultOfTheBet.reduce((reducer), 0) : 0 }}
                </td>
              </tr>
              <tr>
                <td colspan="2" class="px-1 py-2 text-center text-xs font-medium text-gray-500 uppercase tracking-wider bg-yellow-200">
                  Bénéfice ou perte total
                </td>
              </tr>
              <tr>
                <td colspan="2" :class="changeColorOfResult(finalResult.reduce((reducer), 0))" class="px-1 py-1 whitespace-nowrap text-center border-black border-b-2">
                  {{ finalResult.length ? finalResult.reduce((reducer), 0) : 0 }}
                </td>
              </tr>


              <tr>
                <td class="px-1 py-2 text-center text-xs font-medium text-gray-500 uppercase tracking-wider bg-yellow-200 border-r">
                  Mise par jour
                </td>
                <td class="px-1 py-2 text-center text-xs font-medium text-gray-500 uppercase tracking-wider bg-yellow-200 border-r">
                  Montant gagné par jour
                </td>
              </tr>
              <tr>
                <td class="px-1 py-1 whitespace-nowrap text-center border-r">
                  {{ betByDay !== null ? betByDay : 0 }}
                </td>
                <td class="px-1 py-1 whitespace-nowrap text-center border-r">
                  {{ betWinByDay !== null ? betWinByDay : 0 }}
                </td>
              </tr>
              <tr>
                <td colspan="2" class="px-1 py-2 text-center text-xs font-medium text-gray-500 uppercase tracking-wider bg-yellow-200">
                  Résultat par jour
                </td>
              </tr>
              <tr>
                <td colspan="2" :class="changeColorOfResult(resultByDay)" class="px-1 py-1 whitespace-nowrap text-center">
                  {{ resultByDay !== null ? resultByDay : 0 }}
                </td>
              </tr>


            </tbody>
          </table>
        </div>
      <!-- </div> -->
    <!-- </div> -->
  <!-- </div> -->
<!-- </div> -->


</template>

<script>

export default {
  props: [
          'bets', 
          'numberOfDayPlayed', 
          'mountOfBetPlayed', 
          'mountOfResultOfTheBet', 
          'finalResult', 
          'betByDay', 
          'betWinByDay', 
          'resultByDay', 
          'reducer', 
          'changeColorOfResult'
        ],
}
</script>

<style>
</style>
