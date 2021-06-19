---
title: Procesar las plantillas de texto mediante un host personalizado
description: Obtenga información sobre que el proceso de transformación de la plantilla de texto toma un archivo de plantilla de texto como entrada y genera un archivo de texto como salida.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a301df6edaf8558ade5c8a297f233b58de6d8f4e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390937"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Procesar plantillas de texto mediante un host personalizado

El *proceso de transformación de plantilla* de texto toma un archivo de plantilla *de* texto como entrada y genera un archivo de texto como salida. Puede llamar al motor de transformación de texto desde una extensión Visual Studio o desde una aplicación independiente que se ejecuta en una máquina en la que Visual Studio está instalado. Sin embargo, debe proporcionar un *host de templating de texto*. Esta clase conecta la plantilla al entorno, localizando recursos como ensamblados y archivos de inclusión, y trabajando con los mensajes de error y resultado.

> [!TIP]
> Si va a escribir un paquete o extensión que se ejecutará dentro de Visual Studio, considere la posibilidad de usar el servicio de templación de texto, en lugar de escribir su propio host. Para obtener más información, vea [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> No se recomienda utilizar las transformaciones de plantilla de texto en aplicaciones de servidor. No se recomienda utilizar las transformaciones de plantilla de texto excepto en un subproceso único. Esto se debe a que el motor de plantillas de texto vuelve a utilizar un AppDomain único para traducir, compilar y ejecutar plantillas. El código traducido no es seguro para subprocesos. El motor está diseñado para procesar archivos en serie, ya que se encuentran en un proyecto Visual Studio en tiempo de diseño.
>
> Para las aplicaciones en tiempo de ejecución, considere la posibilidad de usar plantillas de texto preprocesadas: vea Generación de texto en tiempo de ejecución [con plantillas de texto T4.](../modeling/run-time-text-generation-with-t4-text-templates.md)

Si la aplicación utiliza un conjunto de plantillas que se corrigen en tiempo de compilación, resulta más sencillo usar plantillas de texto preprocesadas. También puede usar ese enfoque si la aplicación se ejecutará en un equipo en el Visual Studio no está instalado. Para obtener más información, vea [Generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="execute-a-text-template-in-your-application"></a>Ejecutar una plantilla de texto en la aplicación

Para ejecutar una plantilla de texto, se llama al método ProcessTemplate de <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 La aplicación debe encontrar y proporcionar la plantilla y debe trabajar con el resultado.

 En el `host` parámetro , debe proporcionar una clase que implemente [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). El motor lo vuelve a llamar.

 El host debe poder registrar errores, resolver referencias a archivos de ensamblado e inclusión, proporciona un dominio de aplicación en el que se pueda ejecutar la plantilla, y llamar el procesador adecuado para cada directiva.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> se define en **Microsoft.VisualStudio.TextTemplating. \*.0.dll**, y [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) se define en **Microsoft.VisualStudio.TextTemplating.Interfaces. \*.0.dll**.

## <a name="in-this-section"></a>En esta sección
 [Tutorial: Crear un host de plantilla de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md) Muestra cómo crear un host de plantilla de texto personalizado que hace que la funcionalidad de la plantilla de texto esté disponible fuera Visual Studio.

## <a name="reference"></a>Referencia
 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

## <a name="related-sections"></a>Secciones relacionadas

- [El proceso de transformación Plantilla de](../modeling/the-text-template-transformation-process.md) texto describe cómo funciona la transformación de texto y qué partes puede personalizar.
- [La creación de procesadores de directivas de plantillas de texto T4](../modeling/creating-custom-t4-text-template-directive-processors.md) personalizadas proporciona información general sobre los procesadores de directivas de plantilla de texto.
