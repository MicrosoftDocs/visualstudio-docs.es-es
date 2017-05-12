---
title: "Errores en tiempo de ejecuci&#243;n de JavaScript | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT-32725"
  - "VS.WebClient.Help.SCRIPT7002"
  - "VS.WebClient.Help.SCRIPT1001"
  - "VS.WebClient.Help.SCRIPT16389"
  - "VS.WebClient.HelpSCRIPT50"
  - "VS.WebClient.HelpSCRIPT70"
  - "VS.WebClient.HelpSCRIPT87"
  - "VS.WebClient.HelpSCRIPT65535"
  - "VS.WebClient.HelpSCRIPT445"
  - "VS.WebClient.HelpSCRIPT600"
  - "VS.WebClient.HelpSCRIPT2343"
  - "VS.WebClient.HelpSCRIPT122"
  - "VS.WebClient.HelpSCRIPT28"
  - "VS.WebClient.HelpSCRIPT16386"
  - "VS.WebClient.HelpSCRIPT7015"
  - "VS.WebClient.HelpSCRIPT3"
  - "VS.WebClient.HelpSCRIPT16388"
  - "VS.WebClient.HelpSCRIPT14"
  - "VS.WebClient.HelpSCRIPT12030"
  - "VS.WebClient.HelpSCRIPT12029"
  - "VS.WebClient.HelpSCRIPT1001"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "errores [JavaScript]"
  - "errores en tiempo de ejecución, JavaScript"
ms.assetid: c111469d-8f31-4bde-9d46-16d58775db7d
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Errores en tiempo de ejecuci&#243;n de JavaScript
Los errores en tiempo de ejecución de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se producen cuando el script intenta realizar una acción que el sistema no puede ejecutar. Estos errores pueden aparecer cuando se están evaluando expresiones variables o se está asignando la memoria.  
  
## Errores de Windows en tiempo de ejecución  
 Si usa la API de Windows en tiempo de ejecución en su aplicación de la [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], es posible que vea errores de JavaScript que se hayan convertido a partir de valores HRESULT de Windows en tiempo de ejecución. Los valores HRESULT de Windows en tiempo de ejecución que se encuentran en un intervalo superior a 0x80070000 se convierten en errores de JavaScript al tomar el valor hexadecimal de los bits inferiores y convertirlo en un decimal. Por ejemplo, el valor HRESULT 0x80070032 se convierte en el valor decimal 50, y el error de JavaScript es SCRIPT50. El valor HRESULT 0x80074005 se convierte en el valor decimal 16389, y el error de JavaScript es SCRIPT16389.  
  
## Errores  
  
|Número de error|Descripción|  
|---------------------|-----------------|  
|5|[Se denegó el acceso](../../javascript/misc/access-is-denied.md)|  
|438|[El objeto no es compatible con esta propiedad ni con este método](../../javascript/misc/object-doesn-t-support-this-property-or-method.md)|  
|1001|Memoria agotada|  
|5029|[La longitud de la matriz debe ser un valor entero positivo finito](../../javascript/misc/array-length-must-be-a-finite-positive-integer.md)|  
|5030|[Se debe asignar un valor entero positivo finito a la longitud de la matriz](../../javascript/misc/array-length-must-be-assigned-a-finite-positive-number.md)|  
|5028|[Se esperaba un objeto de argumentos o matriz](../../javascript/misc/array-or-arguments-object-expected.md)|  
|5010|[Se esperaba un tipo booleano](../../javascript/misc/boolean-expected.md)|  
|5003|[No se puede asignar al resultado de una función](../../javascript/misc/cannot-assign-to-a-function-result.md)|  
|5000|[No se puede asignar a 'this'](../../javascript/misc/cannot-assign-to-this.md)|  
|5034|[Referencia circular en un argumento de valor no admitida](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|  
|5006|[Se esperaba un objeto de fecha](../../javascript/misc/date-object-expected.md)|  
|5015|[Se esperaba un objeto enumerador](../../javascript/misc/enumerator-object-expected.md)|  
|5022|[Excepción producida y no detectada](../../javascript/misc/exception-thrown-and-not-caught.md)|  
|5020|[Se esperaba '\)' en la expresión regular](../../javascript/misc/expected-right-parenthesis-in-regular-expression-javascript.md)|  
|5019|[Se esperaba '&#93;' en la expresión regular](../../javascript/misc/expected-right-square-bracket-in-regular-expression-javascript.md)|  
|5023|[La función no tiene un objeto prototipo válido](../../javascript/misc/function-does-not-have-a-valid-prototype-object.md)|  
|5002|[Se esperaba una función](../../javascript/misc/function-expected.md)|  
|5008|[Asignación no válida](../../javascript/misc/illegal-assignment-javascript.md)|  
|5021|[Intervalo no válido en el juego de caracteres](../../javascript/misc/invalid-range-in-character-set-javascript.md)|  
|5035|[Argumento reemplazante no válido](../../javascript/misc/invalid-replacer-argument.md)|  
|5014|[Se esperaba un objeto JavaScript](../../javascript/misc/javascript-object-expected.md)|  
|5001|[Se esperaba un número](../../javascript/misc/number-expected.md)|  
|5007|[Se esperaba un objeto](../../javascript/misc/object-expected.md)|  
|5012|[Se esperaba un objeto miembro](../../javascript/misc/object-member-expected.md)|  
|5016|[Se esperaba un objeto de expresión regular](../../javascript/misc/regular-expression-object-expected.md)|  
|5005|[Se esperaba una cadena](../../javascript/misc/string-expected.md)|  
|5017|[Error de sintaxis en la expresión regular](../../javascript/misc/syntax-error-in-regular-expression-javascript.md)|  
|5026|[El número de dígitos fraccionarios está fuera de intervalo](../../javascript/misc/the-number-of-fractional-digits-is-out-of-range.md)|  
|5027|[La precisión está fuera de intervalo](../../javascript/misc/the-precision-is-out-of-range.md)|  
|5025|[El URI que se desea descodificar no tiene una codificación válida](../../javascript/misc/the-uri-to-be-decoded-is-not-a-valid-encoding.md)|  
|5024|[El URI que se desea codificar contiene un carácter no válido](../../javascript/misc/the-uri-to-be-encoded-contains-an-invalid-character.md)|  
|5009|[Identificador no definido](../../javascript/misc/undefined-identifier.md)|  
|5018|[Cuantificador inesperado](../../javascript/misc/unexpected-quantifier-javascript.md)|  
|5013|[Se esperaba VBArray](../../javascript/misc/vbarray-expected.md)|  
  
## Vea también  
 [Errores de sintaxis de JavaScript](../../javascript/reference/javascript-syntax-errors.md)