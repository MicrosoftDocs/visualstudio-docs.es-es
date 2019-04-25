---
title: Maneras de depurar el código XSLT
ms.date: 03/05/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 23e108e476bfa9cb3ce699a16c77eb3520ed4785
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526391"
---
# <a name="debugging-xslt"></a>Depuración de XSLT

Puede depurar el código XSLT en Visual Studio. La transformación XSLT se admite establecer puntos de interrupción, ver estados de ejecución de XSLT del depurador y así sucesivamente. El depurador de XSLT se puede usar para depurar hojas de estilos XSLT o las aplicaciones XSLT.

Puede ejecutar una línea de código en un tiempo de ejecución paso a paso, saltar o ejecutar paso a paso el código. Los comandos para usar la funcionalidad de paso a paso el código del depurador XSLT son que los mismos que para el Visual Studio depuradores.

Una vez se haya iniciado la depuración, el depurador XSLT abre unas ventanas para mostrar el documento de entrada y la salida XSLT.

> [!NOTE]
> El depurador de XSLT solo está disponible en la edición Enterprise de Visual Studio.

## <a name="debug-from-the-xml-editor"></a>Depurar desde el editor XML

Puede iniciar al depurador cuando haya una hoja de estilos o un archivo XML de entrada abierto en el editor. Esto le permite depurar mientras diseña la hoja de estilos.

1. Abra la hoja de estilos o archivo XML en Visual Studio.

1. Seleccione **iniciar la depuración de XSLT** desde el **XML** menús o presione **Alt**+**F5**.

## <a name="debug-from-an-app-that-uses-xslt"></a>Depurar desde una aplicación que utiliza XSLT

Puede ir al código XSLT mientras depura una aplicación. Al presionar **F11** en un <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> llamada, el depurador puede ir al código XSLT.

> [!NOTE]
> No se puede ir al código XSLT desde la clase <xref:System.Xml.Xsl.XslTransform>. La clase <xref:System.Xml.Xsl.XslCompiledTransform> es el único procesador XSLT que admite la entrada al código XSLT durante la depuración.

### <a name="to-start-debugging-an-xslt-application"></a>Para iniciar la depuración de una aplicación XSLT

1. Al crear una instancia del objeto <xref:System.Xml.Xsl.XslCompiledTransform>, establezca el parámetro `enableDebug` a `true` en el código. Esto indica al procesador XSLT que cree información de depuración al compilar el código.

1. Presione **F11** para ir al código XSLT.

   La hoja de estilos XSLT se carga en una nueva ventana de documento y se inicia el depurador de XSLT.

   Como alternativa, puede agregar un punto de interrupción a la hoja de estilos y ejecutar la aplicación.

### <a name="example"></a>Ejemplo

A continuación se ofrece un ejemplo de un programa XSLT de C#  que muestra cómo habilitar la depuración de XSLT.

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

El [generador de perfiles XSLT](../xml-tools/xslt-profiler.md) es una herramienta que permite a los desarrolladores medir, evaluar y abordar problemas relacionados con el rendimiento en el código XSLT mediante la creación de informes de rendimiento de XSLT detallados. Para obtener más información, consulte [generador de perfiles XSLT](../xml-tools/xslt-profiler.md).

## <a name="see-also"></a>Vea también

- [Tutorial: Depurar una hoja de estilos XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Primer vistazo al depurador de Visual Studio](../debugger/debugger-feature-tour.md)
- [Fundamentos de la depuración: Puntos de interrupción](../debugger/using-breakpoints.md)