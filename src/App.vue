<script setup>
import { ref } from 'vue';

const team1Label = ref('POL');
const team2Label = ref('FRA');

const team1Color = ref('#ff0000');
const team2Color = ref('#d3d3d3');

const team1Serve = ref(true);
const team2Serve = ref(false);

const isLabel1Locked = ref(true);
const isLabel2Locked = ref(true);
const isColor1Locked = ref(true);
const isColor2Locked = ref(true);
const isSets1Locked = ref(true);
const isSets2Locked = ref(true);

const team1Sets = ref(0);
const team2Sets = ref(0);

const team1Points = ref(0);
const team2Points = ref(0);

function lockLabel1() {
	isLabel1Locked.value = !isLabel1Locked.value;
}

function lockLabel2() {
	isLabel2Locked.value = !isLabel2Locked.value;
}

function lockColors1() {
	isColor1Locked.value = !isColor1Locked.value;
}

function lockColors2() {
	isColor2Locked.value = !isColor2Locked.value;
}

function lockSets1() {
	isSets1Locked.value = !isSets1Locked.value;
}

function lockSets2() {
	isSets2Locked.value = !isSets2Locked.value;
}

function addTeam1Point() {
	(team1Points.value < 60) ? team1Points.value++ : team1Points.value = 0;
}

function addTeam2Point() {
	(team2Points.value < 60) ? team2Points.value++ : team2Points.value = 0;
}

function addTeam1Set() {
	(team1Sets.value < 3) ? team1Sets.value++ : team1Sets.value = 0;
}

function addTeam2Set() {
	(team2Sets.value < 3) ? team2Sets.value++ : team2Sets.value = 0; 
}

function changeTeam1Serve () {
	team1Serve.value = true;
	team2Serve.value = false;
}

function changeTeam2Serve () {
	team1Serve.value = false;
	team2Serve.value = true;
}

</script>

<template>
	
	<div class="score-display">
		<div class="team1-cont">
			<div class="team1-color" :style="{backgroundColor: team1Color}"></div>
			<div class="team1-label">{{team1Label}}</div>
			<div class="team1-serve">
				<div v-if="team1Serve">🏐</div>
				<div v-else style="visibility: hidden;">🏐</div>
			</div>
		</div>
		
		<div class="score">
			<div class="team1-sets">
				<div>
					<span>SETS</span>
					{{team1Sets}}
				</div>
			</div>
			<div class="team1-points">{{team1Points}}</div>
			<div class="tournament-logo">
				<img src="./assets/vnl-logo.png" alt="" style="width: 100px;">
			</div>
			<div class="team2-points">{{team2Points}}</div>
			<div class="team2-sets">
				<div>
					<span>SETS</span>
					{{team2Sets}}
				</div>
			</div>
		</div>

		<div class="team2-cont">
			<div class="team2-serve">
				<div v-if="team2Serve">🏐</div>
				<div v-else style="visibility: hidden;">🏐</div>
			</div>
			<div class="team2-label">{{team2Label}}</div>
			<div class="team2-color" :style="{backgroundColor: team2Color}"></div>
		</div>
	</div>

	

<!-- --------------------------------------------------------------------------------------------- -->

	<div class="display-menu">
		<div class="menu-team1"><h2>TEAM 1 - {{team1Label}}</h2>
			<div class="menu-team1-label">
				<button @click="lockLabel1()" class="lock">🔒</button>
				<input type="text" v-model="team1Label" maxlength="3" placeholder="team1" :disabled="isLabel1Locked">
			</div>

			<div class="menu-team1-color">
				<button @click="lockColors1()" class="lock">🔒</button>
				<input type="color" v-model="team1Color" :disabled="isColor1Locked">
			</div>

			<div class="menu-team1-sets">
				<button @click="lockSets1()" class="lock">🔒</button>
				<button @click="addTeam1Set()" :disabled="isSets1Locked">Add {{team1Label}} 1 set</button>
			</div>

			<div class="menu-team1-points">
				<button @click="addTeam1Point()">Add {{team1Label}} 1 point</button>
			</div>

			<div class="menu-team1-serves">
				<button @click="changeTeam1Serve()">{{team1Label}} is serving</button>
			</div>
		</div>
<!-- ----------------------------------- -->
		<div class="menu-team2"><h2>TEAM 2 - {{team2Label}}</h2>
			<div class="menu-team2-label">
				<input type="text" v-model="team2Label" maxlength="3" placeholder="team2" :disabled="isLabel2Locked">
				<button @click="lockLabel2()" class="lock">🔒</button>
			</div>

			<div class="menu-team2-color">
				<input type="color" v-model="team2Color" :disabled="isColor2Locked">
				<button @click="lockColors2()" class="lock">🔒</button>
			</div>

			<div class="menu-team2-sets">
				<button @click="addTeam2Set()" :disabled="isSets2Locked">Add {{team2Label}} 1 set</button>
				<button @click="lockSets2()" class="lock">🔒</button>
			</div>

			<div class="menu-team2-points">
				<button @click="addTeam2Point()">Add {{team2Label}} 1 point</button>
			</div>

			<div class="menu-team2-serves">
				<button @click="changeTeam2Serve()">{{team2Label}} is serving</button>
			</div>
		</div>
	</div>
</template>

<style scoped>
.score-display {
	display: flex;
	background: white;
	/* border: 3px solid white; */
	font-size: 4rem;
	color: white;

	.team1-cont, .team2-cont  {
		/* border: 1px solid red; */
		display: flex;
		align-items: center;
		margin: 10px;
		background: #2528d9;
	}

	.team1-color, .team2-color {
		padding: 52px 20px;
	}

	.team1-label {
		padding: 0 100px 0 30px;
		text-transform: uppercase;
	}

	.team2-label {
		padding: 0 30px 0 100px;
		text-transform: uppercase;
	}

	.team1-serve, .team2-serve{
		padding: 0 10px;
	}

	.score {
		/* padding: 10px 20px; */
		/* border: 2px solid black; */
		display: flex;
		margin: 10px 0;
		/* background: blue; */

		.team1-sets, .team2-sets {
			border: 1px solid green;
			background: #2528d9;
			width: 100px;
			display: flex;
			justify-content: center;
			align-items: center;

			div {
				text-align: center;
				position: relative;
				display: flex;
				justify-content: center;

				span {
					font-size: .7rem;
					position: absolute;
					top: 0px;
				} 
			}
			
		}

		.team1-points, .team2-points  {
			/* border: 1px solid red; */
			background: #fa5540;
			margin: 0 10px;
			width: 100px;
			display: flex;
			justify-content: center;
			align-items: center;
		}

		.tournament-logo {
			background-color: #2528d9;
			width: 100px;
			display: flex;
			justify-content: center;
			align-items: center;
		}
	}
}

.display-menu {
	margin-top: 50px;
	display: flex;
	justify-content: center;
	gap: 120px;
	
	.menu-team1 {
		border: 3px dashed black;
		padding: 10px;

		h2 {
			text-align: center;
		}

		.menu-team1-label {
			display: flex;

			input {
				height: 50px;
				width: 150px;
				padding: 0 10px;
				font-size: 1.5rem;
			}
		}

		.menu-team1-color {
			display: flex;

			input {
				height: 50px;
				width: 150px;
			}
		}

		.menu-team1-sets {
			button {
				height: 50px;
				width: 150px;
			}
		}

		.menu-team1-points {
			button {
				height: 50px;
				width: 200px;
			}
		}

		.menu-team1-serves {
			button {
				height: 50px;
				width: 200px;
			}
		}
	}
/* ----------------- */

.menu-team2 {
	border: 3px dashed black;
	padding: 10px;

	h2 {
		text-align: center;
	}

		.menu-team2-label {
			display: flex;

			input {
				height: 50px;
				width: 150px;
				padding: 0 10px;
				font-size: 1.5rem;
				text-align: right;
			}
		}

		.menu-team2-color {
			display: flex;
			
			input {
				height: 50px;
				width: 150px;
			}
		}

		.menu-team2-sets {
			button {
				height: 50px;
				width: 150px;
			}
		}

		.menu-team2-points {
			button {
				height: 50px;
				width: 200px;
			}
		}

		.menu-team2-serves {
			button {
				height: 50px;
				width: 200px;
			}
		}
	}


	.lock {
		width: 50px !important;
	}


	.menu-team-labels {
		input[type='text'] {
			text-transform: uppercase;
		}
	}
}
</style>
