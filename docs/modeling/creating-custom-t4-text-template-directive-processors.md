---
title: Crear procesadores de directivas personalizadas para las plantillas de texto T4
description: Obtenga información sobre el proceso de transformación de plantillas de texto y cómo crear un procesador de directivas de plantillas de texto T4 personalizado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 283f2122c05a91a5e677293f59e3f6e02d43f63a
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363436"
---
# <a name="create-custom-t4-text-template-directive-processors"></a>Crear procesadores de directivas personalizadas para las plantillas de texto T4

El *proceso de transformación de plantillas de texto* toma un archivo de *plantilla de texto* como entrada y genera un archivo de texto como salida. El *motor de transformación de plantillas de texto* controla el proceso y el motor interactúa con un host de transformación de plantillas de texto y uno o varios *procesadores de directivas* de plantilla de texto para completar el proceso. Para obtener más información, vea [el proceso de transformación de plantillas de texto](../modeling/the-text-template-transformation-process.md).

Para crear un procesador de directivas personalizado, crea una clase que herede de <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

La diferencia entre estos dos es que <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implementa la interfaz mínima necesaria para obtener los parámetros del usuario y generar el código que genera el archivo de salida de la plantilla. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementa el modelo de diseño requiere/proporciona. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> controla dos parámetros especiales, `requires` y `provides` .  Por ejemplo, un procesador de directivas personalizado podría aceptar un nombre de archivo del usuario, abrir y leer el archivo y, a continuación, almacenar el texto del archivo en una variable denominada `fileText` . Una subclase de la <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> clase podría tomar un nombre de archivo del usuario como el valor del `requires` parámetro y el nombre de la variable en la que se almacenará el texto como el valor del `provides` parámetro. Este procesador abriría y leyó el archivo y, a continuación, almacena el texto del archivo en la variable especificada.

Antes de llamar a un procesador de directivas personalizado desde una plantilla de texto en Visual Studio, debe registrarlo.

Para obtener más información sobre cómo agregar la clave del registro, vea [implementar un procesador de directivas personalizado](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Directivas personalizadas

Una directiva personalizada tiene el siguiente aspecto:

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

Puede usar un procesador de directivas personalizado si desea tener acceso a los datos externos o a los recursos de una plantilla de texto.

Las distintas plantillas de texto pueden compartir la funcionalidad que proporciona un procesador de directivas único, por lo que los procesadores de directivas proporcionan una manera de factorizar el código para reutilizarlo. La `include` Directiva integrada es similar, porque se puede usar para factorizar código y compartirla entre distintas plantillas de texto. La diferencia es que cualquier funcionalidad que `include` proporciona la Directiva es fija y no acepta parámetros. Si desea proporcionar una funcionalidad común a una plantilla de texto y permitir que la plantilla pase parámetros, debe crear un procesador de directivas personalizado.

Algunos ejemplos de procesadores de directivas personalizados podrían ser:

- Procesador de directivas para devolver datos de una base de datos que acepta un nombre de usuario y una contraseña como parámetros.

- Un procesador de directivas para abrir y leer un archivo que acepta el nombre del archivo como parámetro.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Partes principales de un procesador de directivas personalizado

Para desarrollar un procesador de directivas, debe crear una clase que herede de <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> .

Los métodos más importantes `DirectiveProcessor` que debe implementar son los siguientes.

- `bool IsDirectiveSupported(string directiveName)` -Devuelve `true` si el procesador de directivas puede tratar con la Directiva con nombre.

- `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` -El motor de plantilla llama a este método para cada aparición de una directiva en la plantilla. El procesador debe guardar los resultados.

Después de todas las llamadas a ProcessDirective (), el motor de plantillas llamará a estos métodos:

- `string[] GetReferencesForProcessingRun()` -Devuelve los nombres de los ensamblados que requiere el código de plantilla.

- `string[] GetImportsForProcessingRun()` -Devuelve los espacios de nombres que se pueden usar en el código de plantilla.

- `string GetClassCodeForProcessingRun()` -Devuelve el código de los métodos, las propiedades y otras declaraciones que puede usar el código de plantilla. La forma más fácil de hacerlo es crear una cadena que contenga el código de C# o Visual Basic. Para hacer que el procesador de directivas sea capaz de ser llamado desde una plantilla que usa cualquier lenguaje CLR, puede construir las instrucciones como un árbol CodeDom y devolver después el resultado de serializar el árbol en el lenguaje usado por la plantilla.

- Para obtener más información, vea [Tutorial: crear un procesador de directivas personalizado](../modeling/walkthrough-creating-a-custom-directive-processor.md).

## <a name="see-also"></a>Consulta también

- [Implementar un procesador de directivas personalizado](../modeling/deploying-a-custom-directive-processor.md) explica cómo registrar un procesador de directivas personalizado.
- [Tutorial: crear un procesador de directivas personalizado](../modeling/walkthrough-creating-a-custom-directive-processor.md) describe cómo crear un procesador de directivas personalizado, cómo registrar y probar el procesador de directivas y cómo dar formato al archivo de salida como HTML.
