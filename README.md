<div>
    <form method="post">
        <div>
            <label>Fecha venta:</label>
            <input type="date" name="txtFechaVenta">
        </div>
        <div>
            <label>Cliente:</label>
            <select name="cboCliente">
                <option value="PEPITO">JOSE</option>
                <option value="ALEJA">ALEJA BOADA</option>
                <option value="MARTIN">MARTIN LEON</option>
                <option value="CHRIS">CHRIS AMOR</option>

            </select>
        </div>
        <div>
            <label>
                Producto :</label>
            <select name="cboProducto">
                <option value="TALLARIN">TALLARIN SUMES</option>
                <option value="ARROZ">ARROZ HALCON</option>
                <option value="GELATINA">GELATINA ROYAL</option>
                <option value="GALLETAS">GALLETA OREO</option>
                <option value="PAPAS">PAPAS DE LIMON</option>
            </select>
        </div>
        <div>
            <label>Cantidad:</label>
            <input type="number" name="Cantidad">
        </div>
        <div>
            <label>Precio:</label>
            <input type="number" name="txtPrecio">
        </div>
        <div>
            <button type="submit" name="btnCalcular">Calcular</button>
        </div>
    </form>
</div>
<hr>
<h1>RESULTADO</h1>
<?php
if (isset($_POST['btnCalcular'])) {
    $fecha = $_POST['txtFechaVenta'];
    $cliente = $_POST['cboCliente'];
    $producto = $_POST['cboProducto'];
    $cantidad = $_POST['txtCantidad'];
    $precio = $_POST['txtPrecio'];
    $subTot = $cantidad * $precio;
    $iva = $subTot * 0.12;
    $desc = 0;
    if ($subTot < 50) {
        $desc = $subTot * 0.05;
        $regalo = "NO TIENE REGALO";
    } else {
        if ($subTot >= 50 && $subTot < 100) {
            $desc = $subTot * 0.07;
            $regalo = "PELOTA";
        } else {
            if ($subTot >= 100 && $subTot < 200) {
                $desc = $subTot * 0.1;
                $regalo = "LICUADORA";
            } else {
                $desc = $subTot * 0.15;
                $regalo = "VIAJE A VENEZUELA";
            }
        }
    }
    $totPagar = $subTot + $iva - $desc;
    //**** mostrar resultado */
    echo "Fecha  :" . $fecha . "<br>";
    echo "Cliente :" . $cliente . "<br>";
    echo "Producto :" . $producto . "<br>";
    echo "Subtotal :" . $subTot . "<br>";
    echo "IVA 12% :" . $iva . "<br>";
    echo "Descuento :" . $desc . "<br>";
    echo "Total Pagar :" . $totPagar . "<br>";
    echo "Regalo :" . $regalo . "<br>";
}
?>
