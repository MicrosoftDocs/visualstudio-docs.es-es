---
title: Propiedades de las asociaciones de UML de diagramas de clases | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.common.association.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: f82bcd34-7903-4c00-8da1-613efa07d223
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b132ee2aa0f67662fcfcad92b8ae945c2d66c680
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810311"
---
# <a name="properties-of-associations-on-uml-class-diagrams"></a>Propiedades de las asociaciones de diagramas de clases de UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En un diagrama de clases UML, puede dibujar *asociaciones* entre cualquier par de tipos. Un tipo es una clase, interfaz o enumeración.  

 Una asociación indica que el sistema que está desarrollando almacena vínculos de algún tipo entre las instancias de los tipos asociados. Por lo general, esto no conlleva nada para la implementación de los vínculos. Por ejemplo, podrían ser punteros, filas de una tabla, nombres con referencias cruzadas en XML, etcétera.  

 Una asociación es un método en forma de diagrama para mostrar un atributo o un par de atributos. Por ejemplo, si definió una clase Restaurant para que tenga un atributo de tipo Menu, puede establecer la misma definición dibujando una asociación entre Restaurant y Menu.  

 Para dibujar una asociación, haga clic en **asociación** en el cuadro de herramientas, haga clic en el primer tipo y, a continuación, el segundo. Puede hacer clic en el mismo tipo dos veces para mostrar que las instancias pueden vincularse a otras instancias del mismo tipo.  

## <a name="properties"></a>Propiedades  
 Estas son las propiedades de una asociación en un diagrama de clases UML.  

 Para ver las propiedades de una asociación, haga clic en la asociación y, a continuación, haga clic en **propiedades**. Las propiedades aparecerán en la ventana Propiedades.  

 Algunas de las propiedades también son visibles en el diagrama, como se muestra en la siguiente ilustración.  

 ![Propiedades en asociaciones](../modeling/media/uml-classprop.png "UML_ClassProp")  

|**Property**|Descripción|  
|------------------|-----------------|  
|**Nombre (1)**|Identifica la asociación. También aparece en el diagrama situado junto al punto medio de la asociación.|  
|**Nombre completo**|Identifica de forma única la asociación. Prefijo con el nombre completo del paquete que contiene el primer rol de la asociación.|  
|**Los elementos de trabajo**|Número de elementos de trabajo vinculados a esta asociación. Para vincular elementos de trabajo, consulte [vincular elementos de modelo y los elementos de trabajo](../modeling/link-model-elements-and-work-items.md).|  
|**Color**|Color del conector. A diferencia de otras propiedades, se trata de una propiedad de esta vista de la asociación, no una propiedad de la relación subyacente en el modelo.|  
|**Primer rol**<br /><br /> **Segundo rol**|Cada extremo de la asociación se denomina rol. Cada rol describe las propiedades del atributo equivalente de la clase en el extremo opuesto de la asociación.<br /><br /> En el diagrama de ejemplo, la asociación entre Menu y Menu Item tiene los roles denominados Menu y Contents.<br /><br /> Contents es el nombre de un atributo de la clase Menu.|  

### <a name="properties-of-each-role"></a>Propiedades de cada rol  
 Para ver las propiedades de cada rol, expanda el **primer rol** o **segundo rol** propiedad.  


|     **Property**     |          **Predetermiado**          |                                                                                                                                                                                                                                                                                                                                        Descripción                                                                                                                                                                                                                                                                                                                                         |
|----------------------|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Nombre de rol (2)**   | Nombre del tipo de este rol |                                                                                                                                                                                                                                                                                                       Nombre del rol. Aparece junto al extremo de la asociación del diagrama.                                                                                                                                                                                                                                                                                                        |
|   **Agregación**    |             Ninguna              |                                                                        **Ninguno** (4): representa una relación general entre instancias de las clases.<br /><br /> **Compuesto** (5): el objeto de este rol contiene el objeto en el rol opuesto. Puede usar el **compuesto** herramienta para crear una asociación con la agregación Composite.<br /><br /> **Compartido** (6): objeto de este rol contiene referencias al objeto del otro rol. Puede usar el **agregación** herramienta para crear una asociación con la agregación Shared.<br /><br /> La interpretación exacta es convención local.                                                                         |
|    **Se deriva**    |             False             |                                                                                                                                                                                                                          Si es true, el objeto de este extremo del vínculo se calcula a partir de otros atributos y asociaciones. Por ejemplo, MyWorkPlace se calcula a partir de MyEmployer.WorkPlace. Los detalles deben escribirse en la descripción o en un comentario adjunto.                                                                                                                                                                                                                           |
| **Es derivada de unión** |             False             |                                                                                                                                                                                                                                                                                                             Si es true, el rol es la unión de un conjunto de roles de tipos derivados.                                                                                                                                                                                                                                                                                                             |
|   **Es navegable**   |             True              |                                                 La asociación se puede leer en esta dirección. Dada una instancia del rol contrario, el software que se está describiendo puede determinar de forma eficaz la instancia asociada de este rol.<br /><br /> Si un rol es navegable y el otro no lo es, aparece una flecha (7) en la asociación en la dirección navegable.<br /><br /> De forma predeterminada, la herramienta de asociación crea una asociación que es navegable en una dirección. Para convertirla en una asociación bidireccional, puede seleccionar la asociación, haga clic en la etiqueta de acción que aparece y, a continuación, haga clic en **hacer bidireccional**.                                                 |
|   **Es de solo lectura**   |             False             |                                                                                                                                                                                                                                                                                   Si es true, una instancia de la asociación no se puede cambiar después de crearse. El vínculo es siempre al mismo objeto.                                                                                                                                                                                                                                                                                    |
| **Multiplicidad (3)** |               1               | **1** : este extremo de la asociación siempre se vincula a un objeto. En la ilustración, cada Menu Item tiene un Menu.<br /><br /> **de 0.. 1** : ya sea este extremo de la asociación se vincula a un objeto, o no hay ningún vínculo.<br /><br /> **\\**\* -cada objeto en el otro extremo de la asociación está vinculado a una colección de objetos de este extremo, y la colección puede estar vacía.<br /><br /> **1..\\**  \* -todos los objetos en el otro extremo de la asociación está vinculado al menos un objeto de este extremo. En la ilustración, cada Menu tiene al menos un Menu Item.<br /><br /> *n* **..** *m* -cada objeto del otro extremo tiene una colección de entre *n* y *m* vínculos a objetos de este extremo. |
|    **Se ha pedido**    |             False             |                                                                                                                                                                                                                                                                                                  Si es true, la colección devuelta constituye una lista secuencial. Para un valor de Multiplicity mayor que 1.                                                                                                                                                                                                                                                                                                   |
|    **Es único**     |             False             |                                                                                                                                                                                                                                                                                              Si es true, no hay ningún valor duplicado en la colección devuelta. Para un valor de Multiplicity mayor que 1.                                                                                                                                                                                                                                                                                              |
|    **Visibilidad**    |            Public             |                                                                                                                                                                                                                                 Public: es visible globalmente.<br /><br /> Private: no es visible fuera del tipo propietario.<br /><br /> Protected: es visible para los tipos derivados del propietario.<br /><br /> Package: es visible para otros tipos del mismo paquete.                                                                                                                                                                                                                                  |

## <a name="see-also"></a>Vea también  
 [Diagramas de clases UML: referencia](../modeling/uml-class-diagrams-reference.md)   
 [Propiedades de tipos en diagramas de clases UML](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [Propiedades de atributos en diagramas de clases UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [Propiedades de las operaciones de diagramas de clases UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [Diagramas de clases de UML: instrucciones](../modeling/uml-class-diagrams-guidelines.md)



