<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Envi Dados</title>
</head>
<body>
    <form id="dataForm">
        <label for="data">Dados:</label>
        <input type="text" id="data" name="data">
        <button type="submit">Enviar</button>
    </form>

    <script>
        document.getElementById('dataForm').addEventListener('submit', async function(event) {
            event.preventDefault();
            const data = document.getElementById('data').value;
            const response = await fetch('https://api.github.com/repos/SEU_USUARIO/SEU_REPOSITORIO/dispatches', {
                method: 'POST',
                headers: {
                    'Accept': 'application/vnd.github.v3+json',
                    'Authorization': 'token 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',
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    event_type: 'save_data',
                    client_payload: { data: data }
                })
            });
            if (response.ok) {
                alert('Dados enviados com sucesso!');
            } else {
                alert('Falha ao enviar dados.');
            }
        });
    </script>
</body>
</html>
