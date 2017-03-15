---
title: "Cómo:... con plantillas de texto | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1ac2509-0479-47eb-809c-1f171245d0b6
caps.latest.revision: 11
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: b874c9c259664f7f07e3266781909f74ece6e60a
ms.lasthandoff: 02/22/2017

---
# <a name="how-to--with-text-templates"></a>Cómo: ... con plantillas de texto
Plantillas de texto en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporcionan una forma útil de generar el texto de cualquier tipo. Puede utilizar plantillas de texto para generar texto en tiempo de ejecución como parte de la aplicación y en tiempo de diseño para generar parte del código de proyecto. En este tema se resume con más frecuencia más frecuentes "¿Cómo puedo...?" preguntas frecuentes.  
  
 En este tema, varias respuestas que van precedidas por viñetas son sugerencias alternativas.  
  
 Para obtener una introducción general a las plantillas de texto, leer [generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md).  
  
## <a name="how-to-"></a>Cómo...  
  
### <a name="generate-part-of-my-application-code"></a>Generar parte del código de mi aplicación  
 Tengo una configuración o *modelo* en un archivo o una base de datos. Una o varias partes del código dependen de ese modelo.  
  
-   Generar algunos de los archivos de código a partir de plantillas de texto. Para obtener más información, consulte [generación de código de tiempo de diseño mediante el uso de plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) y [¿qué es la mejor manera de empezar a escribir una plantilla?](#starting).  
  
### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Generar archivos en tiempo de ejecución, pasar datos a la plantilla  
 En tiempo de ejecución, la aplicación genera archivos de texto, como informes, que contienen una mezcla de texto estándar y los datos. Es necesario evitar la escritura de cientos de `write` instrucciones.  
  
-   Agregar una plantilla de texto en tiempo de ejecución al proyecto. Esta plantilla crea una clase en el código, que se puede crear instancias y se utiliza para generar texto. Puede pasar datos a ella en los parámetros del constructor. Para obtener más información, consulte [generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
-   Si desea generar a partir de plantillas que están disponibles en tiempo de ejecución, puede utilizar plantillas de texto estándar. Si está escribiendo un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensión, puede invocar el servicio de plantillas de texto. Para obtener más información, consulte [invocar la transformación de texto en una extensión de VS](../modeling/invoking-text-transformation-in-a-vs-extension.md). En otros contextos, puede utilizar el motor de plantillas de texto. Para obtener más información, consulte <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.</xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>  
  
     Utilice la \<#@parameter#> directiva para pasar parámetros a estas plantillas. Para obtener más información, consulte [directiva de parámetro T4](../modeling/t4-parameter-directive.md).  
  
### <a name="read-another-project-file-from-a-template"></a>Leer otro archivo de proyecto desde una plantilla  
 Para leer un archivo desde la misma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto como plantilla:  
  
-   Inserte `hostSpecific="true"` en la directiva `<#@template#>`.  
  
     En el código, utilice `this.Host.ResolvePath(filename)` para obtener la ruta de acceso completa del archivo.  
  
### <a name="invoke-methods-from-a-template"></a>Invocar métodos desde una plantilla  
 Si los métodos ya existen, por ejemplo, en la norma [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] clases:  
  
-   Utilice la \<#@assembly#> directiva al cargar el ensamblado y usar \<#@import#> para establecer el contexto de espacio de nombres. Para obtener más información, consulte [directiva de importación T4](../modeling/t4-import-directive.md).  
  
     Si usan el mismo conjunto de ensamblado y directivas de importación con frecuencia, considere la posibilidad de escribir un procesador de directivas. En cada plantilla, puede invocar el procesador de directivas que puede cargar los ensamblados y los archivos de modelo y establecer el contexto de espacio de nombres. Para obtener más información, consulte [procesadores de la directiva de plantilla de creación personalizada T4 texto](../modeling/creating-custom-t4-text-template-directive-processors.md).  
  
 Si se están escribiendo los métodos:  
  
-   Si está escribiendo una plantilla de texto en tiempo de ejecución, escribir una definición de clase parcial que tiene el mismo nombre que la plantilla de texto en tiempo de ejecución. Agregue los métodos adicionales en esta clase.  
  
-   Escribir un bloque de control de características de clase `<#+ ... #>` en que se pueden declarar métodos, propiedades y clases privadas. Cuando se compila la plantilla de texto, se transforma en una clase. Los bloques de control estándar `<#...#>` texto se transforman a un único método y los bloques de características de clase se insertan como miembros independientes. Para obtener más información, consulte [bloques de Control de plantilla de texto](../modeling/text-template-control-blocks.md).  
  
     Métodos definidos como características de clase también pueden incluir los bloques de texto incrustado.  
  
     Considere la posibilidad de colocar las características de clase en un archivo independiente que puede `<#@include#>` en uno o más archivos de plantilla.  
  
-   Escribir los métodos en un ensamblado independiente (biblioteca de clases) y llamarlos desde la plantilla. Utilice la `<#@assembly#>` directiva para cargar el ensamblado y `<#@import#>` para establecer el contexto de espacio de nombres. Tenga en cuenta que para volver a generar el ensamblado mientras realiza la depuración, es posible que deba detener y reiniciar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obtener más información, consulte [directivas de plantilla de texto T4](../modeling/t4-text-template-directives.md).  
  
### <a name="generate-many-files-from-one-model-schema"></a>Generar varios archivos de esquema de un modelo  
 Si a menudo genera archivos de modelos que tengan el mismo esquema XML o base de datos:  
  
-   Considere la posibilidad de escribir un procesador de directivas. Esto le permite reemplazar varias instrucciones de ensamblado y las instrucciones en cada plantilla con una sola directiva personalizada de importación. El procesador de directivas también puede cargar y analizar el archivo de modelo. Para obtener más información, consulte [procesadores de la directiva de plantilla de creación personalizada T4 texto](../modeling/creating-custom-t4-text-template-directive-processors.md).  
  
### <a name="generate-files-from-a-complex-model"></a>Generar archivos a partir de un modelo complejo  
  
-   Considere la creación de un lenguaje específico de dominio (DSL) para representar el modelo. Esto facilita mucho más fáciles de escribir las plantillas, porque se usan tipos y propiedades que reflejan los nombres de los elementos del modelo. No es necesario analizar el archivo o navegar por los nodos XML. Por ejemplo:  
  
     `foreach (Book book in this.Library) { ... }`  
  
     Para obtener más información, consulte [introducción con lenguajes específicos de dominio](../modeling/getting-started-with-domain-specific-languages.md) y [generar código desde un lenguaje específico de dominio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
### <a name="get-data-from-includevsprvscode-qualityincludesvsprvsmdmd"></a>Obtener datos[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
 Para utilizar servicios proporcionados en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], conjunto de la `hostSpecific` atributo y carga la `EnvDTE` ensamblado. Por ejemplo:  
  
```c#  
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
  
-   Para obtener más información, consulte [generación de código en un proceso de compilación](../modeling/code-generation-in-a-build-process.md).  
  
## <a name="more-general-questions"></a>Preguntas más generales  
  
###  <a name="a-namestartinga-what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a>¿Cuál es la mejor manera de empezar a escribir una plantilla de texto?  
  
1.  Escribir un ejemplo concreto del archivo generado.  
  
2.  Conviértalo en una plantilla de texto insertando la `<#@template #>` directiva y las directivas y código que son necesarias para cargar el archivo de entrada o el modelo.  
  
3.  Progresivamente puede reemplazar partes del archivo con la expresión y bloques de código.  
  
### <a name="what-is-a-model"></a>¿Qué es un "modelo"?  
  
-   La entrada leída por la plantilla. Podría ser en un archivo o en una base de datos. Puede ser XML, o un dibujo de Visio, un lenguaje específico de dominio (DSL) o un modelo UML, o podría ser texto sin formato. Se puede extenderse en varios archivos. Normalmente más de una plantilla lee un modelo.  
  
     El término "modelo de" implica que representa algún aspecto de su negocio más directa que el código de programa generado u otros archivos. Por ejemplo, podría representar el plan de una red de comunicaciones que se supervisará el software generado.  
  
### <a name="what-is-the-benefit-of-using-text-templates"></a>¿Cuál es la ventaja de usar plantillas de texto?  
 Normalmente, generar código varios u otros archivos de un modelo. El modelo representa los requisitos más directa que el código generado. Detalle de implementación se omite y se escribe en cuanto a los requisitos, en lugar de con el código. Cuando cambien los requisitos, como suelen hacerlo: puede actualizar el modelo más fácil y más confiable que las distintas partes del código de programa.  
  
 Por lo tanto, la generación de código es una herramienta valiosa desde la perspectiva de los métodos de desarrollo ágil.  
  
### <a name="what-best-practices-are-there-for-text-templates"></a>¿Qué "procedimientos recomendados" existen para plantillas de texto?  
  
-   Para obtener más información, consulte [directrices para escribir plantillas de texto T4](../modeling/guidelines-for-writing-t4-text-templates.md).  
  
### <a name="what-is-t4"></a>¿Qué es "T4"?  
  
-   Otro nombre para el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] capacidades de plantilla de texto se describe aquí. La versión anterior, que no se ha publicado, era una abreviatura de "Transformación de plantillas de texto".

