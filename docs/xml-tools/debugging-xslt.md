---
title: Formas de depurar el código XSLT
description: Obtenga información sobre cómo depurar código XSLT en Visual Studio mediante el depurador de XSLT para ejecutar paso a paso el código, establecer puntos de interrupción y ver los estados de ejecución de XSLT.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: a7d0f5a683a627999076969dbc9077ba03d65208
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948562"
---
# <a name="debugging-xslt"></a>Depuración de XSLT

Puede depurar el código XSLT en Visual Studio. El depurador de XSLT admite la definición de puntos de interrupción, la visualización de los estados de ejecución de XSLT, etc. El depurador de XSLT se puede utilizar para depurar una hoja de estilos XSLT o aplicaciones XSLT.

Puede ejecutar código de línea en línea yendo al código, recorriéndolo o saliendo de él. Los comandos para utilizar la funcionalidad de paso de código del depurador de XSLT son los mismos que en los demás depuradores de Visual Studio.

Una vez se haya iniciado la depuración, el depurador XSLT abre unas ventanas para mostrar el documento de entrada y la salida XSLT.

> [!NOTE]
> El depurador de XSLT solo está disponible en las ediciones Professional y Enterprise de Visual Studio.

## <a name="debug-from-the-xml-editor"></a>Depuración desde el editor XML

Puede iniciar el depurador si tiene una hoja de estilos o un archivo XML de entrada abierto en el editor. Esto le permite depurar mientras diseña la hoja de estilos.

1. Abra la hoja de estilos o el archivo XML en Visual Studio.

1. Seleccione **Iniciar depuración de XSLT** en el menú **XML** o presione **Alt**+**F5**.

## <a name="debug-from-an-app-that-uses-xslt"></a>Depuración desde una aplicación que usa XSLT

Puede ir al código XSLT mientras depura una aplicación. Cuando presiona **F11** en una llamada <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName>, el depurador puede ir al código XSLT.

> [!NOTE]
> No se puede ir al código XSLT desde la clase <xref:System.Xml.Xsl.XslTransform>. La clase <xref:System.Xml.Xsl.XslCompiledTransform> es el único procesador XSLT que admite la entrada al código XSLT durante la depuración.

### <a name="to-start-debugging-an-xslt-application"></a>Para iniciar la depuración de una aplicación XSLT

1. Al crear una instancia del objeto <xref:System.Xml.Xsl.XslCompiledTransform>, establezca el parámetro `enableDebug` a `true` en el código. Esto indica al procesador XSLT que cree información de depuración al compilar el código.

1. Presione **F11** para ir al código XSLT.

   La hoja de estilos XSLT se carga en una nueva ventana de documento y se inicia el depurador de XSLT.

   Como alternativa, puede agregar un punto de interrupción a la hoja de estilos y ejecutar la aplicación.

### <a name="example"></a>Ejemplo

A continuación se ofrece un ejemplo de un programa XSLT de C# que muestra cómo habilitar la depuración de XSLT.

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\below-average.xsl";
    private const string outputFile = @"c:\data\xsl_files\output.xml";

    static void Main(string[] args)
    {
      // Enable XSLT debugging.
      XslCompiledTransform xslt = new XslCompiledTransform(true);

      // Compile the style sheet.
      xslt.Load(stylesheet);

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="xslt-profiler"></a>Generador de perfiles XSLT

El [generador de perfiles XSLT](../xml-tools/xslt-profiler.md) es una herramienta que permite a los desarrolladores de software medir, evaluar y solucionar los problemas relacionados con el rendimiento en el código XSLT mediante la creación de informes de rendimiento de XSLT detallados. Para más información, consulte [Generar de perfiles XSLT](../xml-tools/xslt-profiler.md).

## <a name="see-also"></a>Vea también

- [Tutorial: Depuración de una hoja de estilos XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Primer vistazo al depurador de Visual Studio](../debugger/debugger-feature-tour.md)
- [Fundamentos de la depuración: Puntos de interrupción](../debugger/using-breakpoints.md)
