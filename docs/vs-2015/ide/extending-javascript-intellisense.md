---
title: Extender IntelliSense para JavaScript | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript, intellisense object
- extending JavaScript IntelliSense
- customizing JavaScript IntelliSense
- JavaScript, extending IntelliSense
- IntelliSense [JavaScript], extending
ms.assetid: 004e1ab6-bd7a-4327-9e01-89b9be96ba2f
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2bee6a4f6cfdcdd53583fae858186ee8cc1da7ba
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576639"
---
# <a name="extending-javascript-intellisense"></a>Extender IntelliSense para JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [documentación de Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
La característica de extensibilidad de IntelliSense para JavaScript le permite personalizar los resultados de IntelliSense en el editor de JavaScript para bibliotecas de terceros. Esto puede mejorar la experiencia de los desarrolladores que usan estas bibliotecas.  
  
 JavaScript language service proporciona las características de IntelliSense para las bibliotecas de JavaScript de terceros que se agregan a un proyecto. Para la mayoría de las bibliotecas, la finalización de instrucciones se proporciona automáticamente por el servicio de lenguaje. La siguiente ilustración muestra un ejemplo de finalización de instrucciones:  
  
 ![Ejemplo de finalización de instrucciones](../ide/media/js-intellisense-completion.png "js_intellisense_completion")  
  
 Si la biblioteca incluye descripciones de las variables, funciones y objetos en las etiquetas de comentario de JavaScript estándar (/ /), podrá aprovechar automáticamente, de forma predeterminada, de las características de extensibilidad de IntelliSense, que proporcionan información descriptiva en un cuadro emergente que aparece a la derecha de los elementos en una lista de finalización, o al escribir el paréntesis de apertura en una llamada de función. Los comentarios en el cuadro emergente contienen la descripción del miembro. El ejemplo siguiente muestra el cuadro emergente para obtener una lista de finalización.  
  
 ![Ejemplo de un punto de presencia de información rápida&#45;cuadro](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")  
  
 Para mejorar aún más la experiencia del desarrollador, puede proporcionar información de tipos a los desarrolladores en el cuadro emergente. Puede proporcionar información de tipos mediante JavaScript [comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md) en lugar de etiquetas de comentario estándar. Agregar comentarios de documentación XML mediante el uso de etiquetas de comentario de triple barra diagonal (/ / /) y un conjunto definido de elementos XML.  
  
 Como alternativa, puede proporcionar información de tipos mediante el uso de extensibilidad de IntelliSense para JavaScript. Esta característica le permite personalizar los resultados de IntelliSense al crear extensiones de JavaScript y agregarlos al contexto del script. En la extensión, que es un archivo de JavaScript, se suscribe a eventos que exponen el `intellisense` objeto del servicio de lenguaje. Extensibilidad de IntelliSense para JavaScript es la solución preferida para las bibliotecas de si un patrón de comportamiento en la biblioteca impide que el servicio de lenguaje JavaScript que proporciona el nivel deseado de la compatibilidad con IntelliSense y una alternativa a XML declarativo Comentarios de documentación también es necesario. Al personalizar los resultados de IntelliSense, puede crear una experiencia de primera clase IntelliSense, independientemente de los patrones de comportamiento que podría restringir las capacidades de predeterminada del servicio de lenguaje. Para obtener más información, consulte [finalización de instrucciones para identificadores](../ide/statement-completion-for-identifiers.md).  
  
## <a name="adding-an-extension-to-the-script-context"></a>Agregar una extensión para el contexto de Script  
 Para que una extensión de IntelliSense que se ejecutará, debe agregarse al contexto de script actual. La extensión se puede agregar automáticamente al contexto del script mediante el mecanismo de detección automática, o puede agregar la extensión en el contexto de secuencia de comandos manualmente mediante el uso de grupos de referencia o la directiva de referencia.  
  
 El mecanismo de detección automática permite que el servicio de lenguaje para que busque automáticamente las extensiones que siguen la convención de nomenclatura de archivos *nombrebiblioteca*. intellisense.js y que se encuentran en el mismo directorio que la biblioteca de que se aplica la extensión. Por ejemplo, una extensión válida para la biblioteca de jQuery sería jQuery.intellisense.js. Para las extensiones de jQuery más restrictivas, puede usar los nombres de archivo, como jQuery-1.7.1.intellisense.js (una extensión específica de la versión) o jQuery.ui.intellisense.js (una extensión para una biblioteca de jQuery con ámbito). Si se encuentra más de una extensión para una determinada biblioteca, se utiliza la versión más restrictiva de la extensión.  
  
 Si desea usar la extensión para todos los archivos de proyecto de JavaScript, en su lugar, puede agregar la extensión a un grupo de referencias. Hay varios tipos de grupos de referencia, ya sean los que incluyen referencias implícitas y las que incluyen referencias de trabajo dedicado. Para agregar una extensión, deberá agregar el archivo como un grupo de referencia implícita, ya sea normalmente **implícita (Windows)**, **implícito (Web)**. Referencias implícitas se encuentran en el ámbito de cada archivo .js abierto en el Editor de código. Cuando se usa este método, deberá agregar la extensión y el archivo que está complementando la extensión.  
  
 Use la **IntelliSense** página de la **opciones** cuadro de diálogo para agregar una extensión como un grupo de referencias. Puede tener acceso a la **IntelliSense** página eligiendo **herramientas**, **opciones** en la barra de menús y, después, elige **Editor de texto**, **JavaScript**, **IntelliSense**, **referencias**. Para obtener más información acerca de los grupos de referencia, consulte [IntelliSense para JavaScript](../ide/javascript-intellisense.md) y [opciones, Editor de texto, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).  
  
 Si desea usar la extensión para un conjunto específico de archivos, utilice una directiva de referencia. Cuando se usa este método, deberá hacer referencia a la extensión y el archivo que es complementar la extensión. Para obtener información sobre el uso de la directiva de referencia, vea [IntelliSense para JavaScript](../ide/javascript-intellisense.md).  
  
## <a name="handling-intellisense-events"></a>Control de eventos de IntelliSense  
 La característica de extensibilidad permite personalizar los resultados de IntelliSense al suscribirse a eventos, como el `statementcompletion` eventos del servicio de lenguaje `intellisense` objeto. El ejemplo siguiente muestra una extensión sencilla que utiliza el servicio de lenguaje para ocultar a los miembros que comienzan con un carácter de subrayado de finalización de instrucciones. Este código se encuentra en underscorefilter.js y se encuentra en la \\ \\ *ruta de instalación de Visual Studio*\JavaScript\References carpeta.  
  
```javascript  
intellisense.addEventListener('statementcompletion', function (event) {  
    if (event.targetName === "this") return;  
  
    var filterRegex;  
  
    if (event.target === undefined || event.target === window)  
        filterRegex = /^_.*\d{2,}/;  
    else  
        filterRegex = /^_.*/;  
  
    event.items = event.items.filter(function (item) {  
        return !filterRegex.test(item.name);  
    });  
});  
```  
  
 En el código anterior, la extensión comprueba el [propiedad targetName](#TargetName) y [propiedad de destino](#Target) propiedades de la `statementcompletion` objeto event para excluir objetos como `this` y `window`y para asegurarse de que se puede identificar una lista de finalización de instrucciones válido. Si se puede identificar una lista de finalización, la extensión de las actualizaciones de la finalización de instrucciones [propiedad items](#Items) colección mediante el filtrado de miembros que comienzan con un carácter de subrayado.  
  
 Para obtener ejemplos adicionales, busque en el \\ \\ *ruta de instalación de Visual Studio*\JavaScript\References carpeta. El archivo showPlainComments.js en esta carpeta proporciona ejemplos del uso de otros eventos para proporcionar compatibilidad con IntelliSense de forma predeterminada para las etiquetas de comentario de JavaScript estándar (/ /). Al igual que underscorefilter.js, showPlainComments.js ya está disponible como una extensión de trabajo y, puede ver la información de IntelliSense resultante al usar etiquetas de comentario en el código para las variables, funciones y objetos. Para obtener ejemplos adicionales, consulte [ejemplos de código](#CodeExamples).  
  
> [!WARNING]
>  Si modifica los archivos de extensión incluidos con Visual Studio, puede deshabilitar IntelliSense para JavaScript o la característica admitida por la extensión.  
  
 En el código de extensión, puede crear controladores para los siguientes tipos de eventos mediante `addEventListener`:  
  
-   `statementcompletion`, que agrega un controlador para un evento de finalización de instrucción. Finalización de instrucciones que proporciona una lista de miembros para un tipo concreto que aparece después de escribir un carácter especial como un punto (.) o una lista de identificadores que aparece mientras se escribe o al presionar CTRL + J. El controlador recibe un objeto de evento de tipo `CompletionEvent`, que es compatible con los siguientes miembros: [propiedad items](#Items), [propiedad de destino](#Target), [propiedad targetName](#TargetName), y [definir el ámbito de propiedad](#Scope).  
  
-   `signaturehelp`, que agrega un controlador para la información de parámetros de IntelliSense. Información de parámetros proporciona información sobre el número, los nombres y tipos de parámetros requeridos por una función. El controlador recibe un objeto de evento de tipo `SignatureHelpEvent`, que es compatible con los siguientes miembros: [propiedad de destino](#Target), [parentObject propiedad](#ParentObject), [functionComments propiedad](#FunctionComments), [functionHelp propiedad](#FunctionHelp).  
  
-   `statementcompletionhint`, que agrega un controlador de información rápida de IntelliSense. El cuadro emergente de información rápida muestra la declaración completa de identificadores en el código. El controlador recibe un objeto de evento de tipo `CompletionHintEvent`, que es compatible con los siguientes miembros: [completionItem propiedad](#CompletionItem), y [symbolHelp propiedad](#SymbolHelp).  
  
 Para obtener ejemplos que muestran las características de IntelliSense como información rápida, información de parámetros y la finalización de instrucciones, consulte [Using IntelliSense](../ide/using-intellisense.md).  
  
> [!NOTE]
>  En JavaScript, información rápida hace referencia en el cuadro emergente que aparece a la derecha de una lista de finalización. No se puede invocar manualmente la información rápida.  
  
##  <a name="intellisenseObject"></a> Objeto de IntelliSense  
 En la tabla siguiente se muestra las funciones que están disponibles para el `intellisense` objeto. La `intellisense` objeto está disponible solo en tiempo de diseño.  
  
|Función|Descripción|  
|--------------|-----------------|  
|`addEventListener(type, handler);`|Agrega un controlador de eventos para un evento de IntelliSense.<br /><br /> `type` es un valor de cadena. Los valores válidos incluyen `statementcompletion`, `signaturehelp`, y `statementcompletionhint`.<br /><br /> `handler` es una función de controlador de eventos que recibe un objeto de evento de uno de los siguientes tipos:<br /><br /> -   `CompletionEvent`, utilizado para la `statementcompletion` eventos.<br />-   `SignatureHelpEvent`, utilizado para la `signaturehelp` eventos.<br />-   `CompletionHintEvent`, utilizado para la `statementcompletionhint` eventos.<br /><br /> Para obtener ejemplos que utilizan esta función, vea [ejemplos de código](#CodeExamples).|  
|`annotate(obj, doc);`|Especifica la documentación para un objeto mediante la copia de los comentarios de documentación de un objeto a otro objeto.<br /><br /> `obj` Especifica el objeto que se va a copiar la documentación.<br /><br /> `doc` Especifica el objeto desde el que se va a copiar la documentación.<br /><br /> Para obtener un ejemplo que muestra cómo usar esta función, vea [agregar anotaciones de IntelliSense](#Annotations).|  
|`getFunctionComments(func);`|Devuelve los comentarios de una función especificada.<br /><br /> `func` Especifica la función para el que se devuelven los comentarios.<br /><br /> Puede establecer el `func` parámetro mediante el uso de `completionItem.value`.<br /><br /> El valor devuelto `functionComments` objeto incluye los siguientes miembros: `above`, `inside`, y `paramComment`. Para obtener más información, consulte el [functionComments propiedad](#FunctionComments) propiedad.<br /><br /> `getFunctionComments` se puede llamar solo desde dentro de uno de los controladores de eventos registrados por `addEventListener`.<br /><br /> Para obtener un ejemplo que muestra cómo usar esta función, vea \\ \\ *ruta de instalación de Visual Studio*\JavaScript\References\showPlainComments.js.|  
|`logMessage(msg);`|Envía mensajes de diagnóstico a la ventana de salida.<br /><br /> `msg` es una cadena que contiene el mensaje.<br /><br /> Para obtener un ejemplo que muestra cómo usar esta función, vea [enviar mensajes a la ventana de salida](#Logging).|  
|`nullWithCompletionsOf(value);`|Devuelve un valor nulo especial para el que la lista de finalización viene determinada por el objeto pasado en el `value` parámetro.<br /><br /> `value` Determina la lista de finalización para el valor devuelto. `value` puede ser cualquier tipo.<br /><br /> El valor devuelto nulo se trata como null en tiempo de diseño, pero la lista de finalización para el valor devuelto es igual a la lista de finalización para el `value` parámetro.<br /><br /> Un uso de esta función es para proporcionar IntelliSense para un valor devuelto cuando el tipo de valor devuelto es predecible en tiempo de ejecución, pero el valor devuelto es `null` en tiempo de diseño.|  
|`redirectDefinition(func, definition);`|Indica a IntelliSense para usar la función de la información proporcionada en lugar de la función func original cuando la Ayuda del parámetro o **ir a definición** se solicita.<br /><br /> `func` Especifica la función de destino.<br /><br /> `definition` Especifica la función que se usará en lugar de la función de destino para la información de parámetros y **ir a definición**.|  
|`setCallContext(func, thisArg);`|Establece el contexto de llamada o ámbito, para la función especificada.<br /><br /> `func` Especifica la función que se va a establecer el ámbito.<br /><br /> `thisArg` es un objeto literal a la que el `this` palabra clave puede hacer referencia a, que especifica el nuevo ámbito para el miembro. Puede incluir los argumentos para pasar este parámetro, por ejemplo, `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` Proporciona un comportamiento similar a `Function.prototype.bind`, excepto en que utiliza sólo para compatibilidad con IntelliSense de tiempo de diseño. Puede usar `setCallContext` para establecer el ámbito de función si tiene que simular una llamada a código no accesible en caso contrario, para que cuando se llama a la función, la llamada de función incluirá los argumentos y el ámbito correcto.|  
|`undefinedWithCompletionsOf(value);`|Devuelve un valor indefinido especial para el que la lista de finalización viene determinada por el objeto pasado en el `value` parámetro.<br /><br /> `value` Determina la lista de finalización para el valor devuelto. `value` puede ser cualquier tipo.<br /><br /> Devolver el undefined lo trata como indefinido en tiempo de diseño, pero la finalización lista para el valor devuelto es el mismo que la lista de finalización para el `value` parámetro.<br /><br /> Un uso de esta función consiste en proporcionar IntelliSense para un valor devuelto cuando el tipo de valor devuelto es predecible en tiempo de ejecución, pero el valor devuelto es indefinido en tiempo de diseño.|  
|`version()`|Devuelve la versión de Visual Studio.|  
  
## <a name="event-members"></a>Miembros de evento  
 Las secciones siguientes describen los miembros que se exponen en el objeto de evento para los siguientes eventos: `statementcompletion`, `signaturehelp`, y `statementcompletionhint`.  
  
###  <a name="CompletionItem"></a> Propiedad completionItem  
 Devuelve el identificador, conocido como el elemento de finalización para el que se solicita un cuadro emergente de información rápida. Esta propiedad está disponible para el `statementcompletionhint` objeto de evento y para el [propiedad items](#Items) propiedad de la `statementcompletion` objeto de evento.  
  
 Valor devuelto: `completionItem` objeto  
  
 A continuación es los miembros de la `completionItem` objeto:  
  
-   `name`. Lectura y escritura cuando se utiliza en el `items` colección; en caso contrario, solo lectura. Devuelve una cadena que identifica el elemento de finalización.  
  
-   `kind`. Lectura y escritura cuando se utiliza en el `items` colección; en caso contrario, solo lectura. Devuelve una cadena que representa el tipo de elemento de finalización. Los valores posibles son el método, campo, propiedad, parámetro, variable y reserva.  
  
-   `glyph`. Lectura y escritura cuando se utiliza en el `items` colección; en caso contrario, solo lectura. Devuelve una cadena que representa un icono que se muestra en la lista de finalización. Los valores posibles de `glyph` utilice el siguiente formato: vs:*glyphType*, donde *glyphType* corresponde a los miembros de independiente del lenguaje en el <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> enumeración. Por ejemplo, `vs:GlyphGroupMethod` es un valor posible para `glyph`. Cuando `glyph` no se establece, el `kind` propiedad determina el icono predeterminado.  
  
-   `parentObject`. Sólo lectura. Devuelve el objeto primario.  
  
-   `value`. Sólo lectura. Devuelve un objeto que representa el valor del elemento de finalización.  
  
-   `comments`. Sólo lectura. Devuelve una cadena que contiene los comentarios que están por encima del campo o variable.  
  
-   `scope`. Sólo lectura. Devuelve el ámbito del elemento de finalización. Los valores posibles son globales y locales, parámetros y miembros.  
  
###  <a name="Items"></a> Propiedad Items  
 Obtiene o establece los elementos de finalización de la matriz de instrucción. Cada elemento de la matriz es un [completionItem propiedad](#CompletionItem) objeto. El `items` propiedad está disponible para el `statementcompletion` objeto de evento.  
  
 Valor devuelto: matriz  
  
###  <a name="FunctionComments"></a> Propiedad functionComments  
 Devuelve los comentarios de la función. Esta propiedad está disponible para el `signaturehelp` objeto de evento.  
  
 Valor devuelto: `comments` objeto  
  
 A continuación es los miembros de la `comments` objeto:  
  
-   `above`. Devuelve los comentarios antes de la función.  
  
-   `inside`. Devuelve los comentarios dentro de la función, normalmente en formato VSDoc.  
  
-   `paramComments`. Devuelve una matriz que representa comentarios para cada parámetro de la función. Los miembros de la matriz se incluyen:  
  
    -   `name`. Devuelve una cadena que representa el nombre del parámetro.  
  
    -   `comment`. Devuelve una cadena que contiene el parámetro de comentario.  
  
###  <a name="FunctionHelp"></a> Propiedad functionHelp  
 Devuelve la Ayuda de la función. Esta propiedad está disponible para el `signaturehelp` objeto de evento.  
  
 Valor devuelto: `functionHelp` objeto  
  
 A continuación es los miembros de la `functionHelp` objeto:  
  
-   `functionName`. Lectura y escritura. Devuelve una cadena que contiene el nombre de función.  
  
-   `signatures`. Lectura y escritura. Obtiene o establece la matriz de firmas de función. Cada elemento de la matriz es un `signature` objeto. Algunos `signature` propiedades, como `locid`, corresponden a común [comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md) atributos.  
  
     Los miembros de la `signature` objeto incluyen:  
  
    -   `description`. Lectura y escritura. Devuelve una cadena que describe la función.  
  
    -   `locid`. Lectura y escritura. Devuelve un identificador de cadena que contiene información de localización sobre la función.  
  
    -   `helpKeyword`. Lectura y escritura. Devuelve una cadena que contiene la palabra clave de ayuda.  
  
    -   `externalFile`. Lectura y escritura. Devuelve una cadena que representa el archivo que contiene el identificador del miembro.  
  
    -   `externalid`. Lectura y escritura. Devuelve una cadena que representa el identificador de miembro de la función.  
  
    -   `params`. Lectura y escritura. Obtiene o establece la matriz de parámetros para la función. Cada elemento de la matriz de parámetros es un `parameter` objeto que tiene propiedades que corresponden a los siguientes atributos de la [ \<param >](../ide/param-javascript.md) elemento:  
  
        -   `name`. Lectura y escritura. Devuelve una cadena que representa el nombre del parámetro.  
  
        -   `type`. Lectura y escritura. Devuelve una cadena que representa el tipo de parámetro.  
  
        -   `elementType`. Lectura y escritura. Si el tipo es `Array`, devuelve una cadena que representa el tipo de los elementos de la matriz.  
  
        -   `description`. Lectura y escritura. Devuelve una cadena que describe el parámetro.  
  
        -   `locid`. Lectura y escritura. Devuelve un identificador de cadena que contiene información de localización sobre la función.  
  
        -   `optional`. Lectura y escritura. Devuelve una cadena que indica si el parámetro es opcional. `true` indica que el parámetro es opcional; `false` indica que no lo está.  
  
    -   `returnValue`. Lectura y escritura. Obtiene o establece un objeto de valor devuelto con propiedades que corresponden a los siguientes atributos de la [ \<devuelve >](../ide/returns-javascript.md) elemento:  
  
        -   `type`. Lectura y escritura. Devuelve una cadena que representa el tipo de valor devuelto.  
  
        -   `elementType`. Lectura y escritura. Si el tipo es `Array`, devuelve una cadena que representa el tipo de los elementos de la matriz.  
  
        -   `description`. Lectura y escritura. Devuelve una cadena que describe el valor devuelto.  
  
        -   `locid`. Lectura y escritura. Devuelve un identificador de cadena que contiene información de localización sobre la función.  
  
        -   `helpKeyword`. Lectura y escritura. Devuelve una cadena que contiene la palabra clave de ayuda.  
  
        -   `externalFile`. Lectura y escritura. Devuelve una cadena que representa el archivo que contiene el identificador del miembro.  
  
        -   `externalid`. Lectura y escritura. Devuelve una cadena que representa el identificador de miembro de la función.  
  
###  <a name="ParentObject"></a> parentObject, propiedad  
 Devuelve el objeto primario de una función miembro. Por ejemplo, para `document.getElementByID`, `parentObject` devuelve el `document` objeto. Esta propiedad está disponible para el `signaturehelp` objeto de evento.  
  
 Valor devuelto: objeto  
  
###  <a name="Target"></a> Propiedad de destino  
 Devuelve un objeto que representa el elemento a la izquierda del carácter desencadenador, que es un punto (.). Para las funciones, `target` devuelve la función que se solicita información de parámetros. Esta propiedad está disponible para el `statementcompletion` y `signaturehelp` objetos de evento.  
  
 Valor devuelto: objeto  
  
###  <a name="TargetName"></a> Propiedad targetName  
 Devuelve una cadena que representa el destino. Por ejemplo, para "this.", `targetName` devuelve "this". Para "A.B" (cuando el cursor está después de la "B"), `targetName` devuelve "B". Esta propiedad está disponible para el `statementcompletion` objeto de evento.  
  
 Valor devuelto: cadena  
  
###  <a name="SymbolHelp"></a> Propiedad symbolHelp  
 Devuelve el elemento de finalización para el que se solicita un cuadro emergente de información rápida. Esta propiedad está disponible para el `statementcompletionhint` objeto de evento.  
  
 Valor devuelto: `symbolHelp` objeto.  
  
 Algunas propiedades de la `symbolHelp` objetos, como `locid`, corresponden a común [comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md) atributos.  
  
 A continuación es los miembros de la `symbolHelp` objeto:  
  
-   `name`. Lectura y escritura. Devuelve una cadena que contiene el nombre del identificador.  
  
-   `symbolType`. Lectura y escritura. Devuelve una cadena que representa el tipo de símbolo. Los valores posibles incluyen desconocido, booleano, número, cadena, objeto, función, matriz, fecha y Regex.  
  
-   `symbolDisplayType`. Lectura y escritura. Devuelve una cadena que contiene el nombre de tipo para mostrar. Si `symbolDisplayType` no está configurado, `symbolType` se utiliza.  
  
-   `elementType`. Lectura y escritura. Si el `symbolType` es `Array`, devuelve una cadena que representa el tipo de los elementos de la matriz.  
  
-   `scope`. Lectura y escritura. Devuelve una cadena que representa el ámbito del símbolo. Los valores posibles incluyen globales y locales, parámetros y miembros.  
  
-   `description`. Lectura y escritura. Devuelve una cadena que contiene una descripción del símbolo.  
  
-   `locid`. Lectura y escritura. Devuelve un identificador de cadena que contiene información de localización sobre el símbolo.  
  
-   `helpKeyword`. Lectura y escritura. Devuelve una cadena que contiene la palabra clave de ayuda.  
  
-   `externalFile`. Lectura y escritura. Devuelve una cadena que representa el archivo que contiene el identificador del miembro.  
  
-   `externalid`. Lectura y escritura. Devuelve una cadena que representa el identificador de miembro del símbolo.  
  
-   `functionHelp`. Lectura y escritura. Devuelve un [functionHelp propiedad](#FunctionHelp), que pueden contener información cuando el `symbolType` es la función.  
  
###  <a name="Scope"></a> definir el ámbito de propiedad  
 Devuelve el ámbito de la finalización del evento. Los valores posibles para la finalización de ámbito son global y los miembros. Esta propiedad está disponible para el `statementcompletion` objeto de evento.  
  
 Valor devuelto: cadena  
  
## <a name="debugging-intellisense-extensions"></a>Depurar extensiones de IntelliSense  
 No se puede depurar las extensiones, pero puede usar el [intellisense objeto ](#intellisenseObject) /función para enviar información a la ventana de salida de Visual Studio. Para obtener un ejemplo que muestra cómo usar esta función, vea [enviar mensajes a la ventana de salida](#Logging) más adelante en este tema. Para `logMessage` para trabajar, al menos un controlador de eventos debe estar registrado en una extensión.  
  
##  <a name="CodeExamples"></a> Ejemplos de código  
 Esta sección incluye ejemplos de código que muestran cómo usar las API de extensibilidad de IntelliSense. También hay otras formas de usar estas API. Para obtener ejemplos adicionales, consulte los siguientes archivos en el \\ \\ *ruta de instalación de Visual Studio*\JavaScript\References carpeta. Estos están trabajando los ejemplos usados por el servicio de lenguaje JavaScript.  
  
-   underscoreFilter.js. Este código oculta los miembros privados de IntelliSense. Incluye los controladores de eventos para el `statementcompletion` eventos.  
  
-   showPlainComments.js. Este código proporciona compatibilidad con IntelliSense para comentarios estándar. Incluye los controladores de eventos para el `signaturehelp` y `statementcompletionhint` eventos.  
  
###  <a name="Annotations"></a> Agregar anotaciones de IntelliSense  
 El procedimiento siguiente muestra cómo proporcionar soporte técnico de documentación de IntelliSense para una biblioteca de terceros sin modificar directamente la biblioteca. Para ello, puede usar `intellisense.annotate` en una extensión.  
  
 Para que este ejemplo funcione, necesita los siguientes archivos JavaScript en el proyecto:  
  
-   demoLib.js, que es un archivo de proyecto que representa una biblioteca de terceros.  
  
-   demoLib.intellisense.js, que es la extensión de IntelliSense. No es necesario incluir este archivo en el proyecto, pero debe estar en la misma carpeta que exampleLib.js.  
  
-   appCode.js, que es un archivo de proyecto que representa código de aplicación.  
  
##### <a name="to-add-an-intellisense-annotation"></a>Para agregar una anotación de IntelliSense  
  
1.  Agregue el código siguiente a demoLib.js.  
  
    ```javascript  
    function someFunc(a) { };  
    var rectangle;  
  
    ```  
  
2.  Agregue el código siguiente a demoLib.intellisense.js.  
  
    ```javascript  
    intellisense.annotate(someFunc, function (a) {  
        /// <signature>  
        /// <summary>Description of someFunc</summary>  
        /// <param name="a">Param a</param>  
        /// </signature>  
    });  
  
    intellisense.annotate(window, {  
        // This is a comment on a global variable named rectangle.  
        rectangle: undefined  
    });  
    ```  
  
3.  Agregue la directiva reference siguiente como la primera línea de appCode.js. La ruta de acceso usada aquí indica que los archivos JavaScript están en la misma carpeta.  
  
    ```javascript  
    /// <reference path="demoLib.js" />  
  
    ```  
  
4.  En appCode.js, escriba el código siguiente. Podrá ver los comentarios de documentación XML en la extensión aparece como información de parámetros de IntelliSense.  
  
     ![Ejemplo que muestra el uso de intellisense.annotate](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")  
  
5.  En appCode.js, escriba el código siguiente. Mientras escribe, podrá ver los comentarios estándares de la extensión aparece como información rápida de IntelliSense.  
  
     ![Ejemplo que muestra el uso de intellisense.annotate](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")  
  
###  <a name="Logging"></a> Envío de mensajes a la ventana de salida  
 El siguiente procedimiento muestra cómo enviar mensajes a la ventana de salida. Puede enviar mensajes para ayudar a depurar las extensiones de IntelliSense.  
  
 Para que este ejemplo funcione, necesita los siguientes archivos JavaScript en el proyecto:  
  
-   exampleLib.js, que es un archivo de proyecto que representa una biblioteca de terceros.  
  
-   exampleLib.intellisense.js, que es la extensión de IntelliSense. No es necesario incluir este archivo en el proyecto, pero debe estar en la misma carpeta que exampleLib.js.  
  
-   appCode.js, que es un archivo de proyecto que representa código de aplicación.  
  
##### <a name="to-send-a-message-to-the-output-window"></a>Para enviar un mensaje a la ventana de salida  
  
1.  Agregue el código siguiente a exampleLib.js.  
  
    ```javascript  
    var someVar = {  
        a: 1,  
        b: 'hello'  
    };  
    ```  
  
2.  Agregue el código siguiente a exampleLib.intellisense.js.  
  
    ```javascript  
    intellisense.addEventListener('statementcompletion', function (e) {  
        // Prints out statement completion info: Either (1) the member   
        // list, if the trigger character was typed, or (2) the   
        // statement completion identifiers.  
        // e.target represents the object left of the trigger character.  
        intellisense.logMessage(  
            e.target ? 'member list requested, target: ' + e.targetName : 'statement completion for current scope requested');  
  
        // Prints out all statement completion items.  
        e.items.forEach(function (item) {  
            intellisense.logMessage('[completion item] ' + item.name + ', kind:' + item.kind + ', scope:' + item.scope + ', value:' + item.value);  
        });  
    });  
    ```  
  
3.  Agregue la directiva reference siguiente como la primera línea de appCode.js. La ruta de acceso usada aquí indica que los archivos JavaScript están en la misma carpeta.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4.  En la ventana de salida, elija **JavaScript Language Service** en el **mostrar resultados desde** lista. (Para ver la ventana de salida, seleccione **salida** en el menú Ver.)  
  
5.  En appCode.js, escriba el código siguiente. Mientras escribe, la ventana de salida muestra los mensajes del servicio de lenguaje. El primer mensaje en la ventana de salida indica que se ha solicitado la finalización de instrucciones para el ámbito actual.  
  
    ```javascript  
    some  
    ```  
  
     Siguiente es una vista parcial de la salida que debe ver.  
  
    ```scr  
    03:16:14.3113: statement completion for current scope requested  
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined  
  
    …  
    ```  
  
6.  Elija la **Borrar todo** botón en la ventana de salida.  
  
7.  Escriba el siguiente código. El primer mensaje en la ventana de salida indica que se ha solicitado una lista de miembros.  
  
    ```javascript  
    someVar.  
    ```  
  
     Siguiente es una vista parcial de la salida, verá:  
  
    ```scr  
    03:17:43.4032: member list requested, target: someVar  
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1  
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello  
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:  
  
    …  
    ```  
  
###  <a name="Icons"></a> Cambiar los iconos de IntelliSense  
 El siguiente procedimiento muestra cómo cambiar los iconos de IntelliSense muestra de forma predeterminada. Esto puede resultar útil al proporcionar IntelliSense información sobre los conceptos específicos de la biblioteca, como los espacios de nombres, clases, interfaces y enumeraciones.  
  
 Para los valores de icono disponibles, vea <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>.  
  
 Para que este ejemplo funcione, necesita los siguientes archivos JavaScript en el proyecto:  
  
-   exampleLib.js, que es un proyecto de archivo de esa biblioteca represens un tercero.  
  
-   exampleLib.intellisense.js, que es la extensión de IntelliSense. No es necesario incluir este archivo en el proyecto, pero debe estar en la misma carpeta que exampleLib.js.  
  
-   appCode.js, que es un archivo de proyecto que representa código de aplicación.  
  
##### <a name="to-change-the-icons"></a>Para cambiar los iconos  
  
1.  Agregue el código siguiente a exampleLib.js.  
  
    ```javascript  
    function Namespace(name) {  
        this._isNamespace = true;  
        window[name] = this;  
    };  
  
    function Enum(values) {  
        var e = Object.create(values);  
        e._isEnum = true;  
        return e;  
    };  
  
    var SomeNamespace = new Namespace('SomeNamespace');  
    // A constructor function is considered a class.  
    SomeNamespace.SomeClass1 = function () { }  
    SomeNamespace.Enum1 = new Enum({ VALUE1: 0, VALUE2: 1 });  
    ```  
  
2.  Agregue el código siguiente a exampleLib.intellisense.js.  
  
    ```javascript  
    intellisense.addEventListener('statementcompletion', function (e) {  
        e.items.forEach(function (item) {  
            // Detect a namespace by using the _isNamespace flag.  
            if (item.value && item.value._isNamespace) {  
                item.glyph = 'vs:GlyphGroupNamespace';  
                }  
  
            if (item.parentObject && item.parentObject._isNamespace) {  
                // The item is a member of a namespace.   
  
                // All constructor functions that are part of a namespace   
                // are considered classes.   
                // A constructor function starts with  
                // an uppercase letter by convention.    
                if (typeof item.value == 'function' && (item.name[0].toUpperCase()   
                    == item.name[0])) {  
                    item.glyph = 'vs:GlyphGroupClass';  
                }  
  
                // Detect an enumeration by using the _isEnum flag.  
                if (item.value && item.value._isEnum) {  
                    item.glyph = 'vs:GlyphGroupEnum';  
                }  
            }  
        });  
    });  
  
    intellisense.addEventListener('statementcompletionhint', function (e) {  
        if (e.completionItem.value) {  
            if (e.completionItem.value._isNamespace) {  
                e.symbolHelp.symbolDisplayType = 'Namespace';  
            }  
            if (e.completionItem.value._isEnum) {  
                e.symbolHelp.symbolDisplayType = 'Enum';  
            }  
        }  
    });  
    ```  
  
3.  Agregue la directiva reference siguiente como la primera línea de appCode.js. La ruta de acceso usada aquí indica que los archivos JavaScript están en la misma carpeta.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4.  En appCode.js, escriba el código siguiente. Mientras escribe, verá que el icono para el espacio de nombres ha cambiado a "{}", tal y como se usa en C#.  
  
     ![Ejemplo que muestra el uso de la propiedad glyph](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")  
  
5.  En appCode.js, escriba el código siguiente. Mientras escribe, verá un nuevo icono de enumeración para el miembro Enum1 y un nuevo icono de clase para el miembro SomeClass1.  
  
     ![Ejemplo que muestra el uso de la propiedad glyph](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")  
  
###  <a name="Overriding"></a> Evitar los efectos de tiempo de ejecución en los resultados de IntelliSense  
 JavaScript language service ejecuta código para proporcionar información de IntelliSense de forma dinámica. Como resultado, el comportamiento de tiempo de ejecución en ocasiones puede interferir con los resultados deseados. El siguiente procedimiento muestra cómo invalidar los resultados de IntelliSense cuando da como resultado un comportamiento en tiempo de ejecución en IntelliSense incorrecto.  
  
 Para que este ejemplo funcione, necesita los siguientes archivos JavaScript en el proyecto:  
  
-   exampleLib.js, que es un archivo de proyecto que representa una biblioteca de terceros.  
  
-   exampleLib.intellisense.js, que es la extensión de IntelliSense. No es necesario incluir este archivo en el proyecto, pero debe estar en la misma carpeta que exampleLib.js.  
  
-   appCode.js, que es un archivo de proyecto que representa código de aplicación.  
  
##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>Para evitar los efectos de tiempo de ejecución en los resultados de IntelliSense  
  
1.  Agregue el código siguiente a exampleLib.js.  
  
    ```javascript  
    function after(count, func) {  
        return function () {  
            if (--times < 1) {  
                return func.apply(this, arguments);  
            }  
        };  
    };  
    ```  
  
     En el código anterior, la función encapsulada omite las llamadas iniciales, en función del valor de `count`y no devuelve resultados.  
  
2.  Agregue la directiva reference siguiente como la primera línea de appCode.js. La ruta de acceso usada aquí indica que los archivos JavaScript están en la misma carpeta.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
3.  En appCode.js, escriba el código siguiente. Aparece la lista de identificador en lugar de IntelliSense porque la función encapsulada nunca se llama, lo que significa que el `throttled` la función no devuelve ningún resultado.  
  
     ![Ejemplo de invalidación de los resultados de intellisense](../ide/media/js-intellisense-override.png "js_intellisense_override")  
  
4.  Agregue el código siguiente a exampleLib.intellisense.js. Esto cambiará el comportamiento en tiempo de diseño para que IntelliSense se muestra en la función ajustada, según lo previsto.  
  
    ```javascript  
    window.after = function (count, func) {  
        // Just return func.   
        return func;  
    };  
    ```  
  
5.  En appCode.js, pruebe los resultados escribiendo el mismo código que ha escrito anteriormente. Esta vez, IntelliSense proporciona la información deseada.  
  
     ![Ejemplo de invalidación de los resultados de IntelliSense](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")  
  
## <a name="see-also"></a>Vea también  
 [IntelliSense para JavaScript](../ide/javascript-intellisense.md)   
 [Finalización de instrucciones para identificadores](../ide/statement-completion-for-identifiers.md)



