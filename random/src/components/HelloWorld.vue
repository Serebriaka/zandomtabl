<template>
    <button @click="generate" class="btn">
        Сгенерировать
    </button>
    <table>
        <tr>
            <th>Наименование</th>
            <th>Цена</th>
            <th>Количество</th>
            <th>Стоимость</th>
        </tr>
        <tr v-for="obj in array" :key="obj.title">
            <td>{{obj.title}}</td>
            <td>{{obj.sale}}</td>
            <td>{{obj.number}}</td>
            <td>{{obj.price}}</td>
        </tr>

    </table>
</template>

<script>
    export default {
        name: 'HelloWorld',
        data() {
            return {
                array:[]
            }
        },
        methods:{
            generate: function () {
                const createObject = function (title, sale, number, price) {
                    this.title = title;
                    this.sale = sale;
                    this.number = number;
                    this.price = price;
                };
                for (let i = 0; i < 50; i++) {
                    let sale = (Math.random() * (1000.00)).toFixed(2);
                    let number = Math.floor(Math.random() * (100.00));
                    let price = (sale * number).toFixed(2);
                    let abc = 'АБВГДЕЁЖЗИЙКЛМНОПРСТЭУФХЦЧШЩЬЫЭЮЯ';
                    let title= '';
                    while (title.length < 5) {
                        title += abc[Math.floor(Math.random() * abc.length)];
                    }
                    const newObject = new createObject(title, sale,number,price)
                    this.array.push(newObject)
                }

            }
        }
    }
</script>
<style >
    table {
        border: 1px solid grey;
        width: 100%;
    }
    /* границы ячеек первого ряда таблицы */
    th {
        border: 1px solid grey;
    }
    /* границы ячеек тела таблицы */
    td {
        border: 1px solid grey;
    }
</style>
