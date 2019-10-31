---
title: Extender IntelliSense para JavaScript | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- JavaScript, intellisense object
- extending JavaScript IntelliSense
- customizing JavaScript IntelliSense
- JavaScript, extending IntelliSense
- IntelliSense [JavaScript], extending
ms.assetid: 004e1ab6-bd7a-4327-9e01-89b9be96ba2f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bf16b6fdc307e11875f30cfad6e4bb35580b0b04
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665750"
---
# <a name="extending-javascript-intellisense"></a>Extender IntelliSense para JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La característica de extensibilidad de IntelliSense para JavaScript permite personalizar los resultados de IntelliSense en el editor de JavaScript para bibliotecas de terceros. Esto puede mejorar la experiencia de los desarrolladores que usan estas bibliotecas.

 El servicio del lenguaje JavaScript proporciona características de IntelliSense para las bibliotecas de JavaScript de terceros que se agregan a un proyecto. Para la mayoría de las bibliotecas, el servicio de lenguaje proporciona automáticamente la finalización de instrucciones. En la ilustración siguiente se muestra un ejemplo de finalización de instrucciones:

 ![Ejemplo de finalización de instrucciones](../ide/media/js-intellisense-completion.png "js_intellisense_completion")

 Si la biblioteca incluye descripciones de variables, funciones y objetos en etiquetas de comentario estándar de JavaScript (//), se beneficiará automáticamente, de forma predeterminada, de las características de extensibilidad de IntelliSense, que proporcionan información descriptiva en un cuadro emergente que aparece a la derecha de los elementos de una lista de finalización, o al escribir el paréntesis de apertura en una llamada de función. Los comentarios del cuadro emergente contienen la descripción del miembro. En el ejemplo siguiente se muestra el cuadro emergente para una lista de finalización.

 ![Ejemplo de un cuadro emergente&#45;de información rápida](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")

 Para mejorar aún más la experiencia del desarrollador, es posible que desee proporcionar información de tipo a los desarrolladores en el cuadro emergente. Puede proporcionar información de tipo mediante comentarios de [documentación XML](../ide/xml-documentation-comments-javascript.md) de JavaScript en lugar de etiquetas de comentario estándar. Los comentarios de documentación XML se agregan mediante etiquetas de comentario de barra diagonal triple (///) y un conjunto definido de elementos XML.

 Como alternativa, puede proporcionar información de tipos mediante la extensibilidad de IntelliSense para JavaScript. Esta característica permite personalizar los resultados de IntelliSense mediante la creación de extensiones de JavaScript y su adición al contexto del script. En la extensión, que es un archivo de JavaScript, se suscribe a los eventos que expone el objeto de `intellisense` del servicio de lenguaje. La extensibilidad de IntelliSense para JavaScript es la solución preferida para las bibliotecas si un patrón de comportamiento de la biblioteca impide que el servicio de lenguaje JavaScript proporcione el nivel deseado de compatibilidad con IntelliSense y, si se trata de una alternativa a XML declarativo También se necesitan comentarios de documentación. Mediante la personalización de los resultados de IntelliSense, puede crear una experiencia de IntelliSense de primera clase, independientemente de cualquier patrón de comportamiento que pueda restringir las capacidades predeterminadas del servicio de lenguaje. Para más información, consulte [Finalización de instrucciones para identificadores](../ide/statement-completion-for-identifiers.md).

## <a name="adding-an-extension-to-the-script-context"></a>Agregar una extensión al contexto del script
 Para que se ejecute una extensión de IntelliSense, debe agregarse al contexto de script actual. La extensión se puede Agregar automáticamente al contexto de script mediante el mecanismo de detección automática, o bien puede Agregar la extensión al contexto de script manualmente mediante el uso de grupos de referencia o la Directiva de referencia.

 El mecanismo de detección automática permite al servicio de lenguaje buscar automáticamente las extensiones que siguen la Convención de nomenclatura de archivos *nombrebiblioteca*. IntelliSense. js y que se encuentran en el mismo directorio que la biblioteca en la que se encuentra la extensión. se aplica. Por ejemplo, una extensión válida para la biblioteca de jQuery sería jQuery. IntelliSense. js. Para las extensiones de jQuery más restrictivas, puede usar nombres de archivo como jQuery-1.7.1. IntelliSense. js (una extensión específica de la versión) o jQuery. UI. IntelliSense. js (una extensión para una biblioteca de jQuery con ámbito). Se usa la versión más restrictiva de la extensión si se encuentra más de una extensión para una biblioteca determinada.

 Si desea utilizar la extensión para todos los archivos de proyecto de JavaScript, puede Agregar la extensión a un grupo de referencia. Hay varios tipos de grupos de referencia, ya sean los que incluyen referencias implícitas y los que incluyen referencias de trabajo dedicadas. Para agregar una extensión, normalmente es necesario agregar el archivo como un grupo de referencia implícito, ya sea **implícito (Windows)** , **implícito (Web)** . Las referencias implícitas se encuentran en el ámbito de cada archivo. js abierto en el editor de código. Cuando se usa este método, es necesario agregar la extensión y el archivo que la extensión está complementando.

 Use la página **IntelliSense** del cuadro de diálogo **Opciones** para agregar una extensión como grupo de referencias. Para tener acceso a la página **IntelliSense** , elija **herramientas**, **Opciones** en la barra de menús y, a continuación, elija **Editor de texto**, **JavaScript**, **IntelliSense**, **referencias**. Para obtener más información sobre los grupos de referencia, vea IntelliSense y opciones de [JavaScript](../ide/javascript-intellisense.md) [, editor de texto, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

 Si desea utilizar la extensión para un conjunto específico de archivos, use una directiva de referencia. Cuando se usa este método, es necesario hacer referencia a la extensión y al archivo que la extensión está complementando. Para obtener información sobre cómo usar la Directiva de referencia, vea [IntelliSense de JavaScript](../ide/javascript-intellisense.md).

## <a name="handling-intellisense-events"></a>Controlar eventos de IntelliSense
 La característica de extensibilidad permite personalizar los resultados de IntelliSense mediante la suscripción a eventos como el `statementcompletion` evento del `intellisense` objeto del servicio de lenguaje. En el ejemplo siguiente se muestra una extensión simple utilizada por el servicio de lenguaje para ocultar los miembros que comienzan con un carácter de subrayado a partir de la finalización de instrucciones. Este código se encuentra en underscorefilter. js y se encuentra en la \\ \\ carpeta*ruta de instalación de Visual Studio*\JavaScript\References.

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

 En el código anterior, la extensión comprueba la [propiedad TargetName](#TargetName) y las propiedades de [propiedad de destino](#Target) del objeto de evento `statementcompletion` para excluir objetos como `this` y `window` y para garantizar que una lista de finalización de instrucciones válida pueda ser identifica. Si se puede identificar una lista de finalización, la extensión actualiza la colección de [propiedades de elementos](#Items) de finalización de instrucciones mediante el filtrado de los miembros que comienzan con un carácter de subrayado.

 Para obtener ejemplos adicionales, busque en la carpeta \\ \\*ruta de instalación de Visual Studio*\JavaScript\References. El archivo showPlainComments. js de esta carpeta proporciona ejemplos de uso de otros eventos para proporcionar la compatibilidad predeterminada de IntelliSense con las etiquetas de comentario estándar de JavaScript (//). Al igual que underscorefilter. js, showPlainComments. js ya está disponible como una extensión de trabajo y puede ver la información de IntelliSense resultante al usar etiquetas de comentario en el código para variables, funciones y objetos. Para obtener más ejemplos, vea [ejemplos de código](#CodeExamples).

> [!WARNING]
> Si modifica los archivos de extensión incluidos con Visual Studio, puede deshabilitar JavaScript IntelliSense o la característica admitida por la extensión.

 En el código de extensión, puede crear controladores para los siguientes tipos de evento mediante `addEventListener`:

- `statementcompletion`, que agrega un controlador para un evento de finalización de instrucciones. La finalización de instrucciones proporciona una lista de miembros para un tipo determinado que aparece después de escribir un carácter especial, como un punto (.) o una lista de identificadores que aparece mientras escribe o al presionar CTRL + J. El controlador recibe un objeto de evento de tipo `CompletionEvent`, que admite los siguientes miembros: [propiedad items](#Items), [propiedad target](#Target), [propiedad TargetName](#TargetName)y [propiedad Scope](#Scope).

- `signaturehelp`, que agrega un controlador para la información de parámetros de IntelliSense. La información de parámetros proporciona información sobre el número, los nombres y los tipos de parámetros necesarios para una función. El controlador recibe un objeto de evento de tipo `SignatureHelpEvent`, que admite los siguientes miembros: [propiedad de destino](#Target), [propiedad parentObject](#ParentObject), propiedad [functionComments](#FunctionComments), propiedad [functionHelp](#FunctionHelp).

- `statementcompletionhint`, que agrega un controlador para la información rápida de IntelliSense. El cuadro emergente información rápida muestra la declaración completa de los identificadores en el código. El controlador recibe un objeto de evento de tipo `CompletionHintEvent`, que admite los siguientes miembros: la [propiedad completionItem](#CompletionItem)y la [propiedad symbolHelp](#SymbolHelp).

  Para obtener ejemplos que muestran características de IntelliSense, como la finalización de instrucciones, la información de parámetros y la información rápida, vea [usar IntelliSense](../ide/using-intellisense.md).

> [!NOTE]
> En JavaScript, información rápida hace referencia al cuadro emergente que aparece a la derecha de una lista de finalización. No se puede invocar manualmente la información rápida.

## <a name="intellisenseObject"></a>Objeto IntelliSense
 En la tabla siguiente se muestran las funciones que están disponibles para el objeto `intellisense`. El objeto `intellisense` solo está disponible en tiempo de diseño.

|Función|Descripción|
|--------------|-----------------|
|`addEventListener(type, handler);`|Agrega un controlador de eventos para un evento de IntelliSense.<br /><br /> `type` es un valor de cadena. Entre los valores válidos se incluyen `statementcompletion`, `signaturehelp` y `statementcompletionhint`.<br /><br /> `handler` es una función de controlador de eventos que recibe un objeto de evento de uno de los siguientes tipos:<br /><br /> -    `CompletionEvent`, que se usa para el evento `statementcompletion`.<br />-    `SignatureHelpEvent`, que se usa para el evento `signaturehelp`.<br />-    `CompletionHintEvent`, que se usa para el evento `statementcompletionhint`.<br /><br /> Para obtener ejemplos que usan esta función, vea [ejemplos de código](#CodeExamples).|
|`annotate(obj, doc);`|Especifica la documentación de un objeto mediante la copia de comentarios de documentación de un objeto a otro objeto.<br /><br /> `obj` especifica el objeto al que se va a copiar la documentación.<br /><br /> `doc` especifica el objeto desde el que se va a copiar la documentación.<br /><br /> Para obtener un ejemplo en el que se muestra cómo usar esta función, vea [agregar anotaciones de IntelliSense](#Annotations).|
|`getFunctionComments(func);`|Devuelve los comentarios para una función especificada.<br /><br /> `func` especifica la función para la que se devuelven los comentarios.<br /><br /> Puede establecer el parámetro `func` mediante `completionItem.value`.<br /><br /> El objeto devuelto `functionComments` incluye los siguientes miembros: `above`, `inside` y `paramComment`. Para obtener más información, vea la propiedad de la [propiedad functionComments](#FunctionComments) .<br /><br /> solo se puede llamar a `getFunctionComments` desde dentro de uno de los controladores de eventos registrados por `addEventListener`.<br /><br /> Para ver un ejemplo en el que se muestra cómo usar esta función, vea \\ \\*ruta de instalación de Visual Studio*\JavaScript\References\showPlainComments.js.|
|`logMessage(msg);`|Envía mensajes de diagnóstico a la ventana de salida.<br /><br /> `msg` es una cadena que contiene el mensaje.<br /><br /> Para ver un ejemplo que muestra cómo usar esta función, consulte [envío de mensajes al ventana de salida](#Logging).|
|`nullWithCompletionsOf(value);`|Devuelve un valor null especial para el que la lista de finalización viene determinada por el objeto pasado en el parámetro `value`.<br /><br /> `value` determina la lista de finalización para el valor devuelto. `value` puede ser cualquier tipo.<br /><br /> El valor devuelto NULL se trata como null en tiempo de diseño, pero la lista de finalización para el valor devuelto es igual que la lista de finalización del parámetro `value`.<br /><br /> Un uso de esta función es proporcionar IntelliSense para un valor devuelto cuando el tipo de valor devuelto es predecible en tiempo de ejecución, pero el valor devuelto se `null` en tiempo de diseño.|
|`redirectDefinition(func, definition);`|Indica a IntelliSense que use la función de definición proporcionada en lugar de la función FUNC original cuando se solicite ayuda de parámetros o **ir a definición** .<br /><br /> `func` especifica la función de destino.<br /><br /> `definition` especifica la función que se va a usar en lugar de la función de destino para la información de parámetros e **ir a definición**.|
|`setCallContext(func, thisArg);`|Establece el contexto de llamada, o ámbito, para la función especificada.<br /><br /> `func` especifica la función para la que se va a establecer el ámbito.<br /><br /> `thisArg` es un literal de objeto al que puede hacer referencia la palabra clave `this`, que especifica el nuevo ámbito para el miembro. Puede incluir argumentos para pasar en este parámetro, por ejemplo, `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` proporciona un comportamiento similar a `Function.prototype.bind`, salvo que solo se usa para la compatibilidad con IntelliSense en tiempo de diseño. Puede usar `setCallContext` para establecer el ámbito de la función si necesita simular una llamada a código que, de otro modo, no es accesible, de modo que cuando llame a la función, la llamada a la función incluirá el ámbito y los argumentos correctos.|
|`undefinedWithCompletionsOf(value);`|Devuelve un valor no definido especial para el que la lista de finalización viene determinada por el objeto pasado en el parámetro `value`.<br /><br /> `value` determina la lista de finalización para el valor devuelto. `value` puede ser cualquier tipo.<br /><br /> El valor devuelto sin definir se trata como sin definir en tiempo de diseño, pero la lista de finalización para el valor devuelto es igual que la lista de finalización del parámetro `value`.<br /><br /> Un uso de esta función es proporcionar IntelliSense para un valor devuelto cuando el tipo de valor devuelto es predecible en tiempo de ejecución, pero el valor devuelto no está definido en tiempo de diseño.|
|`version()`|Devuelve la versión de Visual Studio.|

## <a name="event-members"></a>Miembros de evento
 En las secciones siguientes se describen los miembros que se exponen en el objeto de evento para los eventos siguientes: `statementcompletion`, `signaturehelp` y `statementcompletionhint`.

### <a name="CompletionItem"></a>Propiedad completionItem
 Devuelve el identificador, conocido como elemento de finalización, para el que se solicita un cuadro emergente de información rápida. Esta propiedad está disponible para el objeto de evento `statementcompletionhint` y para la propiedad [Items](#Items) del objeto de evento `statementcompletion`.

 Valor devuelto: `completionItem` objeto

 A continuación se muestran los miembros del objeto `completionItem`:

- `name`. Lectura y escritura cuando se usa en la colección de `items`; de lo contrario, es de solo lectura. Devuelve una cadena que identifica el elemento de finalización.

- `kind`. Lectura y escritura cuando se usa en la colección de `items`; de lo contrario, es de solo lectura. Devuelve una cadena que representa el tipo de elemento de finalización. Los valores posibles son método, campo, propiedad, parámetro, variable y reservado.

- `glyph`. Lectura y escritura cuando se usa en la colección de `items`; de lo contrario, es de solo lectura. Devuelve una cadena que representa un icono que se muestra en la lista de finalización. Los valores posibles para `glyph` usan el siguiente formato: vs:*glyphType*, donde *glyphType* corresponde a los miembros independientes del lenguaje en la enumeración <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>. Por ejemplo, `vs:GlyphGroupMethod` es un valor posible para `glyph`. Cuando no se establece `glyph`, la propiedad `kind` determina el icono predeterminado.

- `parentObject`. Sólo lectura. Devuelve el objeto primario.

- `value`. Sólo lectura. Devuelve un objeto que representa el valor del elemento de finalización.

- `comments`. Sólo lectura. Devuelve una cadena que contiene los comentarios que están por encima del campo o la variable.

- `scope`. Sólo lectura. Devuelve el ámbito del elemento de finalización. Los valores posibles son global, local, Parameter y Member.

### <a name="Items"></a>Propiedad items
 Obtiene o establece la matriz de elementos de finalización de instrucciones. Cada elemento de la matriz es un objeto de [propiedad completionItem](#CompletionItem) . La propiedad `items` está disponible para el objeto de evento `statementcompletion`.

 Valor devuelto: Array

### <a name="FunctionComments"></a>Propiedad functionComments
 Devuelve los comentarios de la función. Esta propiedad está disponible para el objeto de evento `signaturehelp`.

 Valor devuelto: `comments` objeto

 A continuación se muestran los miembros del objeto `comments`:

- `above`. Devuelve los comentarios sobre la función.

- `inside`. Devuelve los comentarios dentro de la función, normalmente en formato VSDoc.

- `paramComments`. Devuelve una matriz que representa los comentarios de cada parámetro de la función. Los miembros de la matriz incluyen:

  - `name`. Devuelve una cadena que representa el nombre del parámetro.

  - `comment`. Devuelve una cadena que contiene el comentario del parámetro.

### <a name="FunctionHelp"></a>Propiedad functionHelp
 Devuelve la ayuda de la función. Esta propiedad está disponible para el objeto de evento `signaturehelp`.

 Valor devuelto: `functionHelp` objeto

 A continuación se muestran los miembros del objeto `functionHelp`:

- `functionName`. Lectura y escritura. Devuelve una cadena que contiene el nombre de la función.

- `signatures`. Lectura y escritura. Obtiene o establece la matriz de firmas de función. Cada elemento de la matriz es un objeto `signature`. Algunas propiedades de `signature`, como `locid`, corresponden a los atributos de [comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md) comunes.

  Los miembros del objeto `signature` incluyen:

  - `description`. Lectura y escritura. Devuelve una cadena que describe la función.

  - `locid`. Lectura y escritura. Devuelve un identificador de cadena que contiene información de localización sobre la función.

  - `helpKeyword`. Lectura y escritura. Devuelve una cadena que contiene la palabra clave de ayuda.

  - `externalFile`. Lectura y escritura. Devuelve una cadena que representa el archivo que contiene el identificador de miembro.

  - `externalid`. Lectura y escritura. Devuelve una cadena que representa el identificador de miembro de la función.

  - `params`. Lectura y escritura. Obtiene o establece la matriz de parámetros para la función. Cada elemento de la matriz de parámetros es un objeto `parameter` que tiene propiedades que corresponden a los siguientes atributos del elemento [> \<param](../ide/param-javascript.md) :

    - `name`. Lectura y escritura. Devuelve una cadena que representa el nombre del parámetro.

    - `type`. Lectura y escritura. Devuelve una cadena que representa el tipo de parámetro.

    - `elementType`. Lectura y escritura. Si el tipo es `Array`, devuelve una cadena que representa el tipo de los elementos de la matriz.

    - `description`. Lectura y escritura. Devuelve una cadena que describe el parámetro.

    - `locid`. Lectura y escritura. Devuelve un identificador de cadena que contiene información de localización sobre la función.

    - `optional`. Lectura y escritura. Devuelve una cadena que indica si el parámetro es opcional. `true` indica que el parámetro es opcional;  `false` indica que no es.

  - `returnValue`. Lectura y escritura. Obtiene o establece un objeto de valor devuelto con propiedades que corresponden a los siguientes atributos del elemento [\<returns >](../ide/returns-javascript.md) :

    - `type`. Lectura y escritura. Devuelve una cadena que representa el tipo de valor devuelto.

    - `elementType`. Lectura y escritura. Si el tipo es `Array`, devuelve una cadena que representa el tipo de los elementos de la matriz.

    - `description`. Lectura y escritura. Devuelve una cadena que describe el valor devuelto.

    - `locid`. Lectura y escritura. Devuelve un identificador de cadena que contiene información de localización sobre la función.

    - `helpKeyword`. Lectura y escritura. Devuelve una cadena que contiene la palabra clave de ayuda.

    - `externalFile`. Lectura y escritura. Devuelve una cadena que representa el archivo que contiene el identificador de miembro.

    - `externalid`. Lectura y escritura. Devuelve una cadena que representa el identificador de miembro de la función.

### <a name="ParentObject"></a>Propiedad parentObject
 Devuelve el objeto primario de una función miembro. Por ejemplo, para `document.getElementByID`, `parentObject` devuelve el objeto `document`. Esta propiedad está disponible para el objeto de evento `signaturehelp`.

 Valor devuelto: objeto

### <a name="Target"></a>Propiedad de destino
 Devuelve un objeto que representa el elemento situado a la izquierda del carácter desencadenador, que es un punto (.). En el caso de las funciones, `target` devuelve la función para la que se solicita información de parámetros. Esta propiedad está disponible para los objetos de evento `statementcompletion` y `signaturehelp`.

 Valor devuelto: objeto

### <a name="TargetName"></a>targetName (propiedad)
 Devuelve una cadena que representa el destino. Por ejemplo, para "this.", `targetName` devuelve "this". Para "A. B" (cuando el cursor está después de "B"), `targetName` devuelve "B". Esta propiedad está disponible para el objeto de evento `statementcompletion`.

 Valor devuelto: cadena

### <a name="SymbolHelp"></a>Propiedad symbolHelp
 Devuelve el elemento de finalización para el que se solicita un cuadro emergente de información rápida. Esta propiedad está disponible para el objeto de evento `statementcompletionhint`.

 Valor devuelto: `symbolHelp` objeto.

 Algunas propiedades del objeto `symbolHelp`, como `locid`, corresponden a los atributos de [comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md) comunes.

 A continuación se muestran los miembros del objeto `symbolHelp`:

- `name`. Lectura y escritura. Devuelve una cadena que contiene el nombre del identificador.

- `symbolType`. Lectura y escritura. Devuelve una cadena que representa el tipo de símbolo. Entre los valores posibles se incluyen desconocido, booleano, número, cadena, objeto, función, matriz, fecha y Regex.

- `symbolDisplayType`. Lectura y escritura. Devuelve una cadena que contiene el nombre de tipo que se va a mostrar. Si no se establece `symbolDisplayType`, se utiliza `symbolType`.

- `elementType`. Lectura y escritura. Si el `symbolType` es `Array`, devuelve una cadena que representa el tipo de los elementos de la matriz.

- `scope`. Lectura y escritura. Devuelve una cadena que representa el ámbito del símbolo. Entre los valores posibles se incluyen global, local, Parameter y Member.

- `description`. Lectura y escritura. Devuelve una cadena que contiene una descripción del símbolo.

- `locid`. Lectura y escritura. Devuelve un identificador de cadena que contiene información de localización sobre el símbolo.

- `helpKeyword`. Lectura y escritura. Devuelve una cadena que contiene la palabra clave de ayuda.

- `externalFile`. Lectura y escritura. Devuelve una cadena que representa el archivo que contiene el identificador de miembro.

- `externalid`. Lectura y escritura. Devuelve una cadena que representa el identificador de miembro del símbolo.

- `functionHelp`. Lectura y escritura. Devuelve una [propiedad functionHelp](#FunctionHelp), que puede contener información cuando el `symbolType` es function.

### <a name="Scope"></a>Propiedad de ámbito
 Devuelve el ámbito de finalización del evento. Los valores posibles para el ámbito de finalización son global y miembros. Esta propiedad está disponible para el objeto de evento `statementcompletion`.

 Valor devuelto: cadena

## <a name="debugging-intellisense-extensions"></a>Depurar extensiones de IntelliSense
 No se pueden depurar extensiones, pero se puede usar la función de [objeto IntelliSense](#intellisenseObject) para enviar información a la ventana de salida de Visual Studio. Para obtener un ejemplo en el que se muestra cómo usar esta función, vea [enviar mensajes a la ventana de salida](#Logging) más adelante en este tema. Para que `logMessage` funcione, al menos un controlador de eventos debe estar registrado en una extensión.

## <a name="CodeExamples"></a>Ejemplos de código
 En esta sección se incluyen ejemplos de código que muestran cómo usar las API de extensibilidad de IntelliSense. También hay otras maneras de usar estas API. Para obtener más ejemplos, vea los siguientes archivos en la carpeta \\ \\*ruta de instalación de Visual Studio*\JavaScript\References. Estos son ejemplos de trabajo usados por el servicio de lenguaje JavaScript.

- underscoreFilter. js. Este código oculta los miembros privados de IntelliSense. Incluye controladores de eventos para el evento `statementcompletion`.

- showPlainComments. js. Este código proporciona compatibilidad con IntelliSense para los comentarios estándar. Incluye controladores de eventos para los eventos `signaturehelp` y `statementcompletionhint`.

### <a name="Annotations"></a>Agregar anotaciones de IntelliSense
 En el procedimiento siguiente se muestra cómo proporcionar compatibilidad con la documentación de IntelliSense para una biblioteca de terceros sin modificar directamente la biblioteca. Para ello, puede usar `intellisense.annotate` en una extensión.

 Para que este ejemplo funcione, necesita los siguientes archivos JavaScript en el proyecto:

- demoLib. js, que es un archivo de proyecto que representa una biblioteca de terceros.

- demoLib. IntelliSense. js, que es la extensión de IntelliSense. No es necesario incluir este archivo en el proyecto, pero debe estar en la misma carpeta que exampleLib.js.

- appCode.js, que es un archivo de proyecto que representa código de aplicación.

##### <a name="to-add-an-intellisense-annotation"></a>Para agregar una anotación de IntelliSense

1. Agregue el código siguiente a demoLib. js.

    ```javascript
    function someFunc(a) { };
    var rectangle;

    ```

2. Agregue el código siguiente a demoLib. IntelliSense. js.

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

3. Agregue la directiva reference siguiente como la primera línea de appCode.js. La ruta de acceso usada aquí indica que los archivos JavaScript están en la misma carpeta.

    ```javascript
    /// <reference path="demoLib.js" />

    ```

4. En appCode.js, escriba el código siguiente. Verá los comentarios de documentación XML en la extensión que se muestra como información de parámetros de IntelliSense.

     ![Ejemplo que muestra el uso de IntelliSense. anotar](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")

5. En appCode.js, escriba el código siguiente. Mientras escribe, verá los comentarios estándar en la extensión que se muestra como información rápida de IntelliSense.

     ![Ejemplo que muestra el uso de IntelliSense. anotar](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")

### <a name="Logging"></a>Enviar mensajes al Ventana de salida
 En el procedimiento siguiente se muestra cómo enviar mensajes a la ventana de salida. Puede enviar mensajes para ayudar a depurar extensiones de IntelliSense.

 Para que este ejemplo funcione, necesita los siguientes archivos JavaScript en el proyecto:

- exampleLib. js, que es un archivo de proyecto que representa una biblioteca de terceros.

- exampleLib. IntelliSense. js, que es la extensión de IntelliSense. No es necesario incluir este archivo en el proyecto, pero debe estar en la misma carpeta que exampleLib.js.

- appCode.js, que es un archivo de proyecto que representa código de aplicación.

##### <a name="to-send-a-message-to-the-output-window"></a>Para enviar un mensaje a la ventana de salida

1. Agregue el código siguiente a exampleLib. js.

    ```javascript
    var someVar = {
        a: 1,
        b: 'hello'
    };
    ```

2. Agregue el código siguiente a exampleLib. IntelliSense. js.

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

3. Agregue la directiva reference siguiente como la primera línea de appCode.js. La ruta de acceso usada aquí indica que los archivos JavaScript están en la misma carpeta.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

4. En la ventana salida, elija **JavaScript Language Service** en la lista **Mostrar salida de** . (Para ver la ventana de salida, seleccione **salida** en el menú Ver).

5. En appCode.js, escriba el código siguiente. Mientras escribe, la ventana de salida muestra mensajes del servicio de lenguaje. El primer mensaje de la ventana de salida indica que se ha solicitado la finalización de instrucciones para el ámbito actual.

    ```javascript
    some
    ```

     A continuación se muestra una vista parcial del resultado que debería ver.

    ```scr
    03:16:14.3113: statement completion for current scope requested
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined

    …
    ```

6. Elija el botón **Borrar todo** en la ventana de salida.

7. Escriba el siguiente código. El primer mensaje de la ventana de salida indica que se ha solicitado una lista de miembros.

    ```javascript
    someVar.
    ```

     A continuación se muestra una vista parcial de la salida que debería ver:

    ```scr
    03:17:43.4032: member list requested, target: someVar
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:

    …
    ```

### <a name="Icons"></a>Cambiar los iconos de IntelliSense
 En el procedimiento siguiente se muestra cómo cambiar los iconos que IntelliSense muestra de forma predeterminada. Esto puede resultar útil cuando se proporciona información de IntelliSense sobre conceptos específicos de la biblioteca, como espacios de nombres, clases, interfaces y enumeraciones.

 Para ver los valores de los iconos disponibles, consulte <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>.

 Para que este ejemplo funcione, necesita los siguientes archivos JavaScript en el proyecto:

- exampleLib. js, que es un archivo de proyecto que reactiva una biblioteca de terceros.

- exampleLib. IntelliSense. js, que es la extensión de IntelliSense. No es necesario incluir este archivo en el proyecto, pero debe estar en la misma carpeta que exampleLib.js.

- appCode.js, que es un archivo de proyecto que representa código de aplicación.

##### <a name="to-change-the-icons"></a>Para cambiar los iconos

1. Agregue el código siguiente a exampleLib. js.

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

2. Agregue el código siguiente a exampleLib. IntelliSense. js.

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

3. Agregue la directiva reference siguiente como la primera línea de appCode.js. La ruta de acceso usada aquí indica que los archivos JavaScript están en la misma carpeta.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

4. En appCode.js, escriba el código siguiente. Mientras escribe, verá que el icono del espacio de nombres ha cambiado a "{}", como se usa en C#.

     ![Ejemplo que muestra el uso de la propiedad glyph](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")

5. En appCode.js, escriba el código siguiente. Mientras escribe, verá un nuevo icono de enumeración para el miembro Enum1 y un nuevo icono de clase para el miembro SomeClass1.

     ![Ejemplo que muestra el uso de la propiedad glyph](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")

### <a name="Overriding"></a>Evitar efectos en tiempo de ejecución en los resultados de IntelliSense
 El servicio de lenguaje JavaScript ejecuta código para proporcionar de forma dinámica información de IntelliSense. Como resultado, el comportamiento en tiempo de ejecución puede interferir ocasionalmente con los resultados deseados. En el procedimiento siguiente se muestra cómo invalidar los resultados de IntelliSense cuando el comportamiento en tiempo de ejecución produce una IntelliSense incorrecta.

 Para que este ejemplo funcione, necesita los siguientes archivos JavaScript en el proyecto:

- exampleLib. js, que es un archivo de proyecto que representa una biblioteca de terceros.

- exampleLib. IntelliSense. js, que es la extensión de IntelliSense. No es necesario incluir este archivo en el proyecto, pero debe estar en la misma carpeta que exampleLib.js.

- appCode.js, que es un archivo de proyecto que representa código de aplicación.

##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>Para evitar efectos en tiempo de ejecución en los resultados de IntelliSense

1. Agregue el código siguiente a exampleLib. js.

    ```javascript
    function after(count, func) {
        return function () {
            if (--times < 1) {
                return func.apply(this, arguments);
            }
        };
    };
    ```

     En el código anterior, la función encapsulada omite las llamadas iniciales, según el valor de `count`, y no devuelve resultados.

2. Agregue la directiva reference siguiente como la primera línea de appCode.js. La ruta de acceso usada aquí indica que los archivos JavaScript están en la misma carpeta.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

3. En appCode.js, escriba el código siguiente. La lista de identificadores aparece en lugar de IntelliSense porque nunca se llama a la función ajustada, lo que significa que la función `throttled` no devuelve ningún resultado.

     ![Ejemplo de invalidación de los resultados de IntelliSense](../ide/media/js-intellisense-override.png "js_intellisense_override")

4. Agregue el código siguiente a exampleLib. IntelliSense. js. Esto cambiará el comportamiento en tiempo de diseño para que IntelliSense se muestre para la función ajustada, según lo esperado.

    ```javascript
    window.after = function (count, func) {
        // Just return func.
        return func;
    };
    ```

5. En appCode. js, pruebe los resultados escribiendo el mismo código que escribió anteriormente. Esta vez, IntelliSense proporciona la información deseada.

     ![Ejemplo de invalidación de los resultados de IntelliSense](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")

## <a name="see-also"></a>Vea también
 [IntelliSense para JavaScript](../ide/javascript-intellisense.md) [Finalización de instrucciones para identificadores](../ide/statement-completion-for-identifiers.md)
