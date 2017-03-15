---
title: Instrucciones para escribir plantillas de texto T4 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04dd3fc4-10e8-488a-bdea-4d615f50f063
caps.latest.revision: 9
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
ms.openlocfilehash: 7d9dd7193455a625b0410eaca3b2bd243c109743
ms.lasthandoff: 02/22/2017

---
# <a name="guidelines-for-writing-t4-text-templates"></a>Instrucciones para escribir plantillas de texto T4
Estas directrices generales pueden resultar útiles si va a generar código de programa u otros recursos de la aplicación en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Las reglas no son fijas.  
  
## <a name="guidelines-for-design-time-t4-templates"></a>Directrices para plantillas T4 en tiempo de diseño  
 Plantillas T4 en tiempo de diseño son plantillas que generan código en su [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto en tiempo de diseño. Para obtener más información, consulte [generación de código de tiempo de diseño mediante el uso de plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 Genere aspectos variables de la aplicación.  
 Generación de código es muy útil para los aspectos de la aplicación que pueden cambiar durante el proyecto o cambiará entre las distintas versiones de la aplicación. Separe estos aspectos variables de los aspectos más permanentes para que puede determinar fácilmente lo que se va a generar. Por ejemplo, si la aplicación proporciona un sitio Web, separe la página estándar que proporciona funciones de la lógica que define las rutas de navegación de una página a otra.  
  
 Codifique los aspectos variables en uno o más modelos de origen.  
 Un modelo es un archivo o una base de datos que cada plantilla lee para obtener valores concretos para las partes variables del código que se va a generar. Modelos pueden ser bases de datos, archivos XML de su propio diseño, diagramas o lenguajes específicos de dominio. Normalmente, un modelo se utiliza para generar varios archivos en un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto. Cada archivo se genera a partir de una plantilla independiente.  
  
 Puede utilizar más de un modelo en un proyecto. Por ejemplo, podría definir un modelo para la navegación entre las páginas Web y un modelo independiente para el diseño de las páginas.  
  
 Centrar el modelo en el vocabulario y las necesidades de los usuarios, no en su implementación.  
 Por ejemplo, en una aplicación de sitio Web, esperará que el modelo para hacer referencia a las páginas Web e hipervínculos.  
  
 Idealmente, elija un formato de presentación adecuado para el tipo de información que representa el modelo. Por ejemplo, un modelo de rutas de navegación a través de un sitio Web podría ser un diagrama de cuadros y flechas.  
  
 Probar el código generado.  
 Utilice pruebas manuales o automatizadas para comprobar que el código resultante funciona según los usuarios necesitan. Evitar que se generen las pruebas desde el mismo modelo desde el que se genera el código.  
  
 En algunos casos, las pruebas generales pueden realizarse directamente en el modelo. Por ejemplo, podría escribir una prueba que garantiza que todas las páginas del sitio Web pueden tener acceso mediante la exploración de cualquier otro.  
  
 Permitir código personalizado: generar clases parciales.  
 Permitir el código que se escribe a mano además del código generado. Es raro que un esquema de generación de código que puedan tener en cuenta todas las posibles variaciones que podrían surgir. Por lo tanto, debe esperar agregar o reemplazar parte del código generado. Donde el material generado está en un lenguaje .NET como [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], dos estrategias son especialmente útiles:  
  
-   Las clases generadas deben ser parciales. Esto permite agregar contenido al código generado.  
  
-   Las clases deben generarse en pares, uno heredar de la otra. La clase base debe contener todos los métodos y propiedades generados, y la clase derivada debe contener sólo los constructores. Esto permite que el código escrito a mano para reemplazar cualquiera de los métodos generados.  
  
 En otros lenguajes generados como XML, utilice el `<#@include#>` directiva para realizar combinaciones simples de contenido escrito a mano y generado. En casos más complejos, es posible que deba escribir un paso posterior al procesamiento que combine el archivo generado con los archivos escritos a mano.  
  
 Mover material común en los archivos de inclusión o plantillas en tiempo de ejecución  
 Para evitar repetir similar bloques de texto y código en varias plantillas, utilice la `<#@ include #>` directiva. Para obtener más información, consulte [directiva Include de T4](../modeling/t4-include-directive.md).  
  
 Puede también crear plantillas de texto en tiempo de ejecución en un proyecto independiente y, a continuación, llamar a partir de la plantilla en tiempo de diseño. Para ello, utilice el `<#@ assembly #>` directiva tener acceso al proyecto independiente. Para obtener ejemplos, vea ["Herencia en plantillas de texto" en el Blog de Gareth Jones](http://go.microsoft.com/fwlink/?LinkId=208373).  
  
 Considere mover grandes bloques de código en un ensamblado independiente.  
 Si dispone de bloques de código grandes y bloques de características de clase, puede ser útil mover este código a los métodos que se compilan en un proyecto independiente. Puede usar el `<#@ assembly #>` directiva tener acceso al código de la plantilla. Para obtener más información, consulte [directiva de ensamblado T4](../modeling/t4-assembly-directive.md).  
  
 Puede colocar los métodos en una clase abstracta que se puede heredar la plantilla. La clase abstracta debe heredar de <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>.</xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> Para obtener más información, consulte [directiva de plantilla T4](../modeling/t4-template-directive.md).  
  
 Generar código, no los archivos de configuración  
 Un método para escribir una aplicación variable consiste en escribir código de programa genérico que acepte un archivo de configuración. Una aplicación escrita de esta manera es muy flexible y puede volver a configurar cuando cambien los requisitos empresariales, sin tener que recompilar la aplicación. Sin embargo, un inconveniente de este enfoque es que la aplicación realizará menos rendimiento que una aplicación más específica. Además, su código de programa será más difícil de leer y mantener, en parte porque siempre tiene que tratar con los tipos más genéricos.  
  
 Por el contrario, una aplicación cuyas partes variables se generan antes de la compilación puede estar fuertemente tipada. Esto hace mucho más fácil y confiables para escribir código escrito a mano e integrarlo con generado partes del software.  
  
 Para obtener todas las ventajas de la generación de código, intente generar código de programa en lugar de los archivos de configuración.  
  
 Utilice una carpeta de código generado  
 Coloque las plantillas y los archivos generados en una carpeta de proyecto denominada **código generado por**, para asegurarse de desactive que estas no son archivos que se deben editar directamente. Si crea código personalizado para invalidar o agregar a las clases generadas, coloque estas clases en una carpeta que se denomina **código personalizado**. La estructura de un proyecto típico tiene el siguiente aspecto:  
  
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
 Material común se trasladan plantillas heredadas  
 Puede utilizar la herencia para compartir los métodos y los bloques de texto entre las plantillas de texto T4. Para obtener más información, consulte [directiva de plantilla T4](../modeling/t4-template-directive.md).  
  
 También puede usar archivos de inclusión que tienen plantillas en tiempo de ejecución.  
  
 Mover grandes cantidades de código a una clase parcial.  
 Cada plantilla en tiempo de ejecución genera una definición de clase parcial que tiene el mismo nombre que la plantilla. Puede escribir un archivo de código que contiene otra definición parcial de la misma clase. Puede agregar métodos, campos y constructores para la clase de esta manera. Estos miembros pueden llamarse desde los bloques de código en la plantilla.  
  
 Una ventaja de hacerlo es que el código es más fácil de escribir, porque IntelliSense está disponible. Además, puede lograr una mejor separación entre la presentación y la lógica subyacente.  
  
 Por ejemplo, en **MyReportText.tt**:  
  
 `The total is: <#= ComputeTotal() #>`  
  
 En **MyReportText Methods.cs**:  
  
 `private string ComputeTotal() { ... }`  
  
 Permitir código personalizado: proporcionar puntos de extensión  
 Considere la posibilidad de generar métodos virtuales en \<bloques de características de clase #+ #>. Esto permite que una sola plantilla para usarse en muchos contextos sin ninguna modificación. En lugar de modificar la plantilla, puede crear una clase derivada que proporciona la lógica adicional mínima. La clase derivada puede ser cualquier código normal, o puede ser una plantilla en tiempo de ejecución.  
  
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
 Separar la recopilación de datos de generación de texto  
 Intente evitar la mezcla de cálculo y bloques de texto. En cada plantilla de texto, utilice la primera \<código # bloquear #> para establecer las variables y realizar cálculos complejos. Desde el primer bloque de texto hasta el final de la plantilla o la primera \<característica de clase #+ bloquear #>, evitar expresiones largas y evitar condicionales y bucles a menos que contienen bloques de texto. Esta práctica hace que la plantilla sea más fácil de leer y mantener.  
  
 No utilice `.tt` archivos de inclusión  
 Utilice una extensión de nombre de archivo diferente como `.ttinclude` archivos de inclusión. Use `.tt` solamente los archivos que desea procesan las plantillas de texto como tiempo de ejecución o tiempo de diseño. En algunos casos, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] reconoce `.tt` archivos y establece automáticamente las propiedades para el procesamiento.  
  
 Inicie cada plantilla como un prototipo fijo.  
 Escribir un ejemplo del código o el texto que desea generar y asegúrese de que es correcta. A continuación, cambie su extensión a .tt e inserte incrementalmente código que modifique el contenido leyendo el modelo.  
  
 Considere el uso de modelos con tipo.  
 Aunque puede crear un esquema XML o base de datos para los modelos, puede ser útil crear un lenguaje específico de dominio (DSL). Un DSL tiene la ventaja de que genera una clase para representar cada nodo en el esquema y propiedades para representar los atributos. Esto significa que puede programar en términos del modelo de negocio. Por ejemplo:  
  
```  
Team Members:  
<# foreach (Person p in team.Members)   
 { #>   
    <#= p.Name #>   
<# } #>  
```  
  
 Considere el uso de diagramas para los modelos.  
 Muchos modelos se presentan más eficaz y se administran simplemente como tablas de texto, especialmente si son muy grandes.  
  
 Sin embargo, para algunos tipos de requisitos empresariales, es importante aclarar conjuntos complejos de relaciones y flujos de trabajo y los diagramas son el mejor medio adecuado. Una ventaja de un diagrama es que es fácil hablar con los usuarios y otras partes interesadas. Mediante la generación de código de un modelo en el nivel de los requisitos empresariales, el código resulta más flexible cuando cambien los requisitos.  
  
 También puede diseñar su propio tipo de diagrama como un lenguaje específico de dominio (DSL). Código puede generarse de UML y lenguajes DSL. Para obtener más información, consulte [arquitectura de modelado y análisis](../modeling/analyze-and-model-your-architecture.md).  
  
## <a name="see-also"></a>Vea también  
 [Generación de código en tiempo de diseño usando las plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)   
 [Generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md)

