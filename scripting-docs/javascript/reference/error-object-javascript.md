---
title: "Error (Objeto de JavaScript) | Microsoft Docs"
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
  - "Error"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Error (objeto)"
ms.assetid: 0b27d6ec-3997-4e91-a6c0-5afbaf494db7
caps.latest.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 25
---
# Error (Objeto de JavaScript)
Contiene información acerca de los errores.  
  
## Sintaxis  
  
```  
  
      errorObj = new Error()  
errorObj = new Error([number])  
errorObj = new Error([number[, description]])  
```  
  
## Parámetros  
 `errorObj`  
 Obligatorio.  Nombre de variable a la que se asigna el objeto `Error`.  La asignación de variables se omite al crear el error mediante una instrucción `throw`.  
  
 `number`  
 Opcional.  Valor numérico asignado a un error.  Si se omite, será cero.  
  
 `description`  
 Opcional.  Cadena breve que describe un error.  Si se omite, será una cadena vacía.  
  
## Comentarios  
 Siempre que se produce un error en tiempo de ejecución, se crea una instancia del objeto `Error` para describir el error.  Esta instancia tiene dos propiedades intrínsecas que contienen la descripción del error \(propiedad `description`\) y el número de error \(propiedad `number`\).  Para obtener más información, vea [Errores en tiempo de ejecución de JavaScript](../../javascript/reference/javascript-run-time-errors.md).  
  
 Un número de error es un valor de 32 bits.  La palabra de 16 bits superior es el código de componente, mientras que la palabra inferior es el código de error real.  
  
 Los objetos `Error` también se pueden crear explícitamente con la sintaxis anterior, o se pueden producir con la instrucción `throw`.  En ambos casos, puede agregar cualquier propiedad que elija para expandir la capacidad del objeto `Error`.  
  
 Normalmente, la variable local que se crea en una instrucción **try...catch** hace referencia al objeto `Error` creado implícitamente.  Como consecuencia, puede utilizar el número y la descripción del error como prefiera.  
  
## Ejemplo  
 En el método siguiente se demuestra el uso del objeto `Error`.  
  
```  
function checkInput(x) {  
    try  
    {  
        if (isNaN(parseInt(x))) {  
            throw new Error("Input is not a number.");  
        }  
    }  
    catch(e)  
    {  
        document.write(e.description);  
    }  
}  
  
checkInput("not a number");  
```  
  
## Ejemplo  
 En el ejemplo siguiente se demuestra el uso del objeto `Error` creado implícitamente.  
  
```javascript  
try  
   {  
   // Cause an error.  
   x = y;  
   }  
catch(e)  
   {  
      document.write(e);  
      document.write ("<br />");  
  
      document.write ("Number: ");  
      document.write (e.number & 0xFFFF);  
      document.write ("<br />");  
  
      document.write ("Facility Code: ");  
      document.write(e.number>>16 & 0x1FFF);  
      document.write ("<br />");  
  
      document.write ("Description: ");  
      document.write (e.description);  
   }  
  
// Output:  
// ReferenceError: 'y' is undefined  
// Number: 5009  
// Facility Code: 10  
// Description: 'y' is undefined  
  
```  
  
## Métodos  
 [toString \(Método, Error\)](../../javascript/reference/tostring-method-error.md) &#124; [valueOf \(Método, Date\)](../../javascript/reference/valueof-method-date.md)  
  
## Propiedades  
 [constructor \(Propiedad, Error\)](../../javascript/reference/constructor-property-error.md) &#124; [description \(Propiedad\)](../../javascript/reference/description-property-error-javascript.md) &#124; [message \(Propiedad\)](../../javascript/reference/message-property-error-javascript.md) &#124; [name \(Propiedad\)](../../javascript/reference/name-property-error-javascript.md) &#124; [number \(Propiedad\)](../../javascript/reference/number-property-error-javascript.md) &#124; [prototype \(Propiedad, Error\)](../../javascript/reference/prototype-property-error.md) &#124; [stack \(Propiedad, Error\)](../../javascript/reference/stack-property-error-javascript.md) &#124; [stackTraceLimit \(Propiedad, Error\)](../../javascript/reference/stacktracelimit-property-error-javascript.md)  
  
## Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Vea también  
 [new \(Operador\)](../../javascript/reference/new-operator-decrementjavascript.md)   
 [throw \(Instrucción\)](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally \(Instrucción\)](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [var \(Instrucción\)](../../javascript/reference/var-statement-javascript.md)   
 [Aplicación de ejemplo Hilo JavaScript \(Tienda Windows\)](http://hilojs.codeplex.com/SourceControl/latest)