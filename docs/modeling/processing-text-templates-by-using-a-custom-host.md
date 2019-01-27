---
title: Procesar las plantillas de texto mediante un host personalizado
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: d6de5da0ca6026ad993cbd2d4b2e9cb3e8c9280b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962006"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Procesar plantillas de texto mediante un host personalizado

El *transformación de plantilla de texto* procesar toma un *plantilla de texto* archivo como entrada y produce un archivo de texto como salida. El motor de transformación de texto puede llamar desde una extensión de Visual Studio o desde una aplicación independiente que se ejecuta en una máquina donde está instalado Visual Studio. Sin embargo, debe proporcionar un *host de plantillas de texto*. Esta clase conecta la plantilla al entorno, localizando recursos como ensamblados y archivos de inclusión, y trabajando con los mensajes de error y resultado.

> [!TIP]
> Si está escribiendo una extensión o paquete que se ejecutará dentro de Visual Studio, considere la posibilidad de utilizar el servicio de plantillas de texto, en lugar de escribir su propio host. Para obtener más información, consulte [invocar la transformación de texto en una extensión de VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> No se recomienda utilizar las transformaciones de plantilla de texto en aplicaciones de servidor. No se recomienda utilizar las transformaciones de plantilla de texto excepto en un subproceso único. Esto se debe a que el motor de plantillas de texto vuelve a utilizar un AppDomain único para traducir, compilar y ejecutar plantillas. El código traducido no es seguro para subprocesos. El motor está diseñado para procesar los archivos en serie, tal como están en un proyecto de Visual Studio en tiempo de diseño.
>
> Para las aplicaciones de tiempo de ejecución, considere el uso de plantillas de texto preprocesadas: vea [generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

Si la aplicación utiliza un conjunto de plantillas que se corrigen en tiempo de compilación, resulta más sencillo usar plantillas de texto preprocesadas. También puede usar este enfoque si la aplicación se ejecutará en un equipo en el que no está instalado Visual Studio. Para obtener más información, consulte [generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="execute-a-text-template-in-your-application"></a>Ejecutar una plantilla de texto en la aplicación

Para ejecutar una plantilla de texto, se llama al método ProcessTemplate de <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 La aplicación debe encontrar y proporcionar la plantilla y debe trabajar con el resultado.

 En el parámetro `host`, debe proporcionar una clase que implemente <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. El motor lo vuelve a llamar.

 El host debe poder registrar errores, resolver referencias a archivos de ensamblado e inclusión, proporciona un dominio de aplicación en el que se pueda ejecutar la plantilla, y llamar el procesador adecuado para cada directiva.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> se define en **Microsoft.VisualStudio.TextTemplating.\*. 0.log dll**, y <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> se define en **Microsoft.VisualStudio.TextTemplating.Interfaces.\*. 0.log dll**.

## <a name="in-this-section"></a>En esta sección
 [Tutorial: Creación de un Host de plantilla de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md) se muestra cómo crear un host de plantilla de texto personalizado que hace que la funcionalidad de la plantilla de texto que estén disponibles fuera de Visual Studio.

## <a name="reference"></a>Referencia
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>

## <a name="related-sections"></a>Secciones relacionadas

- [El proceso de transformación de plantillas de texto](../modeling/the-text-template-transformation-process.md) describe cómo funciona la transformación de texto y qué partes se pueden personalizar.
- [Crear procesadores de directiva de plantilla de texto personalizado T4](../modeling/creating-custom-t4-text-template-directive-processors.md) proporciona una visión general del texto de los procesadores de directivas de plantilla.