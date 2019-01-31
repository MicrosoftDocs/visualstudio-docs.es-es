---
title: JavaScript
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-javascript
ms.topic: conceptual
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 962657d19026f85e98b1f1d22241aa57013d7df6
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834077"
---
# <a name="javascript-in-visual-studio"></a>JavaScript en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript es un lenguaje de primera clase en Visual Studio. Puede usar la mayoría de las ayudas de edición estándar (fragmentos de código, IntelliSense, etc.) al escribir código JavaScript en el IDE de Visual Studio. Puede escribir código JavaScript para muchos tipos de aplicaciones y servicios.

 Para obtener documentación de referencia del lenguaje JavaScript, consulte el tema sobre [JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).

 Es posible que haya versiones o extensiones específicas de Visual Studio que requieran el desarrollo de ciertos tipos de aplicaciones y servicios con HTML y JavaScript. La lista siguiente contiene vínculos para obtener más información.

- Para crear aplicaciones multiplataforma con Apache Cordova, [obtenga Visual Studio Tools para Apache Cordova](http://go.microsoft.com/fwlink/p/?LinkId=397606).

- Para crear aplicaciones de la [Tienda Windows](http://dev.windows.com/develop), [Windows Phone](http://dev.windows.com/develop) y universales (compatibles con ambas plataformas), [obtenga las herramientas](http://dev.windows.com/develop/downloads).

- Para crear servicios basados en la nube, visite el [sitio de Microsoft Azure](http://azure.microsoft.com/documentation/).

- Para crear sitios web y aplicaciones web, [visite el sitio ASP.NET](http://www.asp.net/get-started/websites).

  > [!NOTE]
  >  Puede crear un sitio web ASP.Net vacío y usarlo para la programación con HTML, CSS y JavaScript. El archivo Webconfig proporcionado por ASP.NET habilita la depuración en Visual Studio (o puede usar herramientas de F12 al ejecutar la aplicación).

  El editor de JavaScript en Visual Studio proporciona compatibilidad con IntelliSense. Para obtener más información, vea [IntelliSense de JavaScript](../ide/javascript-intellisense.md).

## <a name="whats-new-in-javascript"></a>Novedades de JavaScript
 En la tabla siguiente se enumeran las nuevas características para JavaScript.

|Característica|Descripción|
|-------------|-----------------|
|Clases|La nueva sintaxis admite la declaración de [clases](/visualstudio/scripting-docs/javascript/reference/class-statement-javascript).|
|Promises|[Promises](/visualstudio/scripting-docs/javascript/reference/promise-object-javascript) permite una codificación asincrónica más fácil y limpia. Se admiten constructores Promise junto con los métodos de utilidad `all` y `race`.|
|Iterators|Ahora puede iterar por objetos iterables (incluidas matrices, objetos similares a matrices e iteradores), invocando un enlace de iteración personalizado con instrucciones que se ejecutarán para el valor de cada propiedad distintiva. Para más información, vea [Iteradores y generadores](/visualstudio/scripting-docs/javascript/advanced/iterators-and-generators-javascript). **Nota:**  Todavía no se admiten generadores.|
|Funciones de flecha|La función de flecha (=>) proporciona la sintaxis abreviada para la palabra clave `function` que incluye un enlace léxico `this`.|
|Nuevos métodos para objetos integrados|Los objetos integrados [Array (Objeto)](/visualstudio/scripting-docs/javascript/reference/array-object-javascript), [Math (Objeto)](/visualstudio/scripting-docs/javascript/reference/math-object-javascript), [Number (Objeto)](/visualstudio/scripting-docs/javascript/reference/number-object-javascript), [Object (Objeto)](/visualstudio/scripting-docs/javascript/reference/object-object-javascript) y [String (Objeto)](/visualstudio/scripting-docs/javascript/reference/string-object-javascript) incluyen numerosas propiedades y funciones de utilidad nuevas para manipular e inspeccionar datos.|
|Mejoras literales de objeto|Los objetos ahora admiten propiedades calculadas, definiciones de método concisas y sintaxis abreviada para las propiedades cuyo valor se inicializa en una variable con el mismo nombre. Para obtener más información, vea [Crear objetos](/visualstudio/scripting-docs/javascript/creating-objects-javascript).|
|Servidores proxy|Los [servidores proxy](/visualstudio/scripting-docs/javascript/reference/proxy-object-javascript) permiten un comportamiento personalizado para los objetos.|
|Parámetros de REST|Los parámetros de REST permiten activar argumentos consecutivos en una llamada de función a una matriz. Para obtener más información, vea [Funciones](/visualstudio/scripting-docs/javascript/functions-javascript).|
|Operador de propagación|El [operador de propagación](/visualstudio/scripting-docs/javascript/reference/spread-operator-decrement-dot-dot-dot-javascript) (`…`) expande expresiones iterables en argumentos individuales. Por ejemplo, `a.b(…array)` es aproximadamente igual a que `a.b.apply(a, array)`.|
|Símbolos|Los objetos [Símbolo](/visualstudio/scripting-docs/javascript/reference/symbol-object-javascript) permiten agregar propiedades a los objetos existentes sin posibilidad de interferencias con las propiedades de objeto existentes, sin visibilidad no intencionada y sin otras adiciones no coordinadas por parte de otro código.|
|Cadenas de plantillas|Las [cadenas de plantillas](/visualstudio/scripting-docs/javascript/advanced/template-strings-javascript) son literales de cadena que permiten evaluar y concatenar las expresiones con el literal de cadena.|
|Mejoras de Unicode|Se realizaron mejoras en la compatibilidad con Unicode. Por ejemplo, un nuevo formato de secuencia de escape admite puntos de código astral (puntos de código con más de cuatro dígitos hexadecimales). Para obtener más información, consulte [Caracteres especiales](/visualstudio/scripting-docs/javascript/advanced/special-characters-javascript).|
|WeakSet|Un [WeakSet](/visualstudio/scripting-docs/javascript/reference/weakset-object-javascript) es una colección de objetos que se pueden recoger si no se hace referencia a ellos en ningún otro lugar.|
