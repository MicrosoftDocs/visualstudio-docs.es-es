---
title: Propiedades de las operaciones de UML de diagramas de clases | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.operation.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 4128f3e2-3a51-4edf-b3e4-b7f170a32f6b
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7a5a2e18c41f99462231da2a11dc80a0ae01e99e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51804484"
---
# <a name="properties-of-operations-on-uml-class-diagrams"></a>Propiedades de las operaciones de diagramas de clases de UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En un diagrama de clases UML, puede agregar *operaciones* a clases e interfaces. Una operación es un método o función que se puede realizar en una instancia de una clase o interfaz.  

 Para agregar una operación, haga clic en la clase o interfaz, apunte a **agregar**y, a continuación, haga clic en **operación**.  

 Si las operaciones de una clase del diagrama no están visibles, haga clic en el botón de contenido adicional de la parte superior de la clase o interfaz. Si puede ver el **operación** encabezado, haga clic en **[+]** para expandir la sección de operaciones.  

## <a name="signature-of-an-operation"></a>Firma de una operación  
 La firma de una operación es la línea de texto que la representa en una clase o interfaz en un diagrama de clases UML. Tiene la forma siguiente:  

 \+ OperationName (parameter1: Type1 [*],...): ReturnType [\*]  

 \+ denota visibilidad pública. Los otros valores permitidos son: - (privado), # (protegido), ~ (paquete).  

 `OperationName` se subraya si el **Is Static** propiedad es true y está en cursiva si la **Is Abstract** propiedad es true.  

 `: ReturnType` se omite si no se ha definido ningún tipo de valor devuelto.  

 `[*]` denota la multiplicidad de un parámetro o tipo de valor devuelto. Se omite si la multiplicidad es 1.  

 Vea la sección siguiente para obtener una descripción completa de estas propiedades.  

## <a name="properties"></a>Propiedades  
 Estas son las propiedades de una operación en una clase o interfaz de un diagrama de clases UML.  

 Para ver las propiedades de una operación, haga clic en la operación en la clase o interfaz en el diagrama y, a continuación, haga clic en **propiedades**. Las propiedades aparecen en la **propiedades** ventana.  


|      Property       |   Predeterminado    |                                                                                                                                                                                 Descripción                                                                                                                                                                                 |
|---------------------|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **Name**       | (un nombre nuevo) |                                                                                                                                                                Debe ser único dentro del tipo contenedor.                                                                                                                                                                 |
|   **Parámetros**    |    (ninguno)    |      Una lista que tiene el formato <em>nombre</em>**:**<em>tipo</em>**,** <em>nombre</em>**:**  <em>Tipo</em>**,...** Haga clic en **[...]**  para editar la lista.<br /><br /> Los tipos pueden ser tipos primitivos o tipos que se definen en el modelo. Si escribe un nombre para un nuevo tipo en esta propiedad, se agregará un tipo a la sección **Tipos sin especificar** del Explorador de modelos UML.      |
|   **Tipo de valor devuelto**   |    (ninguno)    |                                                                               **(ninguno)** , o un tipo primitivo o un tipo que se define en el modelo. Si escribe un nombre para un nuevo tipo en esta propiedad, se agregará un tipo a la sección **Tipos sin especificar** del Explorador de modelos UML.                                                                                |
| **Condiciones posteriores**  |    (ninguno)    |                                                                                                                         Una condición opcional que especifica una relación entre el estado del sistema antes y después de la ejecución de la operación.                                                                                                                         |
|  **Condiciones previas**  |    (ninguno)    |                                                                                                                            Una condición opcional que especifica las suposiciones acerca del estado del sistema antes de iniciarse la ejecución de la operación.                                                                                                                            |
| **Condiciones del cuerpo** |    (ninguno)    |                                                                                                                                                       Restricción opcional sobre los valores devueltos por la operación.                                                                                                                                                       |
|   **Visibilidad**    |    Public    |                  Los valores permitidos y los caracteres que aparecen en la firma son:<br /><br /> **+ Public** : es visible globalmente<br /><br /> **- Private** : no es visible fuera del tipo propietario.<br /><br /> **# Protected** : es visible para los tipos derivados del propietario.<br /><br /> **~ Package** : es visible para otros tipos del mismo paquete.                   |
|    **Firma**    |  +*Nombre*)   |                                                                                      Resume la visibilidad, nombre, parámetros y tipo de valor devuelto de la operación. Puede cambiar estas propiedades editando la firma en el diagrama o editando las propiedades individuales.                                                                                      |
|   **Los elementos de trabajo**    | 0 asociados |                                                                                                  Número de elementos de trabajo asociados. Sólo lectura.<br /><br /> Para obtener más información, consulte [vincular elementos de modelo y los elementos de trabajo](../modeling/link-model-elements-and-work-items.md).                                                                                                  |
|   **Simultaneidad**   |  Secuencial  | **Secuencial** -la operación es o se va a diseñar sin control de simultaneidad. Llamar simultáneamente a esta operación puede dar lugar a errores.<br /><br /> **Protegido** : la operación se bloqueará automáticamente hasta que se completen otras instancias de él.<br /><br /> **Simultáneas** : la operación se ha diseñado para que varias llamadas a la se pueden ejecutar simultáneamente. |
|    **Es estático**    |    False     |                                                                                                  Si es true, esta operación se comparte entre todas las instancias de este tipo.<br /><br /> Si es true, el nombre de la operación aparece subrayado cuando se muestra en el diagrama.                                                                                                   |
|   **Es abstracto**   |    False     |                                                                                                                                        Si es true, no hay ningún código asociado a esta operación. Por lo tanto, la clase propietaria es abstracta.                                                                                                                                         |
|     **Es la hoja**     |    False     |                                                                                                                                              El diseñador planea que esta operación no se pueda reemplazar en clases derivadas.                                                                                                                                              |
|    **Es la consulta**     |    False     |                                                                                                 Si es true, esta operación no realiza cambios significativos en el estado del sistema. Por lo tanto, se puede usar, por ejemplo, en una prueba para comprobar el estado del sistema.                                                                                                  |
|  **Multiplicidad**   |      1       |                                 **1** -un valor único del tipo especificado.<br /><br /> **de 0.. 1** -puede ser `null`.<br /><br /> \* -una colección de valores del tipo especificado.<br /><br /> **1..\\**  \* : una colección que contiene al menos un valor.<br /><br /> *n* `..` *m* -una colección que contiene entre `n` y `m` valores.                                  |
|   **Se ha pedido**    |    False     |                                                                                                                                             Si es True, la colección constituye una lista secuencial. Para **multiplicidad** más de 1.                                                                                                                                              |
|    **Es único**    |    False     |                                                                                                                                         Si es True, no hay ningún valor duplicado en la colección. Para **multiplicidad** más de 1.                                                                                                                                         |

## <a name="see-also"></a>Vea también  
 [Diagramas de clases UML: referencia](../modeling/uml-class-diagrams-reference.md)   
 [Propiedades de tipos en diagramas de clases UML](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [Propiedades de atributos en diagramas de clases UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [Propiedades de las asociaciones de diagramas de clases UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)   
 [Diagramas de clases de UML: instrucciones](../modeling/uml-class-diagrams-guidelines.md)



