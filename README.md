<div class="titulo">Conversor de Und.</div>

<form action="#" method="post">
    <input type="text" name="param">
        <select name="conversao" id="conversao">
            <option value="km-milha">Km > Milha</option>
            <option value="milha-km">Milha > Km</option>
            <option value="metro-km">Metro > Km</option>
            <option value="km-metro">Km > Metro</option>
            <option value="cel-fa">°C > °F</option>
            <option value="fa-cel">F > °C</option>
        </select>
        <button>Clacular</button>
</form>


<style>
    form > * {
        font-size: 1.8rem;
    }
</style>

<?php
const FATOR_KM_MILHA = 0.621371;
const FATOR_METRO_KM = 1000;

$param = $_POST['param'] ?? 0;
switch ($_POST['conversao']) {
    case 'km-milha':
        $distancia = $param * FATOR_KM_MILHA;
        $mensagem = "$param Km = $distancia milha(s)";
        break;
    case 'milha-km':
        $distancia = $param / FATOR_KM_MILHA;
        $mensagem = "$param milha(s) = $distancia Km";
        break;
    case 'metro-km':
        $distancia = $param / 1000; // CONSTANTE OU NÚMERO, DA NO MSM
        $mensagem = "$param m = $distancia Km";
        break;
    case 'km-metro':
        $distancia = $param * FATOR_METRO_KM;
        $mensagem = "$param Km = $distancia m";
        break;
    case 'cel-fa':
        $temp = ($param * 9/5) + 32;
        $mensagem = "$param °c = $temp °F";
        break;
    case 'fa-cel':
        $temp = ($param - 32) * 5/9;
        $mensagem = "$param °F = $temp °C";
        break;
    default:
        $mensagem = "Nenhum valor inserido !";
}

echo "$mensagem";

?>
