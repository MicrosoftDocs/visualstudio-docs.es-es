---
title: "Novedades de JavaScript | Microsoft Docs"
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
ms.assetid: 342b68ef-df93-48c4-81de-bdf6b6ce58d9
caps.latest.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 33
---
# Novedades de JavaScript
Este documento enumera las características nuevas en JavaScript que se admiten tanto en [modo de borde](http://blogs.msdn.com/b/ie/archive/2014/11/11/living-on-the-edge-our-next-step-in-interoperability.aspx), [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)], y las aplicaciones de la Tienda de Windows Phone.  
  
 Para averiguar qué elementos de JavaScript son compatibles con el modo de borde y dejaron de usarse en aplicaciones de la [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)], consulte [Información de versiones](../javascript/reference/javascript-version-information.md).  
  
> [!IMPORTANT]
>  Para obtener información sobre cómo crear aplicaciones de la [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] y la Tienda Windows Phone usando JavaScript, incluida información sobre el editor de JavaScript de Visual Studio y otras características, consulte [Desarrollar aplicaciones de la Tienda Windows con Visual Studio 2013](http://go.microsoft.com/fwlink/p/?LinkID=238263).  
  
## Nuevas características de JavaScript  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Clases|La nueva sintaxis admite la declaración de [clases](../javascript/reference/class-statement-javascript.md).|  
|Promises|[Promises](../javascript/reference/promise-object-javascript.md) permite una codificación asincrónica más fácil y limpia.  Se admiten constructores Promise junto con los métodos de utilidad `all` y `race`.|  
|Iteradores|Ahora puede iterar por objetos iterables \(incluidas matrices, objetos similares a matrices e iteradores\), invocando un enlace de iteración personalizado con instrucciones que se ejecutarán para el valor de cada propiedad distintiva.  Para obtener más información, consulte [Iteradores y generadores](../javascript/advanced/iterators-and-generators-javascript.md). **Note:**  Todavía no se admiten generadores.|  
|Funciones de flecha|La función de flecha \(\=\>\) proporciona la sintaxis abreviada para la palabra clave `function` que incluye un enlace léxico `this`.|  
|Nuevos métodos para objetos integrados|Los objetos integrados [Array \(Objeto\)](../javascript/reference/array-object-javascript.md), [Math \(Objeto\)](../javascript/reference/math-object-javascript.md), [Number \(Objeto\)](../javascript/reference/number-object-javascript.md), [Object \(Objeto\)](../javascript/reference/object-object-javascript.md) y [String \(Objeto\)](../javascript/reference/string-object-javascript.md) incluyen numerosas propiedades y funciones de utilidad nuevas para manipular e inspeccionar datos.|  
|Mejoras literales de objeto|Los objetos ahora admiten propiedades calculadas, definiciones de método concisas y sintaxis abreviada para las propiedades cuyo valor se inicializa en una variable con el mismo nombre.  Para obtener más información, vea [Crear objetos](../javascript/creating-objects-javascript.md).|  
|Servidores proxy|Los [servidores proxy](../javascript/reference/proxy-object-javascript.md) permiten un comportamiento personalizado para los objetos.|  
|Parámetros de REST|Los parámetros de REST permiten activar argumentos consecutivos en una llamada de función a una matriz.  Para obtener más información, vea [Funciones](../javascript/functions-javascript.md).|  
|Operador de propagación|El [operador de propagación](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md) \(`…`\) expande expresiones iterables en argumentos individuales.  Por ejemplo, `a.b(…array)` es aproximadamente igual a que `a.b.apply(a, array)`.|  
|Símbolos|Los objetos [Símbolo](../javascript/reference/symbol-object-javascript.md) permiten agregar propiedades a los objetos existentes sin posibilidad de interferencias con las propiedades de objeto existentes, sin visibilidad no intencionada y sin otras adiciones no coordinadas por parte de otro código.|  
|Cadenas de plantillas|Las [cadenas de plantillas](../javascript/advanced/template-strings-javascript.md) son literales de cadena que permiten evaluar y concatenar las expresiones con el literal de cadena.|  
|Mejoras de Unicode|Se realizaron mejoras en la compatibilidad con Unicode.  Por ejemplo, un nuevo formato de secuencia de escape admite puntos de código astral \(puntos de código con más de cuatro dígitos hexadecimales\).  Para obtener más información, consulte [Caracteres especiales](../javascript/advanced/special-characters-javascript.md).|  
|WeakSet|Un [WeakSet](../javascript/reference/weakset-object-javascript.md) es una colección de objetos que se pueden recoger si no se hace referencia a ellos en ningún otro lugar.|  
  
## Vea también  
 [Referencia del lenguaje JavaScript](../javascript/javascript-language-reference.md)