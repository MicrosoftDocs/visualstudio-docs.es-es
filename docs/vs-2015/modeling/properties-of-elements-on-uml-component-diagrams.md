---
title: Propiedades de elementos en diagramas de componentes UML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.componentdiagram.shapes.properties
helpviewer_keywords:
- component diagrams, properties
- UML, element properties
ms.assetid: fa0a9460-6675-4642-aa00-50f8719a892d
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fb99ea1efb070c3e79b294bd5d06eedf131623f0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790089"
---
# <a name="properties-of-elements-on-uml-component-diagrams"></a>Propiedades de los elementos de diagramas de componentes de UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En un diagrama de componentes UML, cada elemento del diagrama tiene propiedades. Para ver las propiedades de un elemento, haga clic en el elemento en el diagrama o en **Explorador de modelos UML** y, a continuación, haga clic en **propiedades**. Las propiedades aparecen en la **propiedades** ventana.  
  
> [!NOTE]
>  Este tema trata sobre las propiedades de los elementos de los diagramas de componentes UML. Para obtener más información sobre cómo leer diagramas de componentes UML, vea [diagramas de componentes UML: referencia](../modeling/uml-component-diagrams-reference.md). Para obtener más información sobre cómo dibujar diagramas de componentes UML, vea [diagramas de componentes UML: instrucciones](../modeling/uml-component-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Propiedades de los elementos  
  
|Propiedad|Predeterminado|Elemento|Descripción|  
|--------------|-------------|-------------|-----------------|  
|**Name**|Nombre predeterminado|Todo|Identifica el elemento.|  
|**Nombre completo**|Espacio de nombres :: Nombre|Todo|Identifica de forma única el elemento.<br /><br /> El nombre de un componente o tipo incluye un prefijo con el nombre completo del paquete que lo contiene.<br /><br /> El nombre de una parte o puerto incluye un prefijo con el nombre completo del componente que lo posee.|  
|**Los elementos de trabajo**|0 asociados|Todo|Número de elementos de trabajo asociados a este elemento. Para asociar elementos de trabajo, consulte [vincular elementos de modelo y los elementos de trabajo](../modeling/link-model-elements-and-work-items.md).|  
|**Descripción**|(ninguno)|Todo|Aquí puede realizar anotaciones generales sobre el elemento.|  
|**Color**|(valor predeterminado para el tipo)|Component, Part, Delegation, Part Assembly|Color de la forma. A diferencia de otras propiedades, este es el color de la forma, en lugar del elemento de modelo que muestra la forma.|  
|**Is Indirectly Instantiated**|True|Componente|El componente solo existe como artefacto de diseño. En tiempo de ejecución, solo existen sus partes.|  
|**Es abstracto**|False|Componente|La definición del componente solo puede usarse como una generalización desde la que se pueden especializar otros componentes.|  
|**Visibilidad**|Public|Component, Part, Port|**Pública** : es visible globalmente.<br /><br /> **Paquete** : es visible dentro del paquete.<br /><br /> **Privada** : es visible dentro del componente propietario.<br /><br /> **Protegido** : es visible para los componentes derivados del propietario.|  
|**Type**|Tipo en la creación|Parte<br /><br /> Puerto|El tipo de un elemento Part es un componente o una clase.<br /><br /> El tipo de un elemento Port es una interfaz.|  
|**Multiplicidad**|1|Parte<br /><br /> Puerto|Indica cuántas instancias del tipo especificado forman parte del componente primario.<br /><br /> `1`: exactamente una.<br /><br /> `0..1`: una o ninguna.<br /><br /> `*`: una colección de números.<br /><br /> `n..m`: una colección de instancias de n a m.|  
|**Es el comportamiento**|False|Puerto|Si es true, los mensajes para este puerto se controlan mediante las actividades u operaciones que se describen como parte del componente, en lugar de sus partes.|  
|**Es el servicio**|False|Puerto|Si es true, este puerto forma parte de la interfaz publicada de este componente.|  
|**LinkedPackage**|Modelo|Diagrama|Espacio de nombres predeterminado para los elementos agregados a este diagrama.|  
  
## <a name="see-also"></a>Vea también  
 [Diagramas de casos de uso UML: referencia](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramas de casos de uso de UML: instrucciones](../modeling/uml-use-case-diagrams-guidelines.md)



