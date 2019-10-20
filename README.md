# Google-sheet-scripts
This contains a set of useful scripts for automate tasks in google sheets.

<h3> 1 - DeleteDuplicated </h3>
<h3> 2 - UpdateDate </h3>

<p>Este script permite realizar una nueva entrada de fecha y ecuaciones para aquellos días inferiores a 5. A continuación explico un poco el código.</p>

<p><code> var sheet = SpreadsheetApp.openById('PUT YOUR GOOGLE SHEET ID HERE').getSheetByName('trend');</code>
Esta linea del script permite identificar la hoja del google sheets donde se va a ejecutar el script (hoja trend del google sheet PUT YOUR GOOGLE SHEET ID HERE)</p>

<p><code>  var date = Utilities.formatDate(new Date(), "GMT", "yyyy-MM-dd");</code>
Esta linea nos permite dar formato a la variable date, esto luego servirá al momento de insertarla en el google sheet.</p>

<p><code>  var range = sheet.getRange("A1:A").getValues();</code>
Esta linea nos permite objener el rango del que vamos a obtener los valores, para de acuerdo a esto más adelante ver cual es la ultima linea ingresada y hacer el ingreso en la linea de abajo.</p>

<h3> 3 - UpdateTrend </h3>
