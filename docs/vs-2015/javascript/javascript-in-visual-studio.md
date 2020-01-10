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
ms.openlocfilehash: 778912c3149f9f146c01dbab15afa4fabeaa49b8
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852259"
---
# <a name="javascript-in-visual-studio"></a>JavaScript en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript es un lenguaje de primera clase en Visual Studio. Puede usar la mayoría de las ayudas de edición estándar (fragmentos de código, IntelliSense, etc.) al escribir código JavaScript en el IDE de Visual Studio. Puede escribir código JavaScript para muchos tipos de aplicaciones y servicios.

 Para obtener documentación de referencia del lenguaje JavaScript, consulte el tema sobre [JavaScript](https://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).

 Es posible que haya versiones o extensiones específicas de Visual Studio que requieran el desarrollo de ciertos tipos de aplicaciones y servicios con HTML y JavaScript. La lista siguiente contiene vínculos para obtener más información.

- Para crear aplicaciones multiplataforma con Apache Cordova, [obtenga Visual Studio Tools para Apache Cordova](https://taco.visualstudio.com/docs/install-vs-tools-apache-cordova/).

- Para crear aplicaciones de la [Tienda Windows](https://developer.microsoft.com/), [Windows Phone](https://developer.microsoft.com/) y universales (compatibles con ambas plataformas), [obtenga las herramientas](https://developer.microsoft.com/windows/downloads).

- Para crear servicios basados en la nube, visite el [sitio de Microsoft Azure](https://azure.microsoft.com/documentation/).

- Para crear sitios web y aplicaciones web, [visite el sitio ASP.NET](https://dotnet.microsoft.com/apps/aspnet/web-apps).

  > [!NOTE]
  > Puede crear un sitio web ASP.Net vacío y usarlo para la programación con HTML, CSS y JavaScript. El archivo Webconfig proporcionado por ASP.NET habilita la depuración en Visual Studio (o puede usar herramientas de F12 al ejecutar la aplicación).

  El editor de JavaScript en Visual Studio proporciona compatibilidad con IntelliSense. Para obtener más información, vea [IntelliSense de JavaScript](../ide/javascript-intellisense.md).

## <a name="whats-new-in-javascript"></a>Novedades de JavaScript
 En la tabla siguiente se enumeran las nuevas características para JavaScript.

|Característica|Descripción|
|-------------|-----------------|
|Clases|La nueva sintaxis admite la declaración de [clases](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/class).|
|Promises|[Promises](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) permite una codificación asincrónica más fácil y limpia. Se admiten constructores Promise junto con los métodos de utilidad `all` y `race`.|
|Iterators|Ahora puede iterar por objetos iterables (incluidas matrices, objetos similares a matrices e iteradores), invocando un enlace de iteración personalizado con instrucciones que se ejecutarán para el valor de cada propiedad distintiva. Para más información, vea [Iteradores y generadores](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Iterators_and_Generators). **Nota:** Todavía no se admiten generadores.|
|Funciones de flecha|La función de flecha (=>) proporciona la sintaxis abreviada para la palabra clave `function` que incluye un enlace léxico `this`.|
|Nuevos métodos para objetos integrados|Los objetos integrados [Array (Objeto)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array), [Math (Objeto)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Math), [Number (Objeto)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number), [Object (Objeto)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object) y [String (Objeto)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String) incluyen numerosas propiedades y funciones de utilidad nuevas para manipular e inspeccionar datos.|
|Mejoras literales de objeto|Los objetos ahora admiten propiedades calculadas, definiciones de método concisas y sintaxis abreviada para las propiedades cuyo valor se inicializa en una variable con el mismo nombre. Para obtener más información, vea [Crear objetos](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object).|
|Servidores proxy|Los [servidores proxy](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Proxy) permiten un comportamiento personalizado para los objetos.|
|Parámetros de REST|Los parámetros de REST permiten activar argumentos consecutivos en una llamada de función a una matriz. Para obtener más información, vea [Funciones](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function).|
|Operador de propagación|El [operador de propagación](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Spread_operator) (`…`) expande expresiones iterables en argumentos individuales. Por ejemplo, `a.b(…array)` es aproximadamente igual a que `a.b.apply(a, array)`.|
|Símbolos|Los objetos [Símbolo](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Symbol) permiten agregar propiedades a los objetos existentes sin posibilidad de interferencias con las propiedades de objeto existentes, sin visibilidad no intencionada y sin otras adiciones no coordinadas por parte de otro código.|
|Cadenas de plantillas|Las [cadenas de plantillas](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Template_literals) son literales de cadena que permiten evaluar y concatenar las expresiones con el literal de cadena.|
|Mejoras de Unicode|Se realizaron mejoras en la compatibilidad con Unicode. Por ejemplo, un nuevo formato de secuencia de escape admite puntos de código astral (puntos de código con más de cuatro dígitos hexadecimales). Para obtener más información, consulte [Caracteres especiales](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Regular_Expressions#Types_of_special_characters).|
|WeakSet|Un [WeakSet](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/WeakSet) es una colección de objetos que se pueden recoger si no se hace referencia a ellos en ningún otro lugar.|
