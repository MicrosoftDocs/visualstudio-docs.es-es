---
title: Generación de código y plantillas de texto T4
description: Aprenda cómo una plantilla de texto T4 es una mezcla de bloques de texto y lógica de control que puede generar un archivo de texto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 871aa20fe4fc95ea1641b7f478cb9b01d71284aa
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363580"
---
# <a name="code-generation-and-t4-text-templates"></a>Generación de código y plantillas de texto T4

En Visual Studio, una *plantilla de texto T4* es una mezcla de bloques de texto y lógica de control que puede generar un archivo de texto. La lógica de control se escribe en forma de fragmentos de código de programa en [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. En Visual Studio 2015 Update 2 y versiones posteriores, puede usar las características de la versión 6.0 de C# en las directivas de plantillas T4. El archivo generado puede ser texto de cualquier tipo, como una página web, un archivo de recursos o código fuente de programa en cualquier lenguaje.

Hay dos tipos de plantillas de texto T4: de tiempo de ejecución y de tiempo de diseño.

## <a name="run-time-t4-text-templates"></a>Plantillas de texto T4 de tiempo de ejecución

También denominadas plantillas "preprocesadas", las plantillas de tiempo de ejecución se ejecutan en la aplicación para generar cadenas de texto, normalmente como parte de su salida. Por ejemplo, podría crear una plantilla para definir una página HTML:

```
<html><body>
 The date and time now is: <#= DateTime.Now #>
</body></html>
```

Observe que la plantilla es similar a la salida generada. La similitud de la plantilla con la salida resultante le ayudará a evitar errores cuando quiera cambiarla.

Además, la plantilla contiene fragmentos de código de programa. Puede usar estos fragmentos para repetir secciones de texto, crear secciones condicionales y mostrar datos de la aplicación.

Para generar la salida, la aplicación llama a una función generada por la plantilla. Por ejemplo:

```csharp
string webResponseText = new MyTemplate().TransformText();
```

La aplicación se puede ejecutar en un equipo que no tenga Visual Studio instalado.

Para crear una plantilla en tiempo de ejecución, agregue un archivo de **plantilla de texto preprocesada** al proyecto. Como alternativa, puede agregar un archivo de texto sin formato y establecer su propiedad **Herramienta personalizada** en **TextTemplatingFilePreprocessor**.

Para obtener más información, vea [Generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md). Para obtener más información sobre las sintaxis de las plantillas, vea [Escritura de una plantilla de texto T4](../modeling/writing-a-t4-text-template.md).

## <a name="design-time-t4-text-templates"></a>Plantillas de texto T4 de tiempo de diseño

Las plantillas de tiempo de diseño definen la parte del código fuente y otros recursos de la aplicación. Por lo general, se usan varias plantillas que leen los datos de un único archivo de entrada o una única base de datos, y se generan algunos de los archivos *.cs*, *.vb* u otros de código fuente. Cada plantilla genera un archivo. Se ejecutan dentro de Visual Studio o MSBuild.

Por ejemplo, los datos de entrada podrían ser un archivo XML de datos de configuración. Siempre que edite el archivo XML durante el desarrollo, las plantillas de texto regeneran parte del código de aplicación. Una de las plantillas podría parecerse al siguiente ejemplo:

```
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}
```

En función de los valores del archivo XML, el archivo *.cs* generado será similar al siguiente:

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

A modo de ejemplo, la entrada podría ser un diagrama del flujo de trabajo de una actividad profesional. Si los usuarios cambian su flujo de trabajo profesional, o si empieza a trabajar con nuevos usuarios que tienen un flujo de trabajo diferente, es fácil regenerar el código para ajustarlo al nuevo modelo.

Las plantillas en tiempo de diseño permiten cambiar la configuración de manera más rápida y confiable cuando cambian los requisitos. Normalmente, la entrada se define en términos de requisitos empresariales, como en el ejemplo de flujo de trabajo. Esto permite analizar más fácilmente los cambios con los usuarios. Por tanto, las plantillas en tiempo de diseño son una herramienta útil en un proceso de desarrollo ágil.

Para crear una plantilla en tiempo de diseño, agregue un archivo de **plantilla de texto** al proyecto. Como alternativa, puede agregar un archivo de texto sin formato y establecer su propiedad **Herramienta personalizada** en **TextTemplatingFileGenerator**.

Para obtener más información, vea [Generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Para obtener más información sobre las sintaxis de las plantillas, vea [Escritura de una plantilla de texto T4](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> El término *modelo* se usa a veces para describir los datos que una o varias plantillas leen. El modelo puede tener cualquier formato y estar en cualquier tipo de archivo o base de datos. No tiene que ser un modelo UML ni un modelo de lenguaje específico de dominio. El término "modelo" solo indica que los datos se pueden definir en términos de conceptos de negocios, en lugar de parecerse al código.

El característica de transformación de plantillas de texto de denomina *T4*.

## <a name="see-also"></a>Consulte también

- [Generación de código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md)
