---
title: Crear procesadores de directivas personalizadas para las plantillas de texto T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4221489318e4cdd4268d5c5d00cbaa079838dcba
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55940898"
---
# <a name="creating-custom-t4-text-template-directive-processors"></a>Crear procesadores de directivas personalizadas para las plantillas de texto T4

El *el proceso de transformación de plantillas de texto* toma un *plantilla de texto* archivo como entrada y produce un archivo de texto como salida. El *motor de transformación de plantillas de texto* el proceso y el motor interactúa con un host de transformación de plantillas de texto y la plantilla de texto de uno o varios de los controles *procesadores de directivas* para completar la proceso. Para obtener más información, consulte [el proceso de transformación de plantillas de texto](../modeling/the-text-template-transformation-process.md).

Para crear un procesador de directivas personalizado, crea una clase que herede de <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

La diferencia entre estos dos es que <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implementa la interfaz mínima necesaria para obtener los parámetros del usuario y generar el código que genera el archivo de salida de la plantilla. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementa el patrón de diseño requiere/proporciona. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> controla los dos parámetros especiales, `requires` y `provides`.  Por ejemplo, un procesador de directivas personalizado es posible que acepte un nombre de archivo del usuario, abrirlo y leer el archivo y, a continuación, almacenar el texto del archivo en una variable que se denomina `fileText`. Una subclase de la <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> clase podría tomar un nombre de archivo del usuario como el valor de la `requires` y el nombre de la variable en la que se va a almacenar el texto como el valor de la `provides` parámetro. Este procesador de abrir y leer el archivo y, a continuación, almacenar el texto del archivo en la variable especificada.

Antes de llamar a un procesador de directivas personalizado desde una plantilla de texto en Visual Studio, debe registrarlo.

Para obtener más información sobre cómo agregar la clave del registro, consulte [implementar un procesador de directivas personalizado](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Directivas personalizadas

Una directiva personalizada tiene este aspecto:

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

Puede usar un procesador de directivas personalizado cuando desee tener acceso a recursos o datos externos desde una plantilla de texto.

Diferentes plantillas de texto pueden compartir la funcionalidad que proporciona un único procesador de directivas, por lo que los procesadores de directivas proporcionan una manera para factorizar el código para su reutilización. Integrado `include` directiva es similar, porque puede usarla para factorizar el código y compartirlo entre diferentes plantillas de texto. La diferencia es que cualquier funcionalidad que el `include` directiva proporciona es fijo y no acepta parámetros. Si desea proporcionar una funcionalidad común a una plantilla de texto y permitir que la plantilla pasar parámetros, debe crear un procesador de directivas personalizado.

Algunos ejemplos de procesadores de directivas personalizados podrían ser:

-   Un procesador de directivas para devolver datos de una base de datos que acepta un nombre de usuario y una contraseña como parámetros.

-   Un procesador de directivas para abrir y leer un archivo que acepta el nombre del archivo como un parámetro.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Partes de la entidad de seguridad de un procesador de directivas personalizada

Para desarrollar un procesador de directivas, debe crear una clase que herede de <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

Lo más importante `DirectiveProcessor` métodos que debe implementar son los siguientes.

-   `bool IsDirectiveSupported(string directiveName)` : Devuelve `true` si el procesador de directivas puede tratar con la directiva con nombre.

-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` : El motor de plantilla llama a este método para cada aparición de una directiva en la plantilla. El procesador debe guardar los resultados.

Después de todas las llamadas a ProcessDirective() el motor de plantillas llamará a estos métodos:

-   `string[] GetReferencesForProcessingRun()` : Devuelve los nombres de ensamblados que requiere el código de plantilla.

-   `string[] GetImportsForProcessingRun()` -Devuelve los espacios de nombres que se pueden usar en el código de plantilla.

-   `string GetClassCodeForProcessingRun()` -Devuelve el código de los métodos, propiedades y otras declaraciones que puede usar el código de plantilla. La manera más fácil de hacerlo es generar una cadena que contiene el código C# o Visual Basic. Para hacer que el procesador de directivas sean capaces de que se llama desde una plantilla que use cualquier lenguaje CLR, puede construir las instrucciones como un árbol CodeDom y, a continuación, devolver el resultado de serializar el árbol en el idioma usado por la plantilla.

-   Para obtener más información, vea [Tutorial: Creación de un procesador de directivas personalizado](../modeling/walkthrough-creating-a-custom-directive-processor.md).

## <a name="see-also"></a>Vea también

- [Implementar un procesador de directivas personalizado](../modeling/deploying-a-custom-directive-processor.md) se explica cómo registrar un procesador de directivas personalizado.
- [Tutorial: Crear un procesador de directivas personalizado](../modeling/walkthrough-creating-a-custom-directive-processor.md) describe cómo crear un procesador de directivas personalizado, cómo registrar y probar el procesador de directivas y cómo dar formato al archivo de salida como HTML.