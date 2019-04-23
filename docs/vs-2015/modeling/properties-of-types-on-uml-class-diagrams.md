---
title: Propiedades de tipos de UML de diagramas de clases | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 6e1ef2d0-d67a-401a-bd64-d5e034decd2c
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 17d18a485e57b896aaf3f40b0cfdab63e10dce2c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60062235"
---
# <a name="properties-of-types-on-uml-class-diagrams"></a>Propiedades de los tipos de diagramas de clases de UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En un diagrama de clases UML, un *tipo* es una clase, una interfaz o enumeración.  
  
> [!NOTE]
>  Este tema es sobre las propiedades de los tipos de diagramas de clases de UML. Para obtener más información, vea los temas siguientes:  
  
- [Diagrama de clases de UML: referencia](../modeling/uml-class-diagrams-reference.md)  
  
- [Diagrama de clases de UML: directrices](../modeling/uml-class-diagrams-guidelines.md)  
  
- [Propiedades de los atributos de diagramas de clases de UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
- [Propiedades de las operaciones de diagramas de clases de UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
- [Propiedades de las asociaciones de diagramas de clases de UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)  
  
## <a name="properties"></a>Propiedades  
 Estas son las propiedades de una clase, interfaz o enumeración.  
  
 Para ver las propiedades de un tipo, haga clic en el tipo en el diagrama o en **Explorador de modelos UML**y, a continuación, haga clic en **propiedades**. Las propiedades aparecen en la **propiedades** ventana.  
  
|**Property**|**Predetermiado**|Aparece en|Descripción|  
|------------------|-----------------|----------------|-----------------|  
|**Name**|Nombre predeterminado|Todos los elementos|Identifica el elemento.|  
|**Nombre completo**|Paquete contenedor:: Nombre de tipo|Todos los elementos|Identifica de forma única el elemento. Prefijo con el nombre completo del paquete que lo contiene.|  
|**Color**|Valor predeterminado para la clase de tipo|Todos los elementos|Color de esta forma. A diferencia de otras propiedades, esta no es una propiedad del elemento del modelo subyacente. Las vistas diferentes del mismo tipo pueden tener diferentes colores.|  
|**Es abstracto**|False|Clase|Si es true, no se pueden crear instancias de la clase y está pensada para usarse como clase base.|  
|**Es la hoja**|False|Clase, interfaz|Si es true, el tipo no pretende tener tipos derivados.|  
|**Está activo**|False|Clase|Si es true, cada instancia de este tipo se asocia con un subproceso de control.|  
|**Visibilidad**|Public|Clase, interfaz, enumeración|-Public: es visible globalmente.<br />-Private: este tipo es visible dentro del paquete que lo posee.<br />-Package: es visible dentro del paquete.|  
|**Los elementos de trabajo**|0 asociados|Todos los elementos|Número de elementos de trabajo asociados a este elemento. Para asociar elementos de trabajo, consulte [vincular elementos de modelo y los elementos de trabajo](../modeling/link-model-elements-and-work-items.md).|  
|**Descripción**|(en blanco)|Todos los elementos|Aquí puede realizar anotaciones generales sobre el elemento.|  
|**Enlace a plantilla**|(ninguno)|Clase, interfaz, enumeración|Si no está vacío, este tipo se define enlazando los valores de parámetro a esta clase de plantilla. Expanda la propiedad para ver los enlaces de los parámetros de plantilla.|  
|**Parámetros de plantilla**|(ninguno)|Clase, interfaz, enumeración|Si no está vacío, es una clase de plantilla que tiene los parámetros enumerados aquí. Para agregar parámetros o ver las propiedades de parámetros individuales, haga clic en **[...]** .|  
  
## <a name="see-also"></a>Vea también  
 [Propiedades de atributos en diagramas de clases UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [Propiedades de las operaciones de diagramas de clases UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [Propiedades de las asociaciones de diagramas de clases UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)   
 [Diagrama de clases de UML: directrices](../modeling/uml-class-diagrams-guidelines.md)
