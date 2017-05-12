---
title: "toLocaleString (Number) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 42c05252-13c1-4943-b1a4-b33285aeab3e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# toLocaleString (Number)
Convierte un número en una cadena mediante la configuración regional actual o especificada.  
  
## Sintaxis  
  
```  
  
numberObj.toLocaleString([locales][, options])   
```  
  
#### Parámetros  
 `numberObj`  
 Requerido.  Objeto `Number` que se va a convertir.  
  
 `locales`  
 Opcional.  Un matriz de cadenas de configuración regional que contienen una o más etiquetas de configuración regional o lenguaje.  Si incluye más de una cadena de la configuración regional, enumérelas en orden descendente de prioridad para de manera que la primera entrada se la configuración regional preferida.  Si omite este parámetro, se usa la configuración regional predeterminada del runtime de JavaScript.  
  
 `options`  
 Opcional.  Un objeto que contiene una o más propiedades que especifican opciones de comparación.  
  
## Comentarios  
 A partir de Internet Explorer 11, `toLocaleString` utiliza `Intl.NumberFormat` internamente para crear comparaciones, lo que agrega compatibilidad para los parámetros `locales` y `options` .  Para obtener más información sobre estos parámetros, vea [Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md).  
  
> [!IMPORTANT]
>  Los parámetros `locales` y `options` no se admiten en todos los modos de documento y versiones de explorador.  Para obtener más información, consulte la sección Requisitos.  
  
> [!NOTE]
>  Si omite el parámetro `locales`, utilice `toLocaleString` para mostrar solo los resultados a un usuario; nunca utilícelo para calcular valores desde un script, porque el resultado devuelto es específico del equipo \(el método devuelve la configuración regional actual\).  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo usar el método `toLocaleString` sin parámetros.  
  
```javascript  
var n, s;  
n = new Number(100);  
s = "Current locale value is: ";  
s += n.toLocaleString();                 
document.write(s);  
  
// Output:  
// The value 100 as represented by the current locale.  
```  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo utilizar el método `toLocaleString` con opciones de configuración regional y comparación especificadas.  
  
```javascript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
document.write(number.toLocaleString("en-US"));  
// 123,456,789  
document.write(number.toLocaleString("ja-JP"));  
// 123,456,789  
document.write(number.toLocaleString("ar-SA", options1));  
// ١٢,٣٤٥,٦٧٨,٩٠٠ %  
document.write(number.toLocaleString("hi-IN", options2));  
// ₹ 12,34,56,789.00  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 Los parámetros `locales` y `options`:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vea también  
 [toLocaleDateString \(Método, Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)