<template>
    <div class="transactionContainer">
        <div class="accountInfo shadow">
            <div class="titleContainer">
                <img src="../assets/bank.png">
                <h3>Mi cuenta bancaria</h3>
            </div>
            <span class="money">{{accountByUsername.balance}}</span>
            <span><b>Usuario: </b> {{username}}</span>
            <span><b>Fecha de creación:</b> {{accountByUsername.lastChange}}</span>
        </div>
    </div>
</template>


<script>
import gql from "graphql-tag";

export default {
    name: "Transactions", 
    data: function() {
        return {
            username: localStorage.getItem("username") || "none",
            accountByUsername: {
                balance: "",
                lastChange: ""
            }
        }
    }, 
    apollo: {
        accountByUsername: {
            query: gql`
                query AccountByUsername($username: String!) {
                    accountByUsername(username: $username) {
                        balance
                        lastChange
                    }
                }
            `,
            variables(){
                return {
                    username: this.username
                }
            }
        }
    },
    methods: {
        
    }, 
    created: function () {}
};
</script>


<style scoped>
    .transactionContainer{
        width: 70%;
        margin: auto;
        margin-top: 50px;
    }
    .titleContainer{
        display: flex;
    align-items: center;
    margin-bottom: 5px;
    }
    .titleContainer h3{
        margin: 0;
        margin-left: 10px;
    }
    .accountInfo{
            display: flex;
    flex-direction: column;
      padding: 25px 50px;

    }

    .money{
            font-size: 35px;
    }
</style>