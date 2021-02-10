---
title: Procesar las plantillas de texto mediante un host personalizado
description: Obtenga información sobre que el proceso de transformación de plantillas de texto toma un archivo de plantilla de texto como entrada y genera un archivo de texto como salida.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b1a4e4c2177e388db1de0b42fe10d92daa1a3e67
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934915"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Procesar plantillas de texto mediante un host personalizado

El proceso de *transformación de plantillas de texto* toma un archivo de plantilla de *texto* como entrada y genera un archivo de texto como salida. Puede llamar al motor de transformación de texto desde una extensión de Visual Studio o desde una aplicación independiente que se ejecuta en un equipo en el que está instalado Visual Studio. Sin embargo, debe proporcionar un *host de plantillas de texto*. Esta clase conecta la plantilla al entorno, localizando recursos como ensamblados y archivos de inclusión, y trabajando con los mensajes de error y resultado.

> [!TIP]
> Si está escribiendo un paquete o una extensión que se ejecutará en Visual Studio, considere la posibilidad de usar el servicio de plantillas de texto, en lugar de escribir su propio host. Para obtener más información, consulte [invocar la transformación de texto en una extensión de vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> No se recomienda utilizar las transformaciones de plantilla de texto en aplicaciones de servidor. No se recomienda utilizar las transformaciones de plantilla de texto excepto en un subproceso único. Esto se debe a que el motor de plantillas de texto vuelve a utilizar un AppDomain único para traducir, compilar y ejecutar plantillas. El código traducido no es seguro para subprocesos. El motor está diseñado para procesar archivos en serie, tal como están en un proyecto de Visual Studio en tiempo de diseño.
>
> En el caso de las aplicaciones en tiempo de ejecución, considere la posibilidad de usar plantillas de texto preprocesadas: vea [generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

Si la aplicación utiliza un conjunto de plantillas que se corrigen en tiempo de compilación, resulta más sencillo usar plantillas de texto preprocesadas. También puede usar este enfoque si la aplicación se ejecutará en una máquina en la que Visual Studio no esté instalado. Para obtener más información, vea [Generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="execute-a-text-template-in-your-application"></a>Ejecución de una plantilla de texto en la aplicación

Para ejecutar una plantilla de texto, se llama al método ProcessTemplate de <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 La aplicación debe encontrar y proporcionar la plantilla y debe trabajar con el resultado.

 En el `host` parámetro, debe proporcionar una clase que implemente [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). El motor lo vuelve a llamar.

 El host debe poder registrar errores, resolver referencias a archivos de ensamblado e inclusión, proporciona un dominio de aplicación en el que se pueda ejecutar la plantilla, y llamar el procesador adecuado para cada directiva.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> se define en **Microsoft. VisualStudio. TextTemplating. \*.0.dll** y [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) se define en **Microsoft. visualstudio. TextTemplating. interfaces. \*.0.dll**.

## <a name="in-this-section"></a>En esta sección
 [Tutorial: crear un host de plantilla de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md) Muestra cómo crear un host de plantilla de texto personalizado que hace que la funcionalidad de la plantilla de texto esté disponible fuera de Visual Studio.

## <a name="reference"></a>Referencia
 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

## <a name="related-sections"></a>Secciones relacionadas

- [El proceso de transformación de plantillas de texto](../modeling/the-text-template-transformation-process.md) describe cómo funciona la transformación de texto y qué partes se pueden personalizar.
- [Creación de procesadores de directivas de plantilla de texto T4 personalizadas](../modeling/creating-custom-t4-text-template-directive-processors.md) proporciona una introducción a los procesadores de directivas de plantilla de texto.
