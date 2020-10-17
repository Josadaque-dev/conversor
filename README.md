<div class="titulo">Conversor de Und.</div>

<form action="#" method="post">
    <input type="text" nome='param'>
        <select name="conversao" id="conversao">
            <option value="km-milha">Km > Milha</option>
            <option value="milha-km">Milha > Km</option>
            <option value="metro-km">Metro > Km</option>
            <option value="km-metro">Km > Metro</option>
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
        $distancia = $param * FATOR_METRO_KM; // CONSTANTE OU NÚMERO, DA NO MSM
        $mensagem = "$param m = $distancia Km";
        break;
    case 'km-metro':
        $distancia = $param / FATOR_METRO_KM;
        $mensagem = "$param Km = $distancia m";
        break;
    default:
        $mensagem "Nenhum valor inserido !";
}

echo "$mensagem";

?>
