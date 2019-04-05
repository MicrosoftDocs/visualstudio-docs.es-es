---
title: Propiedades de atributos de UML de diagramas de clases | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.attribute.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: ba01e064-7424-4e72-98fa-42fa1c30e153
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 27affdb42f6f5ad1dd4c880b87e3cbf737d52921
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988238"
---
# <a name="properties-of-attributes-on-uml-class-diagrams"></a>Propiedades de los atributos de diagramas de clases de UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En un diagrama de clases de lenguaje unificado de modelado (UML), se pueden agregar *atributos* a clases e interfaces. Un atributo define los valores que se pueden asociar a instancias de la clase o la interfaz.  

 Para agregar un atributo, haga clic con el botón derecho en la clase o la interfaz, apunte a **Agregar**y después haga clic en **Atributo**.  

 Si los atributos de una clase del diagrama no están visibles, haga clic en el botón de contenido adicional de la parte superior de la clase o la interfaz para expandirla. Si puede ver el encabezado **Atributos** , haga clic en **[+]** para expandir la sección de atributos.  

## <a name="signature-of-an-attribute"></a>Firma de un atributo  
 La firma de un atributo es la línea que lo representa en una clase o una interfaz en un diagrama de clases de UML. Su formato es el siguiente:  

```  
+ AttributeName : TypeName [*]  
```  

 \+ denota visibilidad pública. Los otros valores permitidos son: - (privado), # (protegido), ~ (paquete).  

 `AttributeName` se subraya si el atributo es estático.  

 `: TypeName` se omite si el atributo no tiene tipo.  

 `[*]` denota la multiplicidad. Se omite si la multiplicidad es 1.  

## <a name="properties"></a>Propiedades  
 En la tabla siguiente se describen las propiedades de un atributo de una clase o interfaz en un diagrama de clases de UML.  

 Para ver las propiedades de un atributo, haga clic con el botón derecho en el atributo de la clase o la interfaz del diagrama y después haga clic en **Propiedades**. Las propiedades aparecen en la ventana Propiedades.  

 Para ver las propiedades de un atributo, haga clic en él con el botón derecho y luego haga clic en **Propiedades**.  


|   **Property**    | **Predetermiado**  |                                                                                                                                                                                                         Descripción                                                                                                                                                                                                          |
|-------------------|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Valor predeterminado** |   (vacío)    |                                                                                                                                                                               El valor del atributo cuando se crean instancias del clasificador.                                                                                                                                                                                |
| **Es de solo lectura**  |    False     |                                                                                                                                                                                    Si es True, el valor del atributo no se puede cambiar.                                                                                                                                                                                    |
|   **Es estático**   |    False     |                                                                                                                    Si es True, las instancias de este tipo comparten el mismo valor para este atributo.<br /><br /> Si es True, el nombre del atributo aparece subrayado en el diagrama.                                                                                                                    |
|     **Name**      | (un nombre nuevo) |                                                                                                                                                                                        Debe ser único en el clasificador propietario.                                                                                                                                                                                        |
|     **Type**      |    (ninguno)    |                                                Un tipo primitivo, como **Entero**o un tipo que se define en el modelo. No se pueden usar tipos no primitivos como **Decimal** porque el valor debe estar codificado en los metadatos. Si escribe un nombre para un nuevo tipo en esta propiedad, se agregará un tipo a la sección **Tipos sin especificar** del Explorador de modelos UML.                                                 |
|  **Visibilidad**   |    Public    |                                     Los valores permitidos y los caracteres que aparecen en la firma son los siguientes:<br /><br /> **+ Public** : es visible globalmente<br /><br /> **- Private** : no es visible fuera del tipo propietario.<br /><br /> **# Protected** : es visible para los tipos derivados del propietario.<br /><br /> **~ Package** : es visible para otros tipos del mismo paquete.                                      |
|  **Los elementos de trabajo**   | 0 asociados |                                                                                                                          Número de elementos de trabajo asociados. Sólo lectura.<br /><br /> Para obtener más información, consulte [vincular elementos de modelo y los elementos de trabajo](../modeling/link-model-elements-and-work-items.md).                                                                                                                           |
|    **Es la hoja**    |    False     |                                                                                                                                                                    Si es True, no está diseñado para permitir que este atributo se redefina en los tipos derivados.                                                                                                                                                                     |
|  **Se deriva**   |    False     |                                                                                                              Si es True, este atributo se calcula a partir de otros atributos. Por ejemplo, Diagonal se calcula a partir de Width y Height. Los detalles deben escribirse en la **Descripción** o en un comentario adjunto.                                                                                                              |
|  **Descripción**  |   (vacío)    |                                                                                                                                                                        Para realizar anotaciones generales o para definir restricciones sobre los valores del atributo.                                                                                                                                                                        |
| **Multiplicidad**  |      1       | **1** : este atributo tiene un valor único del tipo especificado.<br /><br /> **0..1** : este atributo puede tener un valor de `null`.<br /><br /> **\\**\* : valor de este atributo es una colección de valores.<br /><br /> **1..\\**  \* -valor de este atributo es una colección que contiene al menos un valor.<br /><br /> *n* **..** *m* : el valor de este atributo es una colección que contiene entre *n* y *m* valores. |
|  **Se ha pedido**   |    False     |                                                                                                                                                                    Si es True, la colección constituye una lista secuencial. Para un valor de **Multiplicity** mayor que 1.                                                                                                                                                                     |
|   **Es único**   |    False     |                                                                                                                                                                Si es True, no hay ningún valor duplicado en la colección. Para un valor de **Multiplicity** mayor que 1.                                                                                                                                                                |

## <a name="see-also"></a>Vea también  
 [Diagrama de clases de UML: Referencia](../modeling/uml-class-diagrams-reference.md)   
 [Propiedades de tipos en diagramas de clases UML](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [Propiedades de las operaciones de diagramas de clases UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [Diagrama de clases de UML: Directrices](../modeling/uml-class-diagrams-guidelines.md)   
 [Diagrama de clases de UML: directrices](../modeling/uml-class-diagrams-guidelines.md)
