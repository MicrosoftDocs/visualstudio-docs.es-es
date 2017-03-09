---
title: "JavaScript en Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# JavaScript en Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

JavaScript es un lenguaje de primera clase en Visual Studio.  Puede usar la mayoría de las ayudas de edición estándar \(fragmentos de código, IntelliSense, etc.\) al escribir código JavaScript en el IDE de Visual Studio.  Puede escribir código JavaScript para muchos tipos de aplicaciones y servicios.  
  
 Para la documentación de referencia del lenguaje JavaScript, vea [JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).  
  
 Es posible que haya versiones o extensiones específicas de Visual Studio que requieran el desarrollo de ciertos tipos de aplicaciones y servicios con HTML y JavaScript.  La lista siguiente contiene vínculos para obtener más información.  
  
-   Para crear aplicaciones multiplataforma con Apache Cordova, [obtenga Visual Studio Tools para Apache Cordova](http://go.microsoft.com/fwlink/p/?LinkId=397606).  
  
-   Para crear aplicaciones de la [Tienda Windows](http://dev.windows.com/develop), [Windows Phone](http://dev.windows.com/develop) y universales \(compatibles con ambas plataformas\), [obtenga las herramientas](http://dev.windows.com/en-us/develop/downloads).  
  
-   Para crear servicios basados en la nube, visite el [sitio de Microsoft Azure](http://azure.microsoft.com/documentation/).  
  
-   Para crear sitios web y aplicaciones web, [visite el sitio ASP.NET](http://www.asp.net/get-started/websites).  
  
    > [!NOTE]
    >  Puede crear un sitio web ASP.Net vacío y usarlo para la programación con HTML, CSS y JavaScript.  El archivo Webconfig proporcionado por ASP.NET habilita la depuración en Visual Studio \(o puede usar herramientas de F12 al ejecutar la aplicación\).  
  
 El editor de JavaScript en Visual Studio proporciona compatibilidad con IntelliSense.  Para obtener más información, vea [IntelliSense para JavaScript](../ide/javascript-intellisense.md).  
  
## Novedades de JavaScript  
 En la tabla siguiente se enumeran las nuevas características para JavaScript.  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Clases|La nueva sintaxis admite la declaración de [clases](../Topic/class%20Statement%20\(JavaScript\).md).|  
|Promises|[Promises](../Topic/Promise%20Object%20\(JavaScript\).md) permite una codificación asincrónica más fácil y limpia.  Se admiten constructores Promise junto con los métodos de utilidad `all` y `race`.|  
|Iteradores|Ahora puede iterar por objetos iterables \(incluidas matrices, objetos similares a matrices e iteradores\), invocando un enlace de iteración personalizado con instrucciones que se ejecutarán para el valor de cada propiedad distintiva.  Para obtener más información, consulte [Iteradores y generadores](../Topic/Iterators%20and%20Generators%20\(JavaScript\).md). **Note:**  Todavía no se admiten generadores.|  
|Funciones de flecha|La función de flecha \(\=\>\) proporciona la sintaxis abreviada para la palabra clave `function` que incluye un enlace léxico `this`.|  
|Nuevos métodos para objetos integrados|Los objetos integrados [Array \(Objeto\)](../Topic/Array%20Object%20\(JavaScript\).md), [Math \(Objeto\)](../Topic/Math%20Object%20\(JavaScript\).md), [Number \(Objeto\)](../Topic/Number%20Object%20\(JavaScript\).md), [Object \(Objeto\)](../Topic/Object%20Object%20\(JavaScript\).md) y [String \(Objeto\)](../Topic/String%20Object%20\(JavaScript\).md) incluyen numerosas propiedades y funciones de utilidad nuevas para manipular e inspeccionar datos.|  
|Mejoras literales de objeto|Los objetos ahora admiten propiedades calculadas, definiciones de método concisas y sintaxis abreviada para las propiedades cuyo valor se inicializa en una variable con el mismo nombre.  Para obtener más información, vea [Crear objetos](../Topic/Creating%20Objects%20\(JavaScript\).md).|  
|Servidores proxy|Los [servidores proxy](../Topic/Proxy%20Object%20\(JavaScript\).md) permiten un comportamiento personalizado para los objetos.|  
|Parámetros de REST|Los parámetros de REST permiten activar argumentos consecutivos en una llamada de función a una matriz.  Para obtener más información, vea [Funciones](../Topic/Functions%20\(JavaScript\).md).|  
|Operador de propagación|El [operador de propagación](../Topic/Spread%20Operator%20\(...\)%20\(JavaScript\).md) \(`…`\) expande expresiones iterables en argumentos individuales.  Por ejemplo, `a.b(…array)` es aproximadamente igual a que `a.b.apply(a, array)`.|  
|Símbolos|Los objetos [Símbolo](../Topic/Symbol%20Object%20\(JavaScript\).md) permiten agregar propiedades a los objetos existentes sin posibilidad de interferencias con las propiedades de objeto existentes, sin visibilidad no intencionada y sin otras adiciones no coordinadas por parte de otro código.|  
|Cadenas de plantillas|Las [cadenas de plantillas](../Topic/Template%20Strings%20\(JavaScript\).md) son literales de cadena que permiten evaluar y concatenar las expresiones con el literal de cadena.|  
|Mejoras de Unicode|Se realizaron mejoras en la compatibilidad con Unicode.  Por ejemplo, un nuevo formato de secuencia de escape admite puntos de código astral \(puntos de código con más de cuatro dígitos hexadecimales\).  Para obtener más información, consulte [Caracteres especiales](../Topic/Special%20Characters%20\(JavaScript\).md).|  
|WeakSet|Un [WeakSet](../Topic/WeakSet%20Object%20\(JavaScript\).md) es una colección de objetos que se pueden recoger si no se hace referencia a ellos en ningún otro lugar.|