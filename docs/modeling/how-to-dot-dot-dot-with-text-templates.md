---
title: 'Cómo: ... con plantillas de texto'
description: Obtenga información sobre las respuestas a preguntas comunes que se encuentran al usar plantillas de texto para generar texto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0c65a7ba67c3972620b3d589188e233827a12ffd
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387273"
---
# <a name="how-to--with-text-templates"></a>Cómo: ... con plantillas de texto
Las plantillas de Visual Studio proporcionan una manera útil de generar texto de cualquier tipo. Puede usar plantillas de texto para generar texto en tiempo de ejecución como parte de la aplicación y en tiempo de diseño para generar parte del código del proyecto. En este tema se resumen las preguntas más frecuentes Cómo ...?" Preguntas.

 En este tema, varias respuestas precedidas por viñetas son sugerencias alternativas.

 Para obtener una introducción general a las plantillas de texto, lea [Generación de código y Plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="how-to-"></a>Cómo...

### <a name="generate-part-of-my-application-code"></a>Generación de parte del código de la aplicación
 Tengo una configuración o un *modelo en* un archivo o una base de datos. Una o varias partes de mi código dependen de ese modelo.

- Genere algunos de los archivos de código a partir de plantillas de texto. Para obtener más información, vea Generación de código en tiempo de diseño mediante plantillas de [texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) y ¿Cuál es la mejor manera de [empezar a escribir una plantilla?](#starting).

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Generación de archivos en tiempo de ejecución, paso de datos a la plantilla
 En tiempo de ejecución, mi aplicación genera archivos de texto, como informes, que contienen una mezcla de texto y datos estándar. Quiero evitar escribir cientos `write` de instrucciones.

- Agregue una plantilla de texto en tiempo de ejecución al proyecto. Esta plantilla crea una clase en el código, que puede crear instancias y usar para generar texto. Puede pasar datos a él en los parámetros del constructor. Para obtener más información, vea [Generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

- Si desea generar a partir de plantillas que solo están disponibles en tiempo de ejecución, puede usar plantillas de texto estándar. Si está escribiendo una extensión Visual Studio, puede invocar el servicio de templating de texto. Para obtener más información, vea [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md). En otros contextos, puede usar el motor de templaciones de texto. Para más información, consulte <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.

     Use la \<#@parameter#> directiva para pasar parámetros a estas plantillas. Para obtener más información, vea [T4 Parameter Directive](../modeling/t4-parameter-directive.md).

### <a name="read-another-project-file-from-a-template"></a>Leer otro archivo de proyecto de una plantilla
 Para leer un archivo del mismo proyecto Visual Studio que la plantilla:

- Inserte `hostSpecific="true"` en la directiva `<#@template#>`.

     En el código, use `this.Host.ResolvePath(filename)` para obtener la ruta de acceso completa del archivo.

### <a name="invoke-methods-from-a-template"></a>Invocación de métodos desde una plantilla

Si los métodos ya existen, por ejemplo, en clases de .NET:

- Use la \<#@assembly#> directiva para cargar el ensamblado y use para establecer el contexto del espacio de \<#@import#> nombres. Para obtener más información, vea [T4 Import Directive](../modeling/t4-import-directive.md).

   Si usa con frecuencia el mismo conjunto de directivas de ensamblado e importación, considere la posibilidad de escribir un procesador de directivas. En cada plantilla, puede invocar el procesador de directivas, que puede cargar los ensamblados y los archivos de modelo y establecer el contexto del espacio de nombres. Para obtener más información, vea [Creating Custom T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md).

Si está escribiendo los métodos usted mismo:

- Si va a escribir una plantilla de texto en tiempo de ejecución, escriba una definición de clase parcial que tenga el mismo nombre que la plantilla de texto en tiempo de ejecución. Agregue los métodos adicionales a esta clase.

- Escriba un bloque de control de características de clase `<#+ ... #>` en el que puede declarar métodos, propiedades y clases privadas. Cuando se compila la plantilla de texto, se transforma en una clase . Los bloques de control estándar y el texto se transforman en un único método y los bloques de características `<#...#>` de clase se insertan como miembros independientes. Para obtener más información, vea [Text Template Control Blocks](../modeling/text-template-control-blocks.md).

   Los métodos definidos como características de clase también pueden incluir bloques de texto incrustados.

   Considere la posibilidad de colocar características de clase en un archivo independiente que pueda `<#@include#>` en uno o varios archivos de plantilla.

- Escriba los métodos en un ensamblado independiente (biblioteca de clases) y llámelos desde la plantilla. Use la `<#@assembly#>` directiva para cargar el ensamblado y para establecer el contexto del espacio de `<#@import#>` nombres. Tenga en cuenta que para volver a generar el ensamblado mientras lo depura, es posible que tenga que detener y reiniciar Visual Studio. Para obtener más información, vea [Directivas de plantilla de texto T4.](../modeling/t4-text-template-directives.md)

### <a name="generate-many-files-from-one-model-schema"></a>Generar muchos archivos a partir de un esquema de modelo
 Si a menudo genera archivos a partir de modelos que tienen el mismo esquema XML o de base de datos:

- Considere la posibilidad de escribir un procesador de directivas. Esto le permite reemplazar varias instrucciones de ensamblado e instrucciones de importación en cada plantilla por una sola directiva personalizada. El procesador de directivas también puede cargar y analizar el archivo de modelo. Para obtener más información, vea [Creating Custom T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md).

### <a name="generate-files-from-a-complex-model"></a>Generación de archivos a partir de un modelo complejo

- Considere la posibilidad de crear un lenguaje específico de dominio (DSL) para representar el modelo. Esto facilita mucho la escritura de las plantillas, ya que se usan tipos y propiedades que reflejan los nombres de los elementos del modelo. No es necesario analizar el archivo ni navegar por los nodos XML. Por ejemplo:

     `foreach (Book book in this.Library) { ... }`

     Para obtener más información, [vea Tareas iniciales con Domain-Specific y](../modeling/getting-started-with-domain-specific-languages.md) Generar código a partir de un Domain-Specific lenguaje [.](../modeling/generating-code-from-a-domain-specific-language.md)

### <a name="get-data-from-visual-studio"></a>Obtener datos de Visual Studio
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

### <a name="execute-text-templates-in-the-build-process"></a>Ejecución de plantillas de texto en el proceso de compilación

- Para obtener más información, vea [Generación de código en un proceso de compilación.](../modeling/code-generation-in-a-build-process.md)

## <a name="more-general-questions"></a>Preguntas más generales

### <a name="what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a> ¿Cuál es la mejor manera de empezar a escribir una plantilla de texto?

1. Escriba un ejemplo específico del archivo generado.

2. Para convertirla en una plantilla de texto, inserte la directiva y las directivas y el código necesarios para cargar el archivo o modelo `<#@template #>` de entrada.

3. Reemplace progresivamente partes del archivo por bloques de expresión y código.

### <a name="what-is-a-model"></a>¿Qué es un “modelo”?

- La entrada leída por la plantilla. Podría estar en un archivo o en una base de datos. Puede ser XML, un dibujo de Visio, un lenguaje específico de dominio (DSL) o un modelo UML, o podría ser texto sin formato. Se podría propagar entre varios archivos. Normalmente, más de una plantilla lee un modelo.

     La implicación del término "modelo" es que representa algún aspecto de su negocio más directamente que el código de programa generado u otros archivos. Por ejemplo, podría representar el plan de una red de comunicaciones que el software generado supervisará.

### <a name="what-is-the-benefit-of-using-text-templates"></a>¿Cuál es la ventaja de usar plantillas de texto?
 Normalmente, se generan varios archivos de código u otros a partir de un modelo. El modelo representa los requisitos más directamente que el código generado. Omite los detalles de implementación y se escribe en términos de los requisitos, en lugar del código. Cuando los requisitos cambian (como suelen hacer), puede actualizar el modelo de forma más fácil y confiable que las distintas partes del código del programa.

 Por lo tanto, la generación de código es una herramienta valiosa desde la perspectiva de los métodos de desarrollo ágiles.

### <a name="what-best-practices-are-there-for-text-templates"></a>¿Qué "procedimientos recomendados" existen para las plantillas de texto?

- Para obtener más información, vea [Directrices para escribir plantillas de texto T4.](../modeling/guidelines-for-writing-t4-text-templates.md)

### <a name="what-is-t4"></a>¿Qué es "T4"?

- Otro nombre para las funcionalidades Visual Studio plantilla de texto que se describen aquí. La versión anterior, que no se publicó, era una abreviatura de "Text Template Transformation".
