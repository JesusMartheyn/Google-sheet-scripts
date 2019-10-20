# Google-sheet-scripts
This contains a set of useful scripts for automate tasks in google sheets.

<h3> 1 - DeleteDuplicate </h3>
<h3> 2 - UpdateDate </h3>

<p>Este script permite realizar una nueva entrada de fecha y ecuaciones para aquellos días inferiores a 5. A continuación explico un poco el código.</p>

<p><code> var sheet = SpreadsheetApp.openById('PUT YOUR GOOGLE SHEET ID HERE').getSheetByName('trend');</code>
Esta linea del script permite identificar la hoja del google sheets donde se va a ejecutar el script (hoja trend del google sheet PUT YOUR GOOGLE SHEET ID HERE)</p>

<p><code>  var date = Utilities.formatDate(new Date(), "GMT", "yyyy-MM-dd");</code>
Esta linea nos permite dar formato a la variable date, esto luego servirá al momento de insertarla en el google sheet.</p>

<p><code>  var range = sheet.getRange("A1:A").getValues(); </code>
Esta linea nos permite objener el rango del que vamos a obtener los valores, para de acuerdo a esto más adelante ver cual es la ultima linea ingresada y hacer el ingreso en la linea de abajo.</p>

<p> El ciclo <b>for</b> nos permite identificar cual es la cantidad de Rows (filas) con datos, de este modo podremos saber la fila en la que debemos insertar nuestras ecuaciones.

<p><code> var row = RowIndex+2; </code>
Esta linea nos permite dar el valor de la linea donde debemos hacer la insercción de la fecha y las ecuaciones asociadas. El valor del contador es aumentado en 2 porque el conteo se hizo desde 0 y porque debemos colocarlo en la próxima fila. </p>

<p><code> var  Trivial = '=COUNTIFS(usuario!$A:$A,A'+row+',usuario!$D:$D,$B$1)'; </code>
De las lineas 15 a la 19 se crean las variables con los valores de las ecuaciones que van a ser interdas de manera autonoma en cada ejecución del script. Note que se concatena el valor de la fila calculada en el paso anterior. </p>

<h3> 3 - UpdateTrendSonar </h3>

