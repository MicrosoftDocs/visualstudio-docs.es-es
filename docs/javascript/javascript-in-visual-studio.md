---
title: JavaScript en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 77e7ce26df70e41e2328442454fe78c7a663f1f3
ms.openlocfilehash: de00ef86413571739446b61427c3a8e6c4680c06
ms.lasthandoff: 03/08/2017

---
# <a name="javascript-in-visual-studio"></a>JavaScript en Visual Studio
JavaScript es un lenguaje de primera clase en Visual Studio. Puede usar la mayoría de las ayudas de edición estándar (fragmentos de código, IntelliSense, etc.) al escribir código JavaScript en el IDE de Visual Studio. Puede escribir código JavaScript para muchos tipos de aplicaciones y servicios.  
  
 Para obtener documentación de referencia del lenguaje JavaScript, consulte el tema sobre [JavaScript](https://docs.microsoft.com/scripting/javascript/javascript-language-reference).
  
 Es posible que haya versiones o extensiones específicas de Visual Studio que requieran el desarrollo de ciertos tipos de aplicaciones y servicios con HTML y JavaScript. La lista siguiente contiene vínculos para obtener más información.  
  
-   Para crear aplicaciones multiplataforma con Apache Cordova, vea [Visual Studio Tools para Apache Cordova](https://docs.microsoft.com/visualstudio/cross-platform/tools-for-cordova/).  
  
-   Para obtener vínculos a las tecnologías de JavaScript que puede usar en Visual Studio, vea las páginas [JavaScript](https://docs.microsoft.com/scripting/javascript/) y [Scripting Technologies](https://docs.microsoft.com/scripting/) (Tecnologías de scripting).
  
 El editor de JavaScript en Visual Studio proporciona compatibilidad con IntelliSense. Para obtener más información, vea [IntelliSense de JavaScript](../ide/javascript-intellisense.md).  
  
## <a name="whats-new-in-javascript"></a>Novedades de JavaScript  
 En la tabla siguiente se enumeran las nuevas características para JavaScript.  
  
|Característica|Descripción|  
|-------------|-----------------|  
|Clases|La nueva sintaxis admite la declaración de [clases](http://msdn.microsoft.com/Library/bf45ebad-4678-4062-88df-55d32b603c69).|  
|Promises|[Promises](http://msdn.microsoft.com/Library/358ad98b-f7fa-448c-9ee0-ef1e2a45e9c6) permite una codificación asincrónica más fácil y limpia. Se admiten constructores Promise junto con los métodos de utilidad `all` y `race`.|  
|Iteradores|Ahora puede iterar por objetos iterables (incluidas matrices, objetos similares a matrices e iteradores), invocando un enlace de iteración personalizado con instrucciones que se ejecutarán para el valor de cada propiedad distintiva. Para más información, vea [Iteradores y generadores](http://msdn.microsoft.com/Library/68ef5b2f-0349-492b-b557-73ff2a2f90cf). **Nota:**Todavía no se admiten generadores.|  
|Funciones de flecha|La función de flecha (=>) proporciona la sintaxis abreviada para la palabra clave `function` que incluye un enlace léxico `this`.|  
|Nuevos métodos para objetos integrados|Los objetos integrados [Array (Objeto)](http://msdn.microsoft.com/Library/08e5f552-0797-4b48-8164-609582fc18c9), [Math (Objeto)](http://msdn.microsoft.com/Library/607b94cb-921c-43cd-b514-fdbc13aeced6), [Number (Objeto)](http://msdn.microsoft.com/Library/76e87c37-cf6c-46cc-bafa-04be1fe3d78d), [Object (Objeto)](http://msdn.microsoft.com/Library/d24ef8fc-217b-4828-94e1-19f72780bae0) y [String (Objeto)](http://msdn.microsoft.com/Library/8063ecd5-5778-4e87-b985-b21420171914) incluyen numerosas propiedades y funciones de utilidad nuevas para manipular e inspeccionar datos.|  
|Mejoras literales de objeto|Los objetos ahora admiten propiedades calculadas, definiciones de método concisas y sintaxis abreviada para las propiedades cuyo valor se inicializa en una variable con el mismo nombre. Para obtener más información, vea [Crear objetos](http://msdn.microsoft.com/Library/58d1baa5-4fe8-4a56-a926-5b11765df704).|  
|Servidores proxy|Los [servidores proxy](http://msdn.microsoft.com/Library/2b89abee-04fa-47e6-9676-980016cff5f8) permiten un comportamiento personalizado para los objetos.|  
|Parámetros de REST|Los parámetros de REST permiten activar argumentos consecutivos en una llamada de función a una matriz. Para obtener más información, vea [Funciones](http://msdn.microsoft.com/Library/e2a72b5a-3edd-43d8-95e8-91721b38c1c1).|  
|Operador de propagación|El [operador de propagación](http://msdn.microsoft.com/Library/10263a4c-bd27-4d87-9917-fb4b6bf373db) (`…`) expande expresiones iterables en argumentos individuales. Por ejemplo, `a.b(…array)` es aproximadamente igual a que `a.b.apply(a, array)`.|  
|Símbolos|Los objetos [Símbolo](http://msdn.microsoft.com/Library/2ad059f1-4b7f-4758-882a-c74ce1283ab0) permiten agregar propiedades a los objetos existentes sin posibilidad de interferencias con las propiedades de objeto existentes, sin visibilidad no intencionada y sin otras adiciones no coordinadas por parte de otro código.|  
|Cadenas de plantillas|Las [cadenas de plantillas](http://msdn.microsoft.com/Library/f2e525a5-b0fc-49c3-95a0-641788e5c12a) son literales de cadena que permiten evaluar y concatenar las expresiones con el literal de cadena.|  
|Mejoras de Unicode|Se realizaron mejoras en la compatibilidad con Unicode. Por ejemplo, un nuevo formato de secuencia de escape admite puntos de código astral (puntos de código con más de cuatro dígitos hexadecimales). Para obtener más información, consulte [Caracteres especiales](http://msdn.microsoft.com/Library/3b38b1bd-1f0f-4748-b13e-55cab36fd126).|  
|WeakSet|Un [WeakSet](http://msdn.microsoft.com/Library/f97e6e7c-d678-4e32-978e-d949a7cafa3a) es una colección de objetos que se pueden recoger si no se hace referencia a ellos en ningún otro lugar.|
