---
title: Instrucciones para escribir plantillas de texto T4 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: accf32ad313cbbfe11c2e85fdfe3101ab428c4a4
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Instrucciones para escribir plantillas de texto T4
Estas directrices generales que pueden resultar útiles si va a generar código de programa u otros recursos de la aplicación en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. No son fijas reglas.  
  
## <a name="guidelines-for-design-time-t4-templates"></a>Directrices para plantillas T4 en tiempo de diseño  
 Plantillas T4 en tiempo de diseño son plantillas que se va a generar código en su [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto en tiempo de diseño. Para obtener más información, consulte [generación de código en tiempo de diseño mediante el uso de plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 Genere aspectos variables de la aplicación.  
 Generación de código es muy útil para los aspectos de la aplicación que puede cambiar durante el proyecto o cambiará entre diferentes versiones de la aplicación. Separar estos aspectos variables de los aspectos más permanentes para que se puede determinar con mayor facilidad lo que debe generarse. Por ejemplo, si la aplicación proporciona un sitio Web, separe la página estándar que proporciona funciones de la lógica que define las rutas de navegación de una página a otra.  
  
 Codifique los aspectos variables en uno o varios modelos de origen.  
 Un modelo es un archivo o una base de datos que cada plantilla lee para obtener valores específicos para las partes variables del código que se va a generar. Los modelos pueden ser bases de datos, archivos XML de diseño, diagramas o lenguajes específicos de dominio. Normalmente, se utiliza un modelo para generar varios archivos en un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto. Cada archivo se genera a partir de una plantilla independiente.  
  
 Puede usar más de un modelo en un proyecto. Por ejemplo, podría definir un modelo para la navegación entre páginas Web y un modelo independiente para el diseño de las páginas.  
  
 El modelo se centran en las necesidades y el vocabulario de los usuarios, no en su implementación.  
 Por ejemplo, en una aplicación de sitio Web, podría esperar el modelo para hacer referencia a las páginas Web e hipervínculos.  
  
 Idealmente, elija un formato de presentación adecuado para el tipo de información que representa el modelo. Por ejemplo, un modelo de rutas de acceso de navegación a través de un sitio Web podría ser un diagrama de cuadros y flechas.  
  
 Probar el código generado.  
 Usar pruebas manuales o automatizadas para comprobar que el código resultante funciona tal y como se requieren los usuarios. Evitar la generación de pruebas desde el mismo modelo desde el que se genera el código.  
  
 En algunos casos, las pruebas generales pueden realizarse directamente en el modelo. Por ejemplo, podría escribir una prueba que garantiza que todas las páginas en el sitio Web pueden tener acceso mediante la navegación desde cualquier otro.  
  
 Permitir código personalizado: generar clases parciales.  
 Permitir el código que se escribe a mano asimismo el código generado. Es raro que un esquema de generación de código para que pueda tener en cuenta todas las variantes posibles que pueden surgir. Por lo tanto, debe esperar agregar o reemplazar parte del código generado. Donde el material generado está en un lenguaje de .NET como [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], dos estrategias son especialmente útiles:  
  
-   Las clases generadas deben ser parciales. Esto permite agregar contenido al código generado.  
  
-   Clases deben generarse en pares, uno heredar de la otra. La clase base debe contener todos los métodos generados y propiedades, y la clase derivada debe contener solo los constructores. Esto permite que el código escrito a mano para reemplazar cualquiera de los métodos generados.  
  
 En otros lenguajes generados como XML, utilice el `<#@include#>` directiva para realizar combinaciones simples de contenido escrito a mano y generado. En casos más complejos, es posible que deba escribir un paso posterior al procesamiento que combine el archivo generado con los archivos escritos a mano.  
  
 Mueva el material común a archivos de inclusión o plantillas en tiempo de ejecución  
 Para evitar repetir similar bloques de texto y código en varias plantillas, use la `<#@ include #>` directiva. Para obtener más información, consulte [directiva Include de T4](../modeling/t4-include-directive.md).  
  
 Puede también generar plantillas de texto en tiempo de ejecución en un proyecto independiente y, a continuación, llamar a partir de la plantilla en tiempo de diseño. Para ello, use la `<#@ assembly #>` directiva para tener acceso al proyecto independiente. Para obtener ejemplos, vea ["Herencia en plantillas de texto" en el Blog de Gareth Jones](http://go.microsoft.com/fwlink/?LinkId=208373).  
  
 Considere la posibilidad de mover grandes bloques de código en un ensamblado independiente.  
 Si tiene bloques de código grande y bloques de características de clase, puede ser útil mover algunas de este código en métodos que se compilan en un proyecto independiente. Puede usar el `<#@ assembly #>` directiva para obtener acceso al código de la plantilla. Para obtener más información, consulte [directiva de ensamblado T4](../modeling/t4-assembly-directive.md).  
  
 Puede colocar los métodos en una clase abstracta que puede heredar la plantilla. La clase abstracta debe heredar de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Para obtener más información, consulte [directiva de plantilla de T4](../modeling/t4-template-directive.md).  
  
 Generar el código, no los archivos de configuración  
 Un método para escribir una aplicación variable consiste en escribir código de programa genérico que acepta un archivo de configuración. Una aplicación escrita de esta manera es muy flexible y puede volver a configurar cuando cambien los requisitos empresariales, sin volver a generar la aplicación. Sin embargo, un inconveniente de este enfoque es que la aplicación realizará peor rendimiento de una aplicación más específica. Además, su código de programa será más difícil de leer y mantener, en parte porque siempre tiene que tratar con los tipos más genéricos.  
  
 Por el contrario, una aplicación cuyas partes variables se generan antes de la compilación puede estar fuertemente tipada. Esto hace mucho más fácil y confiables escribir código escrita a mano e integrar con las partes del software.  
  
 Para obtener todas las ventajas de generación de código, intente generar código de programa en lugar de archivos de configuración.  
  
 Usar una carpeta de código generado  
 Coloque las plantillas y los archivos generados en una carpeta de proyecto denominada **código generado**, de modo que lo desactive que éstos no son archivos que deben editarse directamente. Si crea código personalizado para invalidar o agregar a las clases generadas, coloque estas clases en una carpeta que se denomina **código personalizado**. La estructura de un proyecto típico tiene el siguiente aspecto:  
  
```  
MyProject  
   Custom Code  
      Class1.cs  
      Class2.cs  
   Generated Code  
      Class1.tt  
          Class1.cs  
      Class2.tt  
          Class2.cs  
   AnotherClass.cs  
  
```  
  
## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Directrices para plantillas T4 de tiempo de ejecución (preprocesada)  
 Mover material común en plantillas heredadas  
 Puede utilizar la herencia para compartir los métodos y bloques de texto entre plantillas de texto T4. Para obtener más información, consulte [directiva de plantilla de T4](../modeling/t4-template-directive.md).  
  
 También puede usar incluyen archivos que tienen plantillas en tiempo de ejecución.  
  
 Mover grandes cuerpos de código en una clase parcial.  
 Cada plantilla en tiempo de ejecución genera una definición de clase parcial que tiene el mismo nombre que la plantilla. Puede escribir un archivo de código que contiene otra definición parcial de la misma clase. Puede agregar métodos, campos y constructores para la clase de esta manera. Estos miembros se pueden llamar desde los bloques de código en la plantilla.  
  
 La ventaja de hacerlo es que el código sea más fácil escribir, porque IntelliSense está disponible. Además, puede lograr una mejor separación entre la presentación y la lógica subyacente.  
  
 Por ejemplo, en **MyReportText.tt**:  
  
 `The total is: <#= ComputeTotal() #>`  
  
 En **MyReportText Methods.cs**:  
  
 `private string ComputeTotal() { ... }`  
  
 Permitir código personalizado: proporcionar puntos de extensión  
 Puede ser conveniente generar métodos virtuales en \<bloques de características de clase #+ #>. Esto permite que una única plantilla para su uso en muchos contextos sin ninguna modificación. En lugar de modificar la plantilla, puede construir una clase derivada que proporciona la lógica adicional mínima. La clase derivada puede ser cualquier código normal, o puede ser una plantilla en tiempo de ejecución.  
  
 Por ejemplo, en MyStandardRunTimeTemplate.tt:  
  
```  
This page is copyright <#= CompanyName() #>.  
<#+ protected virtual string CompanyName() { return ""; } #>  
```  
  
 En el código de una aplicación:  
  
```  
class FabrikamTemplate : MyStandardRunTimeTemplate  
{  
  protected override string CompanyName() { return "Fabrikam"; }  
}  
...  
  string PageToDisplay = new FabrikamTemplate().TextTransform();  
  
```  
  
## <a name="guidelines-for-all-t4-templates"></a>Directrices para todas las plantillas T4  
 Separar la recolección de datos de generación de texto  
 Intente evitar mezclar cálculo y bloques de texto. En cada plantilla de texto, utilice la primera \<# de bloque de código de # > para establecer las variables y realizar cálculos complejos. Desde el primer bloque de texto hasta el final de la plantilla o la primera \<característica de clase #+ Bloquear #>, evitar expresiones largas y evitar condicionales y bucles a menos que contengan bloques de texto. Esta práctica hace que la plantilla sea más fácil de leer y mantener.  
  
 No use `.tt` para archivos de inclusión  
 Usar una extensión de nombre de archivo diferente como `.ttinclude` archivos de inclusión. Use `.tt` solamente los archivos que se vayan a ser procesan ya sea como tiempo de ejecución o en tiempo de diseño de plantillas de texto. En algunos casos, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] reconoce `.tt` archivos y configura automáticamente sus propiedades para su procesamiento.  
  
 Inicie cada plantilla como un prototipo fijo.  
 Escribir un ejemplo del código o el texto que desea generar y asegúrese de que es correcta. A continuación, cambie su extensión a .tt e incrementalmente insertar código que modifica el contenido leyendo el modelo.  
  
 Considere el uso de modelos con tipo.  
 Aunque puede crear un esquema XML o base de datos para los modelos, puede ser útil crear un lenguaje específico de dominio (DSL). Un DSL tiene la ventaja de que genera una clase para representar cada nodo en el esquema y propiedades para representar los atributos. Esto significa que se puede programar en términos del modelo de negocio. Por ejemplo:  
  
```  
Team Members:  
<# foreach (Person p in team.Members)   
 { #>   
    <#= p.Name #>   
<# } #>  
```  
  
 Considere el uso de diagramas para los modelos.  
 Muchos modelos de forma más eficaz se presentan y se administran simplemente como tablas de texto, especialmente si son muy grandes.  
  
 Sin embargo, para algunos tipos de requisitos empresariales, es importante aclarar conjuntos complejos de relaciones y flujos de trabajo y los diagramas son el mejor medio adecuado. Una ventaja de un diagrama es que resulta fácil debatir con los usuarios y otras partes interesadas. Mediante la generación de código de un modelo en el nivel de los requisitos empresariales, el código resulta más flexible cuando cambian los requisitos.  
  
 También puede diseñar su propio tipo de diagrama como un lenguaje específico de dominio (DSL). UML y lenguajes DSL puede generar código. Para obtener más información, consulte [analizar y modelar la arquitectura](../modeling/analyze-and-model-your-architecture.md).  
  
## <a name="see-also"></a>Vea también  
 [Generación de código en tiempo de diseño usando las plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)   
 [Generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md)
