<template>
    <div class="home">
        <div class="images">
            <img v-for="attacker in attackers" :src="getImg(attacker.name, 'Attackers')" :alt="attacker.name" @click="setAttacker(attacker.name)" :key="attacker.name">
        </div>

        <div class="values">
            <div>
                <label for="attackerVeteran">Veteran?</label>
                <input id="attackerVeteran" type="checkbox">

                <label for="attackValue">Attack Value</label>
                <input id="attackValue" type="text">

                <label for="attackerCurrentHP">Attacker Current HP</label>
                <input id="attackerCurrentHP" type="text">

                <label for="attackerMaxHP">Attacker Max HP</label>
                <input id="attackerMaxHP" type="text">

                <button>Calculate</button>
            </div>

            <div>
                <label for="defenderVeteran">Veteran?</label>
                <input id="defenderVeteran" type="checkbox">

                <label for="attackValue">Attack Value</label>
                <input id="attackValue" type="text">

                <label for="defenderCurrentHP">Defender Current HP</label>
                <input id="defenderCurrentHP" type="text">

                <label for="defenderMaxHP">Defender Max HP</label>
                <input id="defenderMaxHP" type="text">
            </div>
        </div>

        <div class="images">
            <img v-for="defender in defenders" :src="getImg(defender.name, 'Defenders')" :alt="defender.name" @click="setDefender(defender.name)" :key="defender.name">
        </div>
    </div>
</template>

<script>
export default {
    name: "Home",
    components: {},
    data() {
        return {
            attackers: [
                {
                    name: 'Warrior',
                    attackValue: 2,
                    maxHP: 10
                },
                {
                    name: 'Rider',
                    attackValue: 2,
                    maxHP: 10
                },
                {
                    name: 'Defender',
                    attackValue: 1,
                    maxHP: 15
                },
                {
                    name: 'Swordsman',
                    attackValue: 3,
                    maxHP: 15
                },
                {
                    name: 'Archer',
                    attackValue: 2,
                    maxHP: 10
                },
                {
                    name: 'Catapult',
                    attackValue: 4,
                    maxHP: 10
                },
                {
                    name: 'Knight',
                    attackValue: 3.5,
                    maxHP: 15
                },
                {
                    name: 'Giant',
                    attackValue: 5,
                    maxHP: 40
                },
                {
                    name: 'Boat',
                    attackValue: 1,
                    maxHP: 10
                },
                {
                    name: 'Ship',
                    attackValue: 2,
                    maxHP: 10
                },
                {
                    name: 'Battleship',
                    attackValue: 4,
                    maxHP: 10
                },
                {
                    name: 'Amphibian',
                    attackValue: 2,
                    maxHP: 10
                },
                {
                    name: 'Crab',
                    attackValue: 4,
                    maxHP: 40
                },
                {
                    name: 'Tridention',
                    attackValue: 3,
                    maxHP: 15
                },
                {
                    name: 'Polytaur',
                    attackValue: 3,
                    maxHP: 15
                },
                {
                    name: 'Navalon',
                    attackValue: 4,
                    maxHP: 30
                },
                {
                    name: 'Baby Dragon',
                    attackValue: 3,
                    maxHP: 15
                },
                {
                    name: 'Fire Dragon',
                    attackValue: 4,
                    maxHP: 20
                },
                {
                    name: 'Ice Archer',
                    attackValue: 0,
                    maxHP: 10
                },
                {
                    name: 'Battle Sled',
                    attackValue: 3,
                    maxHP: 15
                },
                {
                    name: 'Ice Fortress',
                    attackValue: 4,
                    maxHP: 20
                },
                {
                    name: 'Gaami',
                    attackValue: 4,
                    maxHP: 30
                },
            ],
            defenders: [
                {
                    name: 'Warrior',
                    defenseValue: 2,
                    maxHP: 10 //lots of duplicated stuff
                },
                {
                    name: 'Rider',
                    defenseValue: 1,
                    maxHP: 10
                },
                {
                    name: 'Defender',
                    defenseValue: 3,
                    maxHP: 15
                },
                {
                    name: 'Swordsman',
                    defenseValue: 3,
                    maxHP: 15
                },
                {
                    name: 'Archer',
                    defenseValue: 1,
                    maxHP: 10
                },
                {
                    name: 'Catapult',
                    defenseValue: 0,
                    maxHP: 10
                },
                {
                    name: 'Knight',
                    defenseValue: 1,
                    maxHP: 15
                },
                {
                    name: 'Giant',
                    defenseValue: 4,
                    maxHP: 40
                },
                {
                    name: 'Boat',
                    defenseValue: 1,
                    maxHP: 10
                },
                {
                    name: 'Ship',
                    defenseValue: 2,
                    maxHP: 10
                },
                {
                    name: 'Battleship',
                    defenseValue: 3,
                    maxHP: 10
                },
                {
                    name: 'Mind Bender',
                    defenseValue: 1,
                    maxHP: 10
                },
                {
                    name: 'Amphibian',
                    defenseValue: 1,
                    maxHP: 10
                },
                {
                    name: 'Crab',
                    defenseValue: 4,
                    maxHP: 40
                },
                {
                    name: 'Tridention',
                    defenseValue: 1,
                    maxHP: 15
                },
                {
                    name: 'Polytaur',
                    defenseValue: 1,
                    maxHP: 15
                },
                {
                    name: 'Navalon',
                    defenseValue: 4,
                    maxHP: 30
                },
                {
                    name: 'Dragon Egg',
                    defenseValue: 2,
                    maxHP: 10
                },
                {
                    name: 'Baby Dragon',
                    defenseValue: 3,
                    maxHP: 15
                },
                {
                    name: 'Fire Dragon',
                    defenseValue: 3,
                    maxHP: 20
                },
                {
                    name: 'Mooni',
                    defenseValue: 2,
                    maxHP: 10
                },
                {
                    name: 'Ice Archer',
                    defenseValue: 1,
                    maxHP: 10
                },
                {
                    name: 'Battle Sled',
                    defenseValue: 2,
                    maxHP: 15
                },
                {
                    name: 'Ice Fortress',
                    defenseValue: 3,
                    maxHP: 20
                },
                {
                    name: 'Gaami',
                    defenseValue: 40,
                    maxHP: 30
                },
                {
                    name: 'Nature Bunny',
                    defenseValue: 1,
                    maxHP: 20
                },
            ]
        }
    },
    methods: {
        getImg(img, where){
            return require(`../assets/${where}/${img}.png`);
        },
        setAttacker(name){
            let attacker = this.attackers.find(x => x.name == name);
            console.log(attacker);
        },
        setDefender(name){
            let defender = this.defenders.find(x => x.name == name);
            console.log(defender);
        }
    }
};
</script>

<style lang="scss" scoped>
.home {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
}

.images {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;

    img {
        height: 4em;
    }
}

.values {
    display: grid;
    grid-template-columns: 1fr 1fr;
    column-gap: 1em;
}

input[type=text] {
    width: 100%;
    padding: 1em 1.2em;
    margin: 0.2em 0 0.6em 0;
    display: inline-block;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
}

input[type=checkbox] {
    display: inline-block;
    width: 100%;
}
</style>