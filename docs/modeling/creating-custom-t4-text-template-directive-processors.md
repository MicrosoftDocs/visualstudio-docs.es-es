---
title: Crear procesadores de directivas personalizadas para las plantillas de texto T4
description: Obtenga información sobre el proceso de transformación de plantillas de texto y cómo crear un procesador de directivas de plantillas de texto T4 personalizado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59644275f17eac197074351a777959bb1826a5de
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389506"
---
# <a name="create-custom-t4-text-template-directive-processors"></a>Crear procesadores de directivas personalizadas para las plantillas de texto T4

El *proceso de transformación de plantilla de* texto toma un archivo de plantilla *de* texto como entrada y genera un archivo de texto como salida. El *motor de transformación de* plantilla de texto controla el proceso y el  motor interactúa con un host de transformación de plantilla de texto y uno o varios procesadores de directivas de plantilla de texto para completar el proceso. Para obtener más información, vea [El proceso de transformación Plantilla de texto](../modeling/the-text-template-transformation-process.md).

Para crear un procesador de directivas personalizado, crea una clase que herede de <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

La diferencia entre estos dos es que implementa la interfaz mínima necesaria para obtener parámetros del usuario y generar el código que genera el archivo de salida <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> de plantilla. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementa el patrón de diseño requires/provides. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> controla dos parámetros especiales, `requires` y `provides` .  Por ejemplo, un procesador de directivas personalizado podría aceptar un nombre de archivo del usuario, abrir y leer el archivo y, a continuación, almacenar el texto del archivo en una variable denominada `fileText` . Una subclase de la clase podría tomar un nombre de archivo del usuario como valor del parámetro y el nombre de la variable en la que se almacenará el texto como valor <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> `requires` del `provides` parámetro. Este procesador abriría y leería el archivo y, a continuación, almacenaría el texto del archivo en la variable especificada.

Antes de llamar a un procesador de directivas personalizado desde una plantilla de Visual Studio, debe registrarlo.

Para obtener más información sobre cómo agregar la clave del Registro, vea [Deploying a Custom Directive Processor](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Directivas personalizadas

Una directiva personalizada tiene este aspecto:

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

Puede usar un procesador de directivas personalizado cuando desee acceder a recursos o datos externos desde una plantilla de texto.

Diferentes plantillas de texto pueden compartir la funcionalidad que proporciona un procesador de directivas única, por lo que los procesadores de directivas proporcionan una manera de factorar el código para su reutilización. La directiva integrada es similar, ya que se puede usar para factormente el código y `include` compartirlo entre diferentes plantillas de texto. La diferencia es que cualquier funcionalidad que proporciona `include` la directiva es fija y no acepta parámetros. Si desea proporcionar funcionalidad común a una plantilla de texto y permitir que la plantilla pase parámetros, debe crear un procesador de directivas personalizado.

Algunos ejemplos de procesadores de directivas personalizadas podrían ser:

- Procesador de directivas para devolver datos de una base de datos que acepta un nombre de usuario y una contraseña como parámetros.

- Procesador de directivas para abrir y leer un archivo que acepta el nombre del archivo como parámetro.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Partes principales de un procesador de directivas personalizado

Para desarrollar un procesador de directivas, debe crear una clase que herede de <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> .

Los métodos `DirectiveProcessor` más importantes que debe implementar son los siguientes.

- `bool IsDirectiveSupported(string directiveName)` - Devuelve `true` si el procesador de directivas puede tratar con la directiva con nombre.

- `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` - El motor de plantillas llama a este método para cada aparición de una directiva en la plantilla. El procesador debe guardar los resultados.

Después de todas las llamadas a ProcessDirective(), el motor de creación de temporales llamará a estos métodos:

- `string[] GetReferencesForProcessingRun()` : devuelve los nombres de ensamblados que requiere el código de plantilla.

- `string[] GetImportsForProcessingRun()` : devuelve los espacios de nombres que se pueden usar en el código de plantilla.

- `string GetClassCodeForProcessingRun()` : devuelve el código de métodos, propiedades y otras declaraciones que el código de plantilla puede usar. La manera más fácil de hacerlo es compilar una cadena que contenga el código de C# Visual Basic código. Para que el procesador de directivas sea capaz de llamarse desde una plantilla que usa cualquier lenguaje CLR, puede construir las instrucciones como un árbol CodeDom y, a continuación, devolver el resultado de serializar el árbol en el lenguaje utilizado por la plantilla.

- Para obtener más información, [vea Tutorial: Crear un procesador de directivas personalizado.](../modeling/walkthrough-creating-a-custom-directive-processor.md)

## <a name="see-also"></a>Vea también

- [Implementar un procesador de directivas personalizadas](../modeling/deploying-a-custom-directive-processor.md) explica cómo registrar un procesador de directivas personalizado.
- [Tutorial: Crear un procesador](../modeling/walkthrough-creating-a-custom-directive-processor.md) de directivas personalizadas describe cómo crear un procesador de directivas personalizado, cómo registrar y probar el procesador de directivas y cómo dar formato HTML al archivo de salida.
