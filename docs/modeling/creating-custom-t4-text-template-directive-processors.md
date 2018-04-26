---
title: Crear procesadores de directivas personalizadas para las plantillas de texto T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 49a3c24116e6cc78084d0830a662ad7a3522d32c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="creating-custom-t4-text-template-directive-processors"></a>Crear procesadores de directivas personalizadas para las plantillas de texto T4

El *proceso de transformación de plantillas de texto* toma una *plantilla de texto* archivo como entrada y genera un archivo de texto como salida. El *motor de transformación de plantillas de texto* controles el proceso y el motor interactúa con un host de transformación de plantillas de texto y una o varias plantillas de texto *procesadores de directivas* para completar el proceso. Para obtener más información, consulte [el proceso de transformación de plantillas de texto](../modeling/the-text-template-transformation-process.md).

Para crear un procesador de directivas personalizado, crea una clase que herede de <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

La diferencia entre estos dos es que <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implementa la interfaz mínima necesaria para obtener los parámetros del usuario y generar el código que genera el archivo de salida de la plantilla. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementa el modelo de diseño requiere/proporciona. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> controla dos parámetros especiales, `requires` y `provides`.  Por ejemplo, un procesador de directivas personalizado podría acepte un nombre de archivo del usuario, abrir y leer el archivo y, a continuación, almacenar el texto del archivo en una variable que se denomina `fileText`. Una subclase de la <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> clase podría tomar un nombre de archivo del usuario como el valor de la `requires` parámetro y el nombre de la variable en la que se va a almacenar el texto como el valor de la `provides` parámetro. Este procesador podría abrir y leer el archivo y, a continuación, almacenar el texto del archivo en la variable especificada.

Antes de llamar a un procesador de directivas personalizado desde una plantilla de texto en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], debe registrarlo.

Para obtener más información sobre cómo agregar la clave del registro, consulte [implementar un procesador de directivas personalizado](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Directivas personalizadas

Una directiva personalizada tiene el siguiente aspecto:

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

Puede usar un procesador de directivas personalizado cuando desee tener acceso a recursos o datos externos desde una plantilla de texto.

Varias plantillas de texto pueden compartir la funcionalidad que proporciona un único procesador de directivas, por lo que los procesadores de directivas proporcionan una manera de factorizar el código para su reutilización. Integrado `include` directiva es similar, porque se puede utilizar para separe el código y compartirlo entre varias plantillas de texto. La diferencia es que cualquier funcionalidad que la `include` directiva proporciona es fija y no acepta parámetros. Si desea proporcionar funcionalidad común a una plantilla de texto y permitir que la plantilla pasar parámetros, debe crear un procesador de directivas personalizado.

Algunos ejemplos de procesadores de directivas personalizados podrían ser:

-   Un procesador de directivas para devolver datos de una base de datos que acepta un nombre de usuario y una contraseña como parámetros.

-   Un procesador de directivas para abrir y leer un archivo que acepta el nombre del archivo como un parámetro.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Partes de la entidad de seguridad de un procesador de directivas personalizado

Para desarrollar un procesador de directivas, debe crear una clase que herede de <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

El más importante `DirectiveProcessor` métodos que debe implementar son los siguientes.

-   `bool IsDirectiveSupported(string directiveName)` -Devuelto `true` si el procesador de directivas puede ocuparse de la directiva con nombre.

-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` : El motor de plantilla llama a este método para cada aparición de una directiva en la plantilla. El procesador debe guardar los resultados.

Después de todas las llamadas a ProcessDirective() el motor de plantillas llamará a estos métodos:

-   `string[] GetReferencesForProcessingRun()` -Devuelve los nombres de ensamblados que requiere el código de plantilla.

-   `string[] GetImportsForProcessingRun()` -Devuelve los espacios de nombres que se pueden usar en el código de plantilla.

-   `string GetClassCodeForProcessingRun()` -Devuelve el código de métodos, propiedades y otras declaraciones que puede usar el código de plantilla. La manera más fácil de hacerlo es generar una cadena que contiene código de Visual Basic o C#. Para hacer que el procesador de directivas puede llamarse desde una plantilla que usa cualquier lenguaje CLR, puede construir las instrucciones como un árbol CodeDom y, a continuación, devolver el resultado de serializar el árbol en el idioma usado por la plantilla.

-   Para obtener más información, consulte [Tutorial: crear un procesador de directivas personalizado](../modeling/walkthrough-creating-a-custom-directive-processor.md).

## <a name="see-also"></a>Vea también

- [Implementar un procesador de directivas personalizado](../modeling/deploying-a-custom-directive-processor.md) explica cómo registrar un procesador de directivas personalizado.
- [Tutorial: Crear un procesador de directivas personalizado](../modeling/walkthrough-creating-a-custom-directive-processor.md) describe cómo crear un procesador de directivas personalizado, cómo registrar y probar el procesador de directivas y cómo dar formato al archivo de salida como HTML.