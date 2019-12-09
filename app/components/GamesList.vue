<template>
    <Page>
        <ActionBar title="Xboxs Santa María" />
        <ScrollView>
            <StackLayout class="home-panel">
                <Label class="h1 text-center" text="Juegos disponibles" />
                <ListView for="game in games">
                    <v-template>
                        <Label class="h2" :text="game.name" />
                    </v-template>
                </ListView>
            </StackLayout>
        </ScrollView>
    </Page>
</template>

<script>
    export default {
        name: "GamesList",
        data() {
            return {
                games: {},
                chargedGames: false
            };
        },
        mounted() {
            this.getGames();
        },
        methods: {
            getGames() {
                fetch("http://josemanuellh.com/xboxs-api/api/juego")
                    .then(function(res) {
                        return res.json();
                    })
                    .then(response => {
                        this.games = response;
                    })
                    .then(() => {
                        this.chargedGames = true;
                    });
            }
        }
    };
</script>