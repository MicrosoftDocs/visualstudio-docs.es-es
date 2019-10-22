---
title: Propiedades de las operaciones en diagramas de clases de UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.operation.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 4128f3e2-3a51-4edf-b3e4-b7f170a32f6b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67d752fa802deef5dcc40fdfa4d762dc6edb1d0d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671345"
---
# <a name="properties-of-operations-on-uml-class-diagrams"></a>Propiedades de las operaciones de diagramas de clases de UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En un diagrama de clases UML, puede agregar *operaciones* a clases e interfaces. Una operación es un método o función que se puede realizar en una instancia de una clase o interfaz.

 Para agregar una operación, haga clic con el botón secundario en la clase o interfaz, seleccione **Agregar**y, a continuación, haga clic en **operación**.

 Si las operaciones de una clase del diagrama no están visibles, haga clic en el botón de contenido adicional de la parte superior de la clase o interfaz. Si puede ver el encabezado de la **operación** , haga clic en **[+]** para expandir la sección operaciones.

## <a name="signature-of-an-operation"></a>Firma de una operación
 La firma de una operación es la línea de texto que la representa en una clase o interfaz en un diagrama de clases UML. Tiene la forma siguiente:

 \+ OperationName (parámetro1: Type1 [*],...): ReturnType [\*]

 \+ denota la visibilidad pública. Los otros valores permitidos son: - (privado), # (protegido), ~ (paquete).

 `OperationName` está subrayada si la propiedad **is static** es true y está en cursiva si la propiedad **is Abstract** es true.

 `: ReturnType` se omite si no se ha definido ningún tipo de valor devuelto.

 `[*]` denota la multiplicidad de un parámetro o tipo de valor devuelto. Se omite si la multiplicidad es 1.

 Vea la sección siguiente para obtener una descripción completa de estas propiedades.

## <a name="properties"></a>Propiedades
 Estas son las propiedades de una operación en una clase o interfaz de un diagrama de clases UML.

 Para ver las propiedades de una operación, haga clic con el botón secundario en la operación en la clase o interfaz del diagrama y, a continuación, haga clic en **propiedades**. Las propiedades aparecen en la ventana **propiedades** .

|      Propiedad.       |   Predeterminado    |                                                                                                                                                                                 Descripción                                                                                                                                                                                 |
|---------------------|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **Nombre**       | (un nombre nuevo) |                                                                                                                                                                Debe ser único dentro del tipo contenedor.                                                                                                                                                                 |
|   **Parámetros**    |    (ninguno)    |      Una lista con el formato <em>nombre</em> **:** <em>tipo</em> **,** <em>nombre</em> **:** <em>tipo</em> **,....** Haga clic en **[...]** para editar la lista.<br /><br /> Los tipos pueden ser tipos primitivos o tipos que se definen en el modelo. Si escribe un nombre para un nuevo tipo en esta propiedad, se agregará un tipo a la sección **Tipos sin especificar** del Explorador de modelos UML.      |
|   **Tipo de valor devuelto**   |    (ninguno)    |                                                                               **(ninguno)** , o un tipo primitivo, o un tipo que se define en el modelo. Si escribe un nombre para un nuevo tipo en esta propiedad, se agregará un tipo a la sección **Tipos sin especificar** del Explorador de modelos UML.                                                                                |
| **Condiciones posteriores**  |    (ninguno)    |                                                                                                                         Una condición opcional que especifica una relación entre el estado del sistema antes y después de la ejecución de la operación.                                                                                                                         |
|  **Condiciones previas**  |    (ninguno)    |                                                                                                                            Una condición opcional que especifica las suposiciones acerca del estado del sistema antes de iniciarse la ejecución de la operación.                                                                                                                            |
| **Condiciones del cuerpo** |    (ninguno)    |                                                                                                                                                       Restricción opcional sobre los valores devueltos por la operación.                                                                                                                                                       |
|   **Visibilidad**    |    Public    |                  Los valores permitidos y los caracteres que aparecen en la firma son:<br /><br /> **+ Public** : es visible globalmente<br /><br /> **- Private** : no es visible fuera del tipo propietario.<br /><br /> **# Protected** : es visible para los tipos derivados del propietario.<br /><br /> **~ Package** : es visible para otros tipos del mismo paquete.                   |
|    **Signatura**    |  *nombre*+ ()   |                                                                                      Resume la visibilidad, nombre, parámetros y tipo de valor devuelto de la operación. Puede cambiar estas propiedades editando la firma en el diagrama o editando las propiedades individuales.                                                                                      |
|   **Elementos de trabajo**    | 0 asociados |                                                                                                  Número de elementos de trabajo asociados. Sólo lectura.<br /><br /> Para obtener más información, vea [vincular elementos de modelo y elementos de trabajo](../modeling/link-model-elements-and-work-items.md).                                                                                                  |
|   **Simultaneidad**   |  Secuencial  | **Secuencial** : la operación es o se diseñará sin el control de simultaneidad. Llamar simultáneamente a esta operación puede dar lugar a errores.<br /><br /> **Protegido** : la operación se bloqueará automáticamente hasta que se completen otras instancias de ella.<br /><br /> **Simultáneo** : la operación está diseñada para que se puedan ejecutar varias llamadas al mismo tiempo. |
|    **Estático**    |    False     |                                                                                                  Si es true, esta operación se comparte entre todas las instancias de este tipo.<br /><br /> Si es true, el nombre de la operación aparece subrayado cuando se muestra en el diagrama.                                                                                                   |
|   **Es abstracto**   |    False     |                                                                                                                                        Si es true, no hay ningún código asociado a esta operación. Por lo tanto, la clase propietaria es abstracta.                                                                                                                                         |
|     **Es hoja**     |    False     |                                                                                                                                              El diseñador planea que esta operación no se pueda reemplazar en clases derivadas.                                                                                                                                              |
|    **Consulta de is**     |    False     |                                                                                                 Si es true, esta operación no realiza cambios significativos en el estado del sistema. Por lo tanto, se puede usar, por ejemplo, en una prueba para comprobar el estado del sistema.                                                                                                  |
|  **Multiplicidad**   |      1       |                                 **1** : un valor único del tipo especificado.<br /><br /> **0.. 1** -se puede `null`.<br /><br /> \*: una colección de valores del tipo especificado.<br /><br /> **1.. \\** \*: colección que contiene al menos un valor.<br /><br /> *n* `..` *m* : colección que contiene entre `n` y valores `m`.                                  |
|   **Está ordenado**    |    False     |                                                                                                                                             Si es True, la colección constituye una lista secuencial. Para una **multiplicidad** superior a 1.                                                                                                                                              |
|    **Es único**    |    False     |                                                                                                                                         Si es True, no hay ningún valor duplicado en la colección. Para una **multiplicidad** superior a 1.                                                                                                                                         |

## <a name="see-also"></a>Vea también
 [Diagramas de clases de UML:](../modeling/uml-class-diagrams-reference.md) [propiedades de referencia de los tipos de diagramas de clases de UML](../modeling/properties-of-types-on-uml-class-diagrams.md) [propiedades de los atributos de diagramas de clases de UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [propiedades de las asociaciones de diagramas de clases](../modeling/properties-of-associations-on-uml-class-diagrams.md) de UML [diagramas de clases de UML: instrucciones](../modeling/uml-class-diagrams-guidelines.md)
