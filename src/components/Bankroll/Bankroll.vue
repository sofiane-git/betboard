<template>
<div class="flex flex-col w-1/4 mt-5 relative">
  <div class="-overflow-x-auto fixed bg-red-500">
    <div class="align-middle inline-block min-w-full ">
      <div class="shadow overflow-hidden border-b border-gray-200 sm:rounded-lg">
        <table class="min-w-full divide-y divide-gray-200">
          <thead class="bg-gray-50">
            <tr>
              <th colspan="2" class="py-2 text-center font-medium text-gray-500">
                <span class="text-l uppercase tracking-wider outline-orange">Gestion de bankroll</span>
                <div class="flex justify-center py-1 border-t">
                    <label class="mr-2 text-sm my-auto">Montant du capital (€)</label>
                    <input class="w-20 mx-0 my-auto text-center border border-yellow-200" type="texte" v-model="bankroll" />
                </div>
              </th>
            </tr>
          </thead>
            <tbody class="bg-white divide-y divide-gray-200">
                <tr>
                    <td class="bg-yellow-300 border-r px-2 py-1 whitespace-nowrap text-center w-3/4">
                    Bankroll
                    </td>
                    <td class="w-1/4 px-2 py-1 whitespace-nowrap text-center">
                        <span>{{bankroll===null ? 0 : bankroll}}</span>
                    </td>
                </tr>
                
                <tr>
                    <td class="bg-yellow-200 border-r px-2 py-1 whitespace-nowrap text-center w-3/4">
                    Confiance 1/5
                    </td>
                    <td class="w-1/4 px-2 py-1 whitespace-nowrap text-center">
                        <span> {{bet1on5(this.bankroll)}} </span>
                    </td>
                </tr>

                <tr>
                    <td class="bg-yellow-300 border-r px-2 py-1 whitespace-nowrap text-center w-3/4">
                    Confiance 2/5
                    </td>
                    <td class="w-1/4 px-2 py-1 whitespace-nowrap text-center">
                        <span> {{bet2on5(this.bankroll)}} </span>
                    </td>
                </tr>

                <tr>
                    <td class="bg-yellow-200 border-r px-2 py-1 whitespace-nowrap text-center w-3/4">
                    Confiance 3/5
                    </td>
                    <td class="w-1/4 px-2 py-1 whitespace-nowrap text-center">
                        <span> {{bet3on5(this.bankroll)}} </span>
                    </td>
                </tr>

                <tr>
                    <td class="bg-yellow-300 border-r px-2 py-1 whitespace-nowrap text-center w-3/4">
                    Confiance 4/5
                    </td>
                    <td class="w-1/4 px-2 py-1 whitespace-nowrap text-center">
                        <span> {{bet4on5(this.bankroll)}} </span>
                    </td>
                </tr>

                <tr>
                    <td class="bg-yellow-200 border-r px-2 py-1 whitespace-nowrap text-center w-3/4">
                    Confiance 5/5
                    </td>
                    <td class="w-1/4 px-2 py-1 whitespace-nowrap text-center">
                        <span> {{bet5on5(this.bankroll)}} </span>
                    </td>
                </tr>

              <!-- More items... -->
            </tbody>

        </table>
      </div>
    </div>
  </div>

</div>
</template>

<script>
// import StatsDay from './StatsDay';
// import StatsMonth from './StatsMonth';
// import StatsYear from './StatsYear';

export default {
    data() {
        return {
            bankroll: null,
        }
    },
    methods: {
        bet1on5(elem) {
            return(
                elem*0.01
            )
        },
        bet2on5(elem) {
            return(
                elem*0.02
            )
        },
        bet3on5(elem) {
            return(
                elem*0.03
            )
        },
        bet4on5(elem) {
            return(
                elem*0.04
            )
        },
        bet5on5(elem) {
            return(
                elem*0.05
            )
        },


    },
}

</script>

<style>
input:focus, .outline-orange:focus {
  outline-color: #FBBF24;
}
.button-add:focus {
  outline-color: #34D399
;
}
</style>
