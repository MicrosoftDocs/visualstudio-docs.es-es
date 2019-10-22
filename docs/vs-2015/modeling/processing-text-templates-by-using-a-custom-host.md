---
title: Procesamiento de plantillas de texto mediante un host personalizado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
ms.assetid: affa3296-854d-47d6-9685-285f6d9ba5dc
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 71f18fbbf9f2d5c587c2cd0961c6625467f4f298
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652452"
---
# <a name="processing-text-templates-by-using-a-custom-host"></a>Procesar las plantillas de texto mediante un host personalizado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El proceso de *transformación de plantillas de texto* toma un archivo de plantilla de *texto* como entrada y genera un archivo de texto como salida. Puede llamar al motor de transformación de texto desde una extensión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o desde una aplicación independiente que se ejecuta en un equipo donde está instalado [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Sin embargo, debe proporcionar un *host de plantillas de texto*. Esta clase conecta la plantilla al entorno, localizando recursos como ensamblados y archivos de inclusión, y trabajando con los mensajes de error y resultado.

> [!TIP]
> Si está escribiendo una extensión o paquete que se ejecutará con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], considere la posibilidad de utilizar el servicio de plantillas de texto, en lugar de escribir su propio host. Para obtener más información, consulte [invocar la transformación de texto en una extensión de vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> No se recomienda utilizar las transformaciones de plantilla de texto en aplicaciones de servidor. No se recomienda utilizar las transformaciones de plantilla de texto excepto en un subproceso único. Esto se debe a que el motor de plantillas de texto vuelve a utilizar un AppDomain único para traducir, compilar y ejecutar plantillas. El código traducido no es seguro para subprocesos. El motor está diseñado para procesar archivos en serie, como se encuentran en un proyecto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en tiempo de diseño.
>
> En el caso de las aplicaciones en tiempo de ejecución, considere la posibilidad de usar plantillas de texto preprocesadas: vea [generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Si la aplicación utiliza un conjunto de plantillas que se corrigen en tiempo de compilación, resulta más sencillo usar plantillas de texto preprocesadas. También puede utilizar ese enfoque si la aplicación se va a ejecutar en un equipo donde no está instalado [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Para obtener más información, vea [generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="executing-a-text-template-in-your-application"></a>Ejecutar una plantilla de texto en la aplicación
 Para ejecutar una plantilla de texto, se llama al método ProcessTemplate de <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:

```
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 La aplicación debe encontrar y proporcionar la plantilla y debe trabajar con el resultado.

 En el parámetro `host`, debe proporcionar una clase que implemente [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). El motor lo vuelve a llamar.

 El host debe poder registrar errores, resolver referencias a archivos de ensamblado e inclusión, proporciona un dominio de aplicación en el que se pueda ejecutar la plantilla, y llamar el procesador adecuado para cada directiva.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> se define en **Microsoft. VisualStudio. TextTemplating. \*,0. dll**y [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) se define en **Microsoft. VisualStudio. TextTemplating. interfaces. \*.0. dll**.

## <a name="in-this-section"></a>En esta sección
 [Tutorial: crear un host de plantilla de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md) Muestra cómo crear un host de plantilla de texto personalizado que hace que la funcionalidad de la plantilla de texto esté disponible fuera de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="reference"></a>Referencia
 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

## <a name="related-sections"></a>Secciones relacionadas
 [El proceso de transformación de plantillas de texto](../modeling/the-text-template-transformation-process.md) Describe cómo funciona la transformación de texto y qué partes se pueden personalizar.

 [Crear procesadores de directivas de plantillas de texto T4 personalizadas](../modeling/creating-custom-t4-text-template-directive-processors.md) Proporciona información general de los procesadores de directivas de plantilla de texto.
