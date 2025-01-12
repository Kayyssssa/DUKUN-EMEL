<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dukun ML Clone</title>
    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background-color: #121212;
            color: #fff;
        }
        .container {
            max-width: 800px;
            margin: 50px auto;
            text-align: center;
        }
        h1 {
            color: #007bff;
        }
        input {
            padding: 10px;
            width: 70%;
            margin-right: 10px;
            border: none;
            border-radius: 4px;
        }
        button {
            padding: 10px 20px;
            background-color: #007bff;
            border: none;
            border-radius: 4px;
            color: #fff;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        table {
            width: 100%;
            margin-top: 20px;
            border-collapse: collapse;
        }
        th, td {
            padding: 10px;
            border: 1px solid #444;
            text-align: left;
        }
        th {
            background-color: #222;
        }
        .team-header {
            color: #007bff;
            margin-top: 30px;
        }
        .enemy-header {
            color: #ff4d4d;
            margin-top: 30px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Dukun ML</h1>
        <input type="text" id="token" placeholder="Masukkan Token Anda di sini...">
        <button onclick="fetchData()">GO</button>
        
        <h2 class="team-header">TEAM</h2>
        <table>
            <thead>
                <tr>
                    <th>ID (Server)</th>
                    <th>Nickname</th>
                    <th>Squad</th>
                    <th>Rank</th>
                    <th>Win Rates</th>
                </tr>
            </thead>
            <tbody id="team-data">
                <tr>
                    <td colspan="5">Waiting for data...</td>
                </tr>
            </tbody>
        </table>

        <h2 class="enemy-header">ENEMY</h2>
        <table>
            <thead>
                <tr>
                    <th>ID (Server)</th>
                    <th>Nickname</th>
                    <th>Squad</th>
                    <th>Rank</th>
                    <th>Win Rates</th>
                </tr>
            </thead>
            <tbody id="enemy-data">
                <tr>
                    <td colspan="5">Waiting for data...</td>
                </tr>
            </tbody>
        </table>
    </div>

    <script>
        function fetchData() {
            const token = document.getElementById('token').value;

            // Simulate fetching data from API
            if (!token) {
                alert('Please enter a token!');
                return;
            }

            const teamData = [
                { id: '12345', nickname: 'Player1', squad: 'SquadA', rank: 'Mythic', winRate: '80%' },
                { id: '67890', nickname: 'Player2', squad: 'SquadB', rank: 'Legend', winRate: '75%' }
            ];

            const enemyData = [
                { id: '54321', nickname: 'Enemy1', squad: 'SquadX', rank: 'Epic', winRate: '65%' },
                { id: '98765', nickname: 'Enemy2', squad: 'SquadY', rank: 'Grandmaster', winRate: '60%' }
            ];

            populateTable('team-data', teamData);
            populateTable('enemy-data', enemyData);
        }

        function populateTable(tableId, data) {
            const tableBody = document.getElementById(tableId);
            tableBody.innerHTML = '';

            data.forEach(row => {
                const tr = document.createElement('tr');
                tr.innerHTML = `
                    <td>${row.id}</td>
                    <td>${row.nickname}</td>
                    <td>${row.squad}</td>
                    <td>${row.rank}</td>
                    <td>${row.winRate}</td>
                `;
                tableBody.appendChild(tr);
            });
        }
    </script>
</body>
</html>
