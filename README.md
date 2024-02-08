<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cotizador GSPL</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f7f7f7;
        }
        .container {
            background-color: #fff;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            max-width: 400px;
            width: 100%;
        }
        h1 {
            margin-bottom: 20px;
            color: #333;
        }
        label {
            display: block;
            text-align: left;
            margin-bottom: 5px;
            color: #555;
        }
        input {
            width: calc(100% - 10px);
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        #cotizacion {
            display: inline-block;
            padding: 10px 20px;
            background-color: #007bff;
            color: #fff;
            border-radius: 4px;
            font-weight: bold;
            margin-bottom: 15px;
        }
        button {
            background-color: #007bff;
            color: #fff;
            border: none;
            border-radius: 4px;
            padding: 10px 20px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #0056b3;
        }
        #resultado, #mensaje {
            margin-top: 20px;
            text-align: left;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Cotizador GSPL</h1>
        
        <label for="nombreEmpresa">Nombre de la empresa:</label>
        <input type="text" id="nombreEmpresa" placeholder="Ingrese el nombre de la empresa">
        
        <label for="nit">NIT:</label>
        <input type="text" id="nit" placeholder="Ingrese el NIT de la empresa">
        
        <label for="nombreProducto">Nombre del producto:</label>
        <input type="text" id="nombreProducto" placeholder="Ingrese el nombre del producto">
        
        <label for="valor">Valor unitario del producto:</label>
        <input type="number" id="valor" placeholder="Ingrese el valor unitario del producto">
        
        <label for="cotizacion">Número de cotización:</label>
        <span id="cotizacion">01</span>
        
        <button onclick="generarCotizacion()">Generar Cotización</button>
        
        <div id="resultado"></div>
        <div id="mensaje"></div>
    </div>

    <script>
        var contadorCotizacion = 1;

        function generarCotizacion() {
            var nombreEmpresa = document.getElementById('nombreEmpresa').value;
            var nit = document.getElementById('nit').value;
            var nombreProducto = document.getElementById('nombreProducto').value;
            var valor = parseFloat(document.getElementById('valor').value);

            var iva = valor * 0.19; // 19% de IVA
            var total = valor + iva;
            
            var resultado = "<strong>Nombre de la empresa:</strong> " + nombreEmpresa + "<br>";
            resultado += "<strong>NIT:</strong> " + nit + "<br>";
            resultado += "<strong>Nombre del producto:</strong> " + nombreProducto + "<br>";
            resultado += "<strong>Valor unitario del producto:</strong> $" + valor.toFixed(2) + "<br>";
            resultado += "<strong>IVA (19%):</strong> $" + iva.toFixed(2) + "<br>";
            resultado += "<strong>Total a pagar:</strong> $" + total.toFixed(2) + "<br>";
            
            document.getElementById('resultado').innerHTML = resultado;
            
            document.getElementById('cotizacion').innerText = formatNumeroCotizacion(contadorCotizacion);
            contadorCotizacion++;
            
            document.getElementById('mensaje').innerHTML = "La cotización ha sido generada correctamente.";
        }

        function formatNumeroCotizacion(numero) {
            var str = numero.toString();
            return str.padStart(2, '0');
        }
    </script>
</body>
</html>
