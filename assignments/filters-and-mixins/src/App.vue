<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <h1>Filters & Mixins</h1>
                <!-- Exercise 1) -->
                <!-- Build a local Filter which reverses the Text it is applied on -->
                {{ firstText | reverseText }}
                
                <br>
                <br>

                <!-- Exercise 2 -->
                <!-- Build a global Filter which counts the length of a word and it appends it -->
                <!-- Like this: "Test" => Gets Filtered to => "Test (4)" -->
                {{ secondText | appendCount }}

                <br>
                <br>

                <!-- Exercise 3 -->
                <!-- Do the same as in Exercises 1 & 2, now with Computed Properties -->
                {{ computedReverseText }}<br>
                {{ computedAppendCount }}                

                <br>
                <br>

                <!-- Exercise 4 -->
                <!-- Share the Computed Property rebuilding Exercise 2 via a Mixin -->
            </div>
        </div>
    </div>
</template>

<script>
    import { appendCountMixin } from './appendCountMixin';

    export default {
        mixins: [appendCountMixin],
        data() {
            return {
                firstText: 'Hello World',
                secondText: 'Hey'
            }
        },
        filters: {
            reverseText(value) {
                return value.split('').reverse().join('');
            }
        },
        computed: {
            computedReverseText() {
                return this.firstText.split('').reverse().join('');
            },
            // computedAppendCount() {
            //     return `${this.secondText} (${this.secondText.length})`;
            // }
        }
    }
</script>

<style>
</style>
