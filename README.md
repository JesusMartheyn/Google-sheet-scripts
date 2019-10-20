# Google-sheet-scripts
This contains a set of useful scripts for automate tasks in google sheets.

<h3> 1 - DeleteDuplicated </h3>
<h3> 2 - UpdateDate </h3>
Este script permite realizar una nueva entrada de fecha y ecuaciones para aquellos días inferiores a 5. A continuación explico un poco el código.

  var sheet = SpreadsheetApp.openById('PUT YOUR GOOGLE SHEET ID HERE').getSheetByName('trend');  
  var date = Utilities.formatDate(new Date(), "GMT", "yyyy-MM-dd");   
  var range = sheet.getRange("A1:A").getValues();

Linea 1. Esta linea del script permite identificar la hoja del google sheets donde se va a ejecutar el script (hoja trend del google sheet
<h3> 3 - UpdateTrend </h3>
