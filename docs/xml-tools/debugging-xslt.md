---
title: Maneras de depurar código XSLT
ms.date: 03/05/2019
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: bb358efb711211d58525afb8d30d5cb4cad6b2e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646073"
---
# <a name="debugging-xslt"></a>Depuración de XSLT

Puede depurar código XSLT en Visual Studio. El depurador de XSLT permite establecer puntos de interrupción, ver Estados de ejecución XSLT, etc. El depurador de XSLT se puede usar para depurar hojas de estilos XSLT o aplicaciones XSLT.

Puede ejecutar código de línea en línea depurando paso a paso por instrucciones, pasando por el código. Los comandos para usar la funcionalidad de paso de código del depurador de XSLT son los mismos que los de los demás depuradores de Visual Studio.

Una vez se haya iniciado la depuración, el depurador XSLT abre unas ventanas para mostrar el documento de entrada y la salida XSLT.

> [!NOTE]
> El depurador de XSLT solo está disponible en las ediciones Professional y Enterprise de Visual Studio.

## <a name="debug-from-the-xml-editor"></a>Depurar desde el editor XML

Puede iniciar el depurador de si tiene una hoja de estilos o un archivo XML de entrada abierto en el editor de. Esto le permite depurar mientras está diseñando la hoja de estilos.

1. Abra la hoja de estilos o el archivo XML en Visual Studio.

1. Seleccione **iniciar depuración XSLT** en el menú **XML** o presione **Alt** +**F5**.

## <a name="debug-from-an-app-that-uses-xslt"></a>Depurar desde una aplicación que usa XSLT

Puede entrar en XSLT durante la depuración de una aplicación. Al presionar **F11** en una llamada <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName>, el depurador puede entrar en el código XSLT.

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
      xslt.Load(stylesheet)

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="xslt-profiler"></a>Generador de perfiles XSLT

El [generador de perfiles XSLT](../xml-tools/xslt-profiler.md) es una herramienta que permite a los desarrolladores medir, evaluar y solucionar problemas relacionados con el rendimiento en el código XSLT mediante la creación de informes de rendimiento XSLT detallados. Para obtener más información, vea [generador de perfiles XSLT](../xml-tools/xslt-profiler.md).

## <a name="see-also"></a>Vea también

- [Tutorial: depurar una hoja de estilos XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Primer vistazo al depurador de Visual Studio](../debugger/debugger-feature-tour.md)
- [Fundamentos de la depuración: puntos de interrupción](../debugger/using-breakpoints.md)
