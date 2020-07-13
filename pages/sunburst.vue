<template>
    <v-container>
        <v-row>
            <v-col cols="12" md="2"></v-col>
                <v-col cols="12" md="8">
                    <div id="myDiv">
                    </div>
                </v-col>
            <v-col cols="12" md="2"></v-col>
        </v-row>
    </v-container>
</template>

<script>
import { vueWindowSizeMixin } from 'vue-window-size';

export default {
    mixins: [vueWindowSizeMixin],
    data() {
        return {

        }
    },
    methods: {
    },
    mounted: function(){
        Plotly.d3.csv('https://raw.githubusercontent.com/plotly/datasets/master/coffee-flavors.csv', function(err, rows){
            function unpack(rows, key) {
            return rows.map(function(row) { return row[key]; });
        }
        var data = [
            {
            type: "sunburst",
            maxdepth: 3,
            ids: unpack(rows, 'ids'),
            labels: unpack(rows, 'labels'),
            parents:unpack(rows, 'parents')
            }
        ];
        var layout = {
            margin: {l: 0, r: 0, b: 0, t:0},
            sunburstcolorway:[
                "#636efa","#EF553B","#00cc96","#ab63fa","#19d3f3",
                "#e763fa", "#FECB52","#FFA15A","#FF6692","#B6E880"
            ],
            extendsunburstcolorway: true
        };
        Plotly.newPlot('myDiv', data, layout, {showSendToCloud: true});
        })
    },
}
</script>

<style scoped>

</style>