---
title: 'Cómo: ... con plantillas de texto'
description: Obtenga información acerca de las respuestas a preguntas comunes que se encuentran al usar plantillas de texto para generar texto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50844ce8c6943fcf6b2a0b91c7fd2cfcb6184094
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363190"
---
# <a name="how-to--with-text-templates"></a>Cómo: ... con plantillas de texto
Las plantillas de texto de Visual Studio proporcionan una manera útil de generar texto de cualquier tipo. Puede usar plantillas de texto para generar texto en tiempo de ejecución como parte de la aplicación y en tiempo de diseño para generar parte del código del proyecto. En este tema se resume el "Cómo...?" más frecuente. las.

 En este tema, varias respuestas precedidas de las viñetas son sugerencias alternativas.

 Para obtener una introducción general a las plantillas de texto, lea [generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="how-to-"></a>Cómo...

### <a name="generate-part-of-my-application-code"></a>Generar parte del código de mi aplicación
 Tengo una configuración o un *modelo* en un archivo o en una base de datos. Una o varias partes de mi código dependen de ese modelo.

- Genere algunos de los archivos de código a partir de plantillas de texto. Para obtener más información, vea [generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) y [¿cuál es la mejor manera de empezar a escribir una plantilla?](#starting).

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Generar archivos en tiempo de ejecución, pasar datos a la plantilla
 En tiempo de ejecución, mi aplicación genera archivos de texto, como informes, que contienen una mezcla de texto y datos estándar. Deseo evitar escribir cientos de `write` instrucciones.

- Agregue una plantilla de texto en tiempo de ejecución al proyecto. Esta plantilla crea una clase en el código, en la que se pueden crear instancias y usar para generar texto. Puede pasar datos a él en los parámetros del constructor. Para obtener más información, vea [Generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

- Si desea generar a partir de plantillas que solo están disponibles en tiempo de ejecución, puede usar plantillas de texto estándar. Si está escribiendo una extensión de Visual Studio, puede invocar el servicio de plantillas de texto. Para obtener más información, consulte [invocar la transformación de texto en una extensión de vs](../modeling/invoking-text-transformation-in-a-vs-extension.md). En otros contextos, puede usar el motor de plantillas de texto. Para obtener más información, vea <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.

     Use la \<#@parameter#> Directiva para pasar parámetros a estas plantillas. Para obtener más información, consulte [la Directiva de parámetros T4](../modeling/t4-parameter-directive.md).

### <a name="read-another-project-file-from-a-template"></a>Leer otro archivo de proyecto de una plantilla
 Para leer un archivo del mismo proyecto de Visual Studio que la plantilla:

- Inserte `hostSpecific="true"` en la directiva `<#@template#>`.

     En el código, use `this.Host.ResolvePath(filename)` para obtener la ruta de acceso completa del archivo.

### <a name="invoke-methods-from-a-template"></a>Invocar métodos desde una plantilla

Si los métodos ya existen, por ejemplo, en las clases de .NET:

- Use la \<#@assembly#> Directiva para cargar el ensamblado y use \<#@import#> para establecer el contexto del espacio de nombres. Para obtener más información, vea [Directiva de importación T4](../modeling/t4-import-directive.md).

   Si usa con frecuencia el mismo conjunto de directivas de ensamblado e importación, considere la posibilidad de escribir un procesador de directivas. En cada plantilla, puede invocar el procesador de directivas, que puede cargar los ensamblados y los archivos del modelo y establecer el contexto del espacio de nombres. Para obtener más información, vea [crear procesadores de directivas de plantillas de texto T4 personalizadas](../modeling/creating-custom-t4-text-template-directive-processors.md).

Si va a escribir los métodos usted mismo:

- Si está escribiendo una plantilla de texto en tiempo de ejecución, escriba una definición de clase parcial que tenga el mismo nombre que la plantilla de texto en tiempo de ejecución. Agregue los métodos adicionales a esta clase.

- Escriba un bloque `<#+ ... #>` de control de características de clase en el que pueda declarar métodos, propiedades y clases privadas. Cuando se compila la plantilla de texto, se transforma en una clase. Los bloques de control estándar `<#...#>` y el texto se transforman en un único método, y los bloques de características de clase se insertan como miembros independientes. Para obtener más información, vea [bloques de control de plantillas de texto](../modeling/text-template-control-blocks.md).

   Los métodos definidos como características de clase también pueden incluir bloques de texto incrustados.

   Considere la posibilidad de colocar características de clase en un archivo independiente que puede incluir `<#@include#>` en uno o varios archivos de plantilla.

- Escriba los métodos en un ensamblado independiente (biblioteca de clases) y llámelos desde la plantilla. Use la `<#@assembly#>` Directiva para cargar el ensamblado y `<#@import#>` para establecer el contexto del espacio de nombres. Tenga en cuenta que, para volver a generar el ensamblado durante la depuración, es posible que tenga que detener y reiniciar Visual Studio. Para obtener más información, vea [directivas de plantilla de texto T4](../modeling/t4-text-template-directives.md).

### <a name="generate-many-files-from-one-model-schema"></a>Generar muchos archivos a partir de un esquema de modelo
 Si suele generar archivos a partir de modelos que tienen el mismo esquema XML o de base de datos:

- Considere la posibilidad de escribir un procesador de directivas. Esto permite reemplazar varias instrucciones de ensamblado e importar instrucciones en cada plantilla con una única directiva personalizada. El procesador de directivas también puede cargar y analizar el archivo de modelo. Para obtener más información, vea [crear procesadores de directivas de plantillas de texto T4 personalizadas](../modeling/creating-custom-t4-text-template-directive-processors.md).

### <a name="generate-files-from-a-complex-model"></a>Generar archivos a partir de un modelo complejo

- Considere la posibilidad de crear un lenguaje específico de dominio (DSL) para representar el modelo. Esto hace que sea mucho más fácil escribir las plantillas, ya que se usan tipos y propiedades que reflejan los nombres de los elementos del modelo. No es necesario analizar el archivo ni navegar por los nodos XML. Por ejemplo:

     `foreach (Book book in this.Library) { ... }`

     Para obtener más información, vea [Introducción con lenguajes de Domain-Specific](../modeling/getting-started-with-domain-specific-languages.md) y [generar código a partir de un lenguaje de Domain-Specific](../modeling/generating-code-from-a-domain-specific-language.md).

### <a name="get-data-from-visual-studio"></a>Obtención de datos de Visual Studio
 Para usar los servicios proporcionados en Visual Studio, establezca el `hostSpecific` atributo y cargue el `EnvDTE` ensamblado. Por ejemplo:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>
```

### <a name="execute-text-templates-in-the-build-process"></a>Ejecutar plantillas de texto en el proceso de compilación

- Para obtener más información, vea [generación de código en un proceso de compilación](../modeling/code-generation-in-a-build-process.md).

## <a name="more-general-questions"></a>Preguntas más generales

### <a name="what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a> ¿Cuál es la mejor manera de empezar a escribir una plantilla de texto?

1. Escriba un ejemplo concreto del archivo generado.

2. Convertirlo en una plantilla de texto insertando la `<#@template #>` Directiva y las directivas y el código necesarios para cargar el archivo de entrada o el modelo.

3. Reemplace progresivamente partes del archivo por bloques de expresiones y de código.

### <a name="what-is-a-model"></a>¿Qué es un “modelo”?

- La entrada leída por la plantilla. Podría estar en un archivo o en una base de datos. Puede tratarse de XML, de un dibujo de Visio o de un lenguaje específico de dominio (DSL), o de un modelo UML, o de texto sin formato. Podría distribuirse en varios archivos. Normalmente, más de una plantilla Lee un modelo.

     La implicación del término "modelo" es que representa un aspecto de su empresa más directamente que el código de programa generado u otros archivos. Por ejemplo, podría representar el plan de una red de comunicaciones que el software generado supervisará.

### <a name="what-is-the-benefit-of-using-text-templates"></a>¿Cuál es la ventaja de usar plantillas de texto?
 Normalmente, se generan varios códigos u otros archivos a partir de un modelo. El modelo representa los requisitos más directamente que el código generado. Omite los detalles de la implementación y se escribe en función de los requisitos, en lugar del código. Cuando cambien los requisitos, como lo hacen normalmente, puede actualizar el modelo de forma más sencilla y confiable que las distintas partes del código del programa.

 La generación de código es, por lo tanto, una valiosa herramienta desde la perspectiva de los métodos de desarrollo ágiles.

### <a name="what-best-practices-are-there-for-text-templates"></a>¿Qué procedimientos recomendados hay para las plantillas de texto?

- Para obtener más información, vea [instrucciones para escribir plantillas de texto T4](../modeling/guidelines-for-writing-t4-text-templates.md).

### <a name="what-is-t4"></a>¿Qué es "T4"?

- Otro nombre para las funciones de la plantilla de texto de Visual Studio que se describen aquí. La versión anterior, que no se publicó, era una abreviatura de "transformación de plantilla de texto".
