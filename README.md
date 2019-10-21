# Google-sheet-scripts
This contains a set of useful scripts for automate tasks in google sheets.

<h3> 1 - DeleteDuplicate </h3>

<p><code> var sheet = SpreadsheetApp.openById('PUT YOUR GOOGLE SHEET ID HERE').getSheetByName('usuario');</code>
Esta linea nos permite indicar la hoja y el google sheet donde se va a ejecutar el script. En este caso es en la hoja usuario del google sheet PUT YOUR GOOGLE SHEET ID HERE.</p>
  
<p><code> var data = sheet.getRange("A:Z").getValues();</code>
En esta linea damos el rango donde pueden haber datos a comparar, en caso que se coloque un dato por fuera de este rango será eliminado sin importar si esté o no duplicada la información.</p>
  
<p><code> if (row[1] == newData[j][1])</code>
Dentro de este <b>for</b> lo más importante es esta instrucción, donde podemos indicar cúal es el dato que vamos a comparar, en este caso la columna B. Para este script este es el dato a ser comparado para determinar si hay o no una entrada duplicada.</p>


<h3> 2 - UpdateDate </h3>

<p>Este script permite realizar una nueva entrada de fecha y ecuaciones para aquellos días inferiores a 5. A continuación explico un poco el código.</p>

<p><code> var sheet = SpreadsheetApp.openById('PUT YOUR GOOGLE SHEET ID HERE').getSheetByName('trend');</code>
Esta linea del script permite identificar la hoja del google sheets donde se va a ejecutar el script (hoja trend del google sheet PUT YOUR GOOGLE SHEET ID HERE)</p>

<p><code>  var date = Utilities.formatDate(new Date(), "GMT", "yyyy-MM-dd");</code>
Esta linea nos permite dar formato a la variable date, esto luego servirá al momento de insertarla en el google sheet.</p>

<p><code>  var range = sheet.getRange("A1:A").getValues();</code>
Esta linea nos permite objener el rango del que vamos a obtener los valores, para de acuerdo a esto más adelante ver cual es la ultima linea ingresada y hacer el ingreso en la linea de abajo.</p>

<p> El ciclo <b>for</b> nos permite identificar cual es la cantidad de Rows (filas) con datos, de este modo podremos saber la fila en la que debemos insertar nuestras ecuaciones.

<p><code> var row = RowIndex+2;</code>
Esta linea nos permite dar el valor de la linea donde debemos hacer la insercción de la fecha y las ecuaciones asociadas. El valor del contador es aumentado en 2 porque el conteo se hizo desde 0 y porque debemos colocarlo en la próxima fila. </p>

<p><code> var  Trivial = '=COUNTIFS(usuario!$A:$A,A'+row+',usuario!$D:$D,$B$1)';</code>
De las lineas 15 a la 19 se crean las variables con los valores de las ecuaciones que van a ser interdas de manera autonoma en cada ejecución del script. Note que se concatena el valor de la fila calculada en el paso anterior. </p>

<p><code> sheet.appendRow([date, Trivial, Low, Medium, High,sum]);</code>
En esta linea acomodamos la inserción de los datos de izquierda a derecha, desde la primera posición (A). Esta parte del código se encuentra en un condicional que es opcional, el cual solo permite que hayan inserciones de lunes a viernes. </p>

<h3> 3 - UpdateTrendSonar </h3>

<p><code> var sheet = SpreadsheetApp.openById('PUT YOUR GOOGLE SHEET ID HERE').getSheetByName('SonarCloud KS');</code>
Esta linea del script nos permite indicar la hoja del google sheet donde vamos a hacer la inseción de información, en este caso es la hoja SonarCloud KS del sheet PUT YOUR GOOGLE SHEET ID HERE.</p>

<p><code> var range = sheet.getRange("A1:A").getValues();</code>
Esta linea nos permite indicar el rango que va a ser tenido en cuenta para nuestro propósito.</p>

<p>Este ciclo <b>for</b> nos permite identificar el numero de la ultima Row(fila) con información en nuestro rango.</p>

<p><code> var row = RowIndex+1;</code>
Esta linea nos permite conocer el ultimo row con información en nuestro rango establecido. Se le suma 1 debido a que el contador inicia en la posición 0.</p>

<p><code> var COVERAGE = sheet.getRange("F2");</code>
Esta linea del script nos permite indicar la celda exacta donde se encuentra el valor del COVERAGE, en este caso en la cela F2.</p>

<p><code> var  Trend_COVERAGE = '=TREND(B2:B'+row+', $A$2:$A$'+row+')';</code>
En esta linea se crea la variable que contiene la ecuación a ser insertada en la celda del Coverage. Notese que se está concatenando el valor de row.</p>

<p><code> COVERAGE.setValue(Trend_COVERAGE);</code>
Esta linea finalmente hace la inserción del valor Trend_COVERAGE en la posición COVERAGE (F2).</p>

