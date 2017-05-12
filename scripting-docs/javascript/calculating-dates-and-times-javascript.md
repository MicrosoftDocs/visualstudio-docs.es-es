---
title: "Calcular fechas y horas (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "aritmética de fecha y hora [JavaScript]"
  - "JavaScript, fecha y hora"
  - "comparación de fecha [JavaScript]"
  - "cálculos de fecha y hora [JavaScript]"
ms.assetid: ea976f78-d934-479b-9056-880390d8bddd
caps.latest.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 34
---
# Calcular fechas y horas (JavaScript)
Puede usar el [objeto Date](../javascript/reference/date-object-javascript.md) para realizar tareas de calendario y de reloj habituales, como comparar fechas y calcular el tiempo transcurrido.  
  
## Establecer una fecha en la fecha actual  
 Cuando crea una instancia del [objeto Date](../javascript/reference/date-object-javascript.md) sin especificar una fecha, devuelve un valor que representa la fecha y hora actuales, incluidos el año, mes, día, hora, minuto, segundo y milisegundo.  Después, puede leer o modificar este valor de fecha y hora.  
  
 En el ejemplo siguiente se muestra cómo crear instancias de una fecha sin utilizar parámetros y mostrarla en el formato *mm\-dd\-yy*.  
  
```javascript  
var dt = new Date();  
  
// Display the month, day, and year. getMonth() returns a 0-based number.  
var month = dt.getMonth()+1;  
var day = dt.getDate();  
var year = dt.getFullYear();  
document.write(month + '-' + day + '-' + year);  
  
// Output: current month, day, year  
```  
  
## Establecer una fecha concreta  
 Puede establecer una fecha concreta pasando una cadena de fecha al constructor.  
  
```javascript  
var dt = new Date('8/24/2009');  
document.write(dt);  
  
// Output: Mon Aug 24 00:00:00 PDT 2009  
  
```  
  
> [!IMPORTANT]
>  La zona horaria que se muestra en la cadena de fecha corresponde a la zona horaria establecida en el equipo local.  
>   
>  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] es flexible en el formato de la cadena que se utiliza como parámetro.  Por ejemplo, puede escribir "8\-24\-2009", "24 de agosto, 2009" o "24 de agosto de 2009".  
  
 También puede especificar una hora.  En el ejemplo siguiente se muestra una manera de especificar una fecha y hora en formato ISO.  La "Z" indica la hora UTC.  
  
```javascript  
var dt = new Date('2010-06-09T15:20:00Z');  
document.write(dt);  
document.write("<br />");  
document.write(dt.toISOString());  
  
// Output:  
// Wed Jun 09 2010 08:20:00 GMT-0700 (Pacific Daylight Time)  
// 2010-06-09T15:20:00.000Z  
```  
  
 Para obtener más información sobre formatos de fecha como ISO, vea [Cadenas de fecha y hora](../javascript/date-and-time-strings-javascript.md).  
  
 En el ejemplo siguiente se muestran otras maneras de especificar una hora.  
  
```javascript  
var dtA = new Date('8/24/2009 14:52:10');  
  
// The parameters are year, month, day, hours, minutes, seconds.  
var dtB = new Date(2009, 7, 24, 14, 52, 10);  
document.write(dtA);  
document.write("<br/>");  
document.write(dtB);  
  
// Output:  
// Mon Aug 24 14:52:10 PDT 2009  
// Mon Aug 24 14:52:10 PDT 2009  
  
```  
  
## Sumar y restar días, meses y años  
 Puede utilizar los métodos getX y setX del objeto `Date` para establecer fechas y horas específicas.  
  
 En el siguiente ejemplo se muestra cómo puede establecer una fecha para el día anterior.  Observe que, en caso necesario, los valores de mes y año también se modifican.  
  
```javascript  
var myDate = new Date("1/1/1990");  
var dayOfMonth = myDate.getDate();  
myDate.setDate(dayOfMonth - 1);  
  
document.write(myDate);  
  
// Output: Sun Dec 31 00:00:00 PST 1989  
```  
  
 En el ejemplo siguiente se establece la fecha en el último día del mes restando un día al primer día del mes siguiente.  
  
> [!TIP]
>  Los meses del año se numeran de 0 \(enero\) a 11 \(diciembre\).  Los días de la semana se numeran de 0 \(domingo\) a 6 \(sábado\).  
  
```javascript  
var myDate = new Date("1/1/1990")  
myDate.setMonth(myDate.getMonth() + 1);  
  
myDate.setDate (myDate.getDate() - 1);  
  
document.write(myDate);  
  
// Output: Wed Jan 31 00:00:00 PST 1990  
  
```  
  
## Trabajar con días de la semana  
 El [método getDay](../javascript/reference/getday-method-date-javascript.md) obtiene el día de la semana como un número comprendido entre 0 \(domingo\) y 6 \(sábado\). \(Este método es diferente del [método getDate](../javascript/reference/getdate-method-date-javascript.md), que obtiene el día del mes como un número comprendido entre 1 y 31\).  
  
 En el ejemplo siguiente se establece la fecha del Día de Acción de Gracias, que en Estados Unidos es el cuarto jueves de noviembre.  El script encuentra el 1 de noviembre del año actual, después busca el primer jueves y le agrega tres semanas.  
  
```javascript  
var myDate = new Date();  
myDate.setHours(0, 0, 0, 0);  
  
myDate.setYear(2013);  
  
// Determine November 1.  
myDate.setDate(1);  
myDate.setMonth(10);  
  
// Find Thursday.  
var thursday = 4;  
while(myDate.getDay() != thursday) {  
    myDate.setDate(myDate.getDate() + 1);  
}  
  
// Add 3 weeks.  
myDate.setDate(myDate.getDate() + 21);  
  
document.write(myDate);  
  
// Output: Thu Nov 28 00:00:00 <time zone> 2013  
  
```  
  
## Calcular el tiempo transcurrido  
 El [método getTime](../javascript/reference/gettime-method-date-javascript.md) devuelve el número de milisegundos transcurridos desde la medianoche del 1 de enero de 1970.  Para cualquier fecha anterior a esa, devuelve un número negativo.  
  
 Puede usar el [método getTime](../javascript/reference/gettime-method-date-javascript.md) para establecer una hora inicial y final para calcular el tiempo transcurrido.  Se puede utilizar para medir unidades pequeñas, como unos segundos, y unidades grandes, como días.  
  
 En el ejemplo siguiente se calcula el tiempo transcurrido en segundos.  El [método getTime](../javascript/reference/gettime-method-date-javascript.md) obtiene el número de milisegundos desde la fecha cero.  
  
```javascript  
var startTime = new Date('1/1/1990');  
var startMsec = startTime.getMilliseconds();  
startTime.setTime(5000000);  
var elapsed = (startTime.getTime() - startMsec) / 1000;   
document.write(elapsed);  
  
// Output: 5000  
  
```  
  
 Para trabajar con unidades más controlables, puede dividir los milisegundos proporcionados por el [método getTime](../javascript/reference/gettime-method-date-javascript.md) por un número adecuado.  Por ejemplo, para convertir los milisegundos en días, divida el número por 86.400.000 \(1.000 milisegundos x 60 segundos x 60 minutos x 24 horas\).  
  
 En el siguiente ejemplo se muestra el tiempo que ha transcurrido desde el primer día del año especificado.  Se usan operaciones de división para calcular el tiempo transcurrido en días, horas, minutos y segundos.  No tiene en cuenta el horario de verano.  
  
```javascript  
// Set the unit values in milliseconds.  
var msecPerMinute = 1000 * 60;  
var msecPerHour = msecPerMinute * 60;  
var msecPerDay = msecPerHour * 24;  
  
// Set a date and get the milliseconds  
var date = new Date('6/15/1990');  
var dateMsec = date.getTime();  
  
// Set the date to January 1, at midnight, of the specified year.  
date.setMonth(0);  
date.setDate(1);  
date.setHours(0, 0, 0, 0);  
  
// Get the difference in milliseconds.  
var interval = dateMsec - date.getTime();  
  
// Calculate how many days the interval contains. Subtract that  
// many days from the interval to determine the remainder.  
var days = Math.floor(interval / msecPerDay );  
interval = interval - (days * msecPerDay );  
  
// Calculate the hours, minutes, and seconds.  
var hours = Math.floor(interval / msecPerHour );  
interval = interval - (hours * msecPerHour );  
  
var minutes = Math.floor(interval / msecPerMinute );  
interval = interval - (minutes * msecPerMinute );  
  
var seconds = Math.floor(interval / 1000 );  
  
// Display the result.  
document.write(days + " days, " + hours + " hours, " + minutes + " minutes, " + seconds + " seconds.");  
  
//Output: 164 days, 23 hours, 0 minutes, 0 seconds.  
```  
  
### Determinar la edad del usuario  
 En el siguiente ejemplo se toma el cumpleaños del usuario y se calcula la edad del usuario en años.  Para ello, se resta el año del nacimiento del año en curso y, a continuación, se resta 1 si el cumpleaños no se ha producido todavía en el año en curso.  
  
```javascript  
var birthday = new Date("8/1/1985");  
var today = new Date();  
var years = today.getFullYear() - birthday.getFullYear();  
  
// Reset birthday to the current year.  
birthday.setFullYear(today.getFullYear());  
  
// If the user's birthday has not occurred yet this year, subtract 1.  
if (today < birthday)  
{  
    years--;  
}  
document.write("You are " + years + " years old.");  
  
// Output: You are <number of years> years old.  
  
```  
  
## Comparar fechas  
 Al comparar fechas en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], debe tener en cuenta que el operador `==` devuelve `true` solo si las fechas situadas a ambos lados del operador hacen referencia al mismo objeto.  Por consiguiente, si tiene dos objetos `Date` independientes establecidos en la misma fecha, `date1 == date2` devuelve `false`.  Además, un objeto `Date` establecido con solo la fecha y sin la hora se inicializa en la medianoche de esa fecha.  Por lo tanto, si compara un objeto `Date` establecido sin un tiempo especificado en `Date.now`, por ejemplo, debe tener en cuenta que el primer objeto `Date` se establece en la medianoche y el objeto `Date.now` no.  
  
 En el siguiente ejemplo se comprueba si la fecha actual es igual, anterior o posterior a una fecha especificada.  Para establecer la fecha actual en `todayAtMidn`, el script crea un objeto `Date` para el año, mes y día en curso.  
  
```javascript  
// Get the current date at midnight.  
var now = new Date();   
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set specificDate to a specified date at midnight.  
var specificDate = new Date("9/21/2009");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() == specificDate.getTime())  
{  
    document.write("Same");  
}  
else  
{  
    document.write("Different");  
}  
  
//Output: Different  
```  
  
 Al modificar el ejemplo anterior, podemos comprobar si una fecha proporcionada está dentro de un intervalo determinado.  
  
```javascript  
// Get the current date at midnight.  
var now = new Date();  
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set start/end dates to a specified date (ISO format).  
var startDate = new Date("2009-06-09T15:20:00Z");  
var endDate = new Date("2011-06-09T15:20:00Z");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() > startDate.getTime() &&   
    todayAtMidn.getTime() < endDate.getTime()) {  
    document.write("Specified date is within this range.");  
}  
else {  
    document.write("Specified date is not in this range.");  
}  
  
// Output: Specified date is not in this range.  
```  
  
## Vea también  
 [Date \(Objeto\)](../javascript/reference/date-object-javascript.md)