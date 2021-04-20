<template>
<div class="mt-5 md:w-full lg:w-3/4 mx-auto pb-4">
  <div class="flex flex-col">
    <div class="-my-2 sm:-mx-6 lg:-mx-8">
      <div class="py-4 align-middle inline-block min-w-full sm:px-1 lg:px-8">
        <div class="shadow border-b border-gray-200 sm:rounded-lg">
          <table class="min-w-full divide-y divide-gray-200 ">
            <caption>Résultat par mois</caption>
              <thead class="bg-gray-50">
                <tr>
                  <th scope="col" class="px-6 py-3 text-center text-sm font-medium text-gray-500 uppercase tracking-wider w-1/4 ">
                    Mois
                  </th>
                  <th scope="col" class="px-6 py-3 text-center text-sm font-medium text-gray-500 uppercase tracking-wider w-1/4 ">
                    Mise Jouée
                  </th>
                  <th scope="col" class="px-6 py-3 text-center text-sm font-medium text-gray-500 uppercase tracking-wider w-1/4 ">
                    Montant gagné
                  </th>
                  <th scope="col" class="px-6 py-3 text-center text-sm font-medium text-gray-500 uppercase tracking-wider w-1/4 ">
                    Bénéfice / Perte
                  </th>
                </tr>
              </thead>

            <tbody class="bg-white divide-y divide-gray-200">
              <tr v-for="(elem, index) in months" :key="index" >
                <td class="w-1/4 px-1 py-2 text-center text-sm font-medium text-gray-500 uppercase tracking-wider bg-yellow-200 border-r">
                  {{elem}}
                </td>
                <td class="w-1/4 px-1 py-2 text-center text-sm font-medium text-gray-500 uppercase tracking-wider border-r">
                  {{ numberOfDayPlayed }}
                </td>
                <td class="w-1/4 px-1 py-2 text-center text-sm font-medium text-gray-500 uppercase tracking-wider border-r">
                  {{elem}}
                </td>
                <td class="w-1/4 px-1 py-2 text-center text-sm font-medium text-gray-500 uppercase tracking-wider ">
                  Nombre de paris joués
                </td>
                
              </tr>




            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</div>


</template>

<script>

export default {
  data () {
    return {
      months: ['Janvier', 'Février', 'Mars', 'Avril', 'Mai', 'Juin', 'Juillet', 'Aout', 'Septembre', 'Octobre', 'Novembre', 'Décembre']
    }
  },
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
