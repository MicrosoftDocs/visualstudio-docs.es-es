---
title: "JSON.parse (Funci&#243;n de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "JSON.parse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JSON.parse (método)"
  - "parse JSON (método)"
ms.assetid: 20f00d31-5ab5-4c3c-ab49-2534fc39a9b4
caps.latest.revision: 41
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 41
---
# JSON.parse (Funci&#243;n de JavaScript)
Convierte una cadena de la notación de objetos de JavaScript \(JSON\) en un objeto.  
  
## Sintaxis  
  
```  
JSON.parse(text [, reviver])  
```  
  
## Parámetros  
 `text`  
 Obligatorio. Una cadena JSON válida.  
  
 `reviver`  
 Opcional. Función que transforma los resultados. Se llama a esta función para cada miembro del objeto. Si un miembro contiene objetos anidados, estos se transforman antes que el objeto principal. Para cada miembro, ocurre lo siguiente:  
  
-   Si `reviver` devuelve un valor válido, el valor del miembro se reemplaza con el valor transformado.  
  
-   Si `reviver` devuelve el mismo valor que recibió, el valor del miembro no se modifica.  
  
-   Si `reviver` devuelve `null` o `undefined`, se elimina el miembro.  
  
## Valor devuelto  
 Un objeto o matriz.  
  
## Excepciones  
 Si esta función causa un error de análisis de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] \(como "SCRIPT1014: Carácter no válido"\), el texto de entrada no cumple la sintaxis de JSON. Para corregir el error, realice uno de estos procedimientos:  
  
-   Modifica el argumento `text` para que sea conforme con la sintaxis de JSON. Para más información, vea la sección [Notación de sintaxis BNF](http://go.microsoft.com/fwlink/?LinkId=125203) de objetos JSON.  
  
     Por ejemplo, si la respuesta está en formato JSONP en lugar de JSON puro, pruebe este código en el objeto de respuesta:  
  
    ```javascript  
    var fixedResponse = response.responseText.replace(/\\'/g, "'");  
    var jsonObj = JSON.parse(fixedResponse);  
    ```  
  
-   Asegúrese de que el argumento `text` se haya serializado con una implementación conforme a JSON, como `JSON.stringify`.  
  
-   Ejecute el argumento `text` en un validador de JSON como [JSLint](http://www.jslint.com/) para ayudar a identificar errores de sintaxis.  
  
## Ejemplo  
 En el ejemplo siguiente se usa `JSON.parse` para convertir una cadena JSON en un objeto.  
  
```javascript  
var jsontext = '{"firstname":"Jesper","surname":"Aaberg","phone":["555-0100","555-0120"]}';  
var contact = JSON.parse(jsontext);  
document.write(contact.surname + ", " + contact.firstname);  
document.write(contact.phone[1]);  
// Output:  
// Aaberg, Jesper  
// 555-0100  
```  
  
## Ejemplo  
 En el ejemplo siguiente se convierte una matriz en una cadena JSON mediante `JSON.stringify` y, a continuación, se convierte la cadena de nuevo en una matriz mediante `JSON.parse`.  
  
```javascript  
var arr = ["a", "b", "c"];  
var str = JSON.stringify(arr);  
document.write(str);  
document.write ("<br/>");  
  
var newArr = JSON.parse(str);  
  
while (newArr.length > 0) {  
    document.write(newArr.pop() + "<br/>");  
}  
  
// Output:  
// ["a","b","c"]  
// c  
// b  
// a  
```  
  
## Ejemplo  
 La función `reviver` se suele usar para transformar la representación JSON de las cadenas de fecha de Organización internacional de normalización \(ISO\) en objetos `Date` con el formato de hora universal coordinada \(UTC\). En este ejemplo se usa `JSON.parse` para deserializar una cadena de fecha con formato ISO. La función `dateReviver` devuelve objetos `Date` para los miembros a los que se da formato como cadenas de fecha ISO.  
  
```javascript  
var jsontext = '{ "hiredate": "2008-01-01T12:00:00Z", "birthdate": "2008-12-25T12:00:00Z" }';  
var dates = JSON.parse(jsontext, dateReviver);  
document.write(dates.birthdate.toUTCString());  
  
function dateReviver(key, value) {  
    var a;  
    if (typeof value === 'string') {  
        a = /^(\d{4})-(\d{2})-(\d{2})T(\d{2}):(\d{2}):(\d{2}(?:\.\d*)?)Z$/.exec(value);  
        if (a) {  
            return new Date(Date.UTC(+a[1], +a[2] - 1, +a[3], +a[4],  
                            +a[5], +a[6]));  
        }  
    }  
    return value;  
};  
  
// Output:  
// Thu, 25 Dec 2008 12:00:00 UTC  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## Vea también  
 [JSON.stringify \(Función\)](../../javascript/reference/json-stringify-function-javascript.md)   
 [toJSON \(Método, Date\)](../../javascript/reference/tojson-method-date-javascript.md)   
 [Aplicación de ejemplo de la plantilla Hub \(Tienda Windows\)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)