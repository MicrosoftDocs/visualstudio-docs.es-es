---
title: "Cadenas de plantillas (JavaScript) | Microsoft Docs"
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
ms.assetid: f2e525a5-b0fc-49c3-95a0-641788e5c12a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Cadenas de plantillas (JavaScript)
En [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)], puede usar cadenas de plantillas para construir literales de cadena con expresiones incrustadas.  Las cadenas de plantillas también proporcionan compatibilidad integrada para cadenas multilíneas.  
  
 Para construir una cadena de plantillas, escriba la cadena entre acentos graves \(también llamados acentos invertidos\) \(\`\), en lugar de comillas simples o dobles.  En el ejemplo de código siguiente se muestra una cadena de plantillas simple.  
  
```  
`Template strings can include 'single quotes' and "double quotes" inline.`  
  
```  
  
 Las cadenas de plantillas pueden incluir saltos de línea sin necesidad de usar el carácter de avance de línea \(\\n\).  
  
```  
`Template strings can include line breaks and don't need the linefeed character.`  
```  
  
 El carácter $ se usa para especificar los marcadores de posición dentro de una cadena de plantillas.  La sintaxis es ${*expresión*}, donde *expresión* es cualquier expresión de JavaScript como una variable o función, tal como se muestra en el ejemplo siguiente.  
  
```  
var name = "Bob";  
var str = `Hello ${name}, how are you this fine ${partOfDay()}?`  
console.log(str);  
  
function partOfDay () {  
    var hour = new Date().getHours();  
  
    if (hours <= 12) {  
        return “morning”;  
    } else if (hours <= 5) {  
        return “afternoon”;  
    } else {  
        return “evening”;  
    }  
}  
  
// Output:  
// Hello Bob, how are you this fine afternoon?  
```  
  
 Las funciones de plantilla etiquetadas permiten modificar el valor de una cadena de plantillas con una función que se invoca con argumentos de la cadena de plantillas.  El primer argumento es una matriz de literales de cadena, delimitado por las expresiones de cadenas de plantillas que contiene, y el segundo argumento es una matriz \(un [parámetro Rest](../../javascript/functions-javascript.md)\) que contiene los valores de las expresiones de cadenas de plantillas.  
  
 En el ejemplo siguiente, se usa la función de plantilla etiquetada, buildURL, para construir una dirección URL.  La sintaxis está diseñada para usar el nombre de función seguido inmediatamente de la cadena de plantillas.  
  
```  
function buildURL(strArray, ...valArray) {  
    var newUrl = strArray[0] + "ja-ja" + "/" + valArray[1] +  
    "/" + valArray[2];  
  
    return newUrl;  
}  
  
var lang = "en-us";  
var a = "library";  
var b = "dn771551.aspx";  
  
// Call the tagged template function.  
var url = buildURL`http://msdn.microsoft.com/${lang}/${a}/${b}`;  
  
console.log(url);  
  
// Output:  
// http://msdn.microsoft.com/ja-ja/library/dn771551.aspx  
```  
  
 Si necesita acceder a los valores de cadena sin formato que se pasaron, el primer argumento pasado a la función de plantilla etiquetada admite una propiedad `raw` que devuelve el formato de cadena sin formato de las cadenas que se pasaron.  
  
```  
function buildURL(strArray, ...valArray) {  
    console.log(strArray.raw);  
}  
  
var lang = "en-us";  
var a = "library";  
var b = "dn771551.aspx";  
  
// Call the tagged template function.  
var url = buildURL`http://msdn.microsoft.com/${lang}/${a}/${b}`;  
  
// Ouput:  
// http://msdn.microsoft.com/  
// /  
// en-us  
// library  
```  
  
> [!NOTE]
>  También puede usar la función [String.raw](../../javascript/reference/string-raw-function-javascript.md) para devolver el formato de cadena sin formato de una cadena de plantillas.  
  
## Vea también  
 [Referencia del lenguaje JavaScript](../../javascript/javascript-language-reference.md)   
 [JavaScript avanzado](../../javascript/advanced/advanced-javascript.md)