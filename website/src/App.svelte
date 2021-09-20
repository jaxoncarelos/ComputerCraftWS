<script>
	    let command;
        const ws = new WebSocket("ws://localhost:8081")
        function moveTurtleForward(){
			console.log("ran")
            ws.send("return turtle.forward()")
        }
        function turnTurtleRight(){
            ws.send("return turtle.turnRight()")
        }
        function turnTurtleLeft(){
            ws.send("return turtle.turnLeft()")
        }
        function runCommand(){
			console.log(command)
			console.log("hit")
            ws.send("return turtle." + command)
        }
		function turtleGoUp(){
			ws.send("return turtle.up()")
		}
		function turtleGoDown(){
			ws.send("return turtle.down()")
		}
</script>

<main>
	<body>
		<div class="main">
			<button class="btn top" style="font-size: 50px" on:click={moveTurtleForward}>Forward</button>
		</div>
		<div class="sideways">
			<button class="btn btm right" style="font-size: 50px" on:click={turnTurtleLeft}> Left</button>
			<button class="btn btm left" style="font-size: 50px" on:click={turnTurtleRight}> Right</button>
		</div>
		<div class="up">
			<button class="btn uhp" on:click={turtleGoUp}> UP </button>
		</div>
		<div class="down">
			<button class="btn dwn" on:click={turtleGoDown}> DOWN </button>
		</div>
		<button class="btn command" on:click={runCommand}>Run Command</button>
		<input type="text" class="command input" bind:value={command}>
	</body>
</main>

<style>
	.dwn{
		height: 100px;
		font-size: 50px;
		top: 5px;
	}
	.up{
		height: 100px;
		font-size: 50px;
		left: 100px;
	}
    .top{
        background: #333;
        left: 150px;        
    }
    .btm{

        top: 120px;
    }
    .left{
        left: 420px;
    }
    .btn{
        border-radius: 15px;
        background: #333;
        color: white;
		width: 350px;
    }
	.command{

		top: 400px;
		left: 330px;
		width: 150px;
	}
	.input{

		background: #333;
		color: white;
		left: 50px;
		width: 250px;
	}
	div{
		display: flex;
		justify-content: center;
		align-items: center;
		width: 100%;
		height: 100%;
	}
</style>