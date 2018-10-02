---
title: Propiedades de elementos de UML diagramas de casos de uso | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties
- vs.teamarch.usecasediagram.shapes.properties
helpviewer_keywords:
- use case diagrams, properties
ms.assetid: 2728fb26-a275-4fce-8a2c-5a78af6bee04
caps.latest.revision: 13
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: dd23baadfca51bf669336ab96bf00ee5d4594a08
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578026"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>Propiedades de los elementos de diagramas de casos de uso UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [propiedades de elementos de UML diagramas de casos de uso](https://docs.microsoft.com/visualstudio/modeling/properties-of-elements-on-uml-use-case-diagrams).  
  
En un diagrama de caso de uso UML, cada elemento del diagrama tiene propiedades. Para ver las propiedades de un elemento, haga clic en el elemento en el diagrama o en **Explorador de modelos UML** y, a continuación, haga clic en **propiedades**. Las propiedades aparecen en la **propiedades** ventana.  
  
> [!NOTE]
>  Este tema trata sobre las propiedades de los elementos de los diagramas de caso de uso UML. Para obtener más información sobre cómo leer diagramas de actividades UML, vea [diagramas de casos de uso de UML: referencia](../modeling/uml-use-case-diagrams-reference.md). Para obtener más información sobre cómo dibujar diagramas de actividades UML, vea [diagramas de casos de uso de UML: instrucciones](../modeling/uml-use-case-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Propiedades de los elementos  
  
|Propiedad|Predeterminado|Elemento|Descripción|  
|--------------|-------------|-------------|-----------------|  
|**Name**|Nombre predeterminado|Todo|Identifica el elemento.|  
|**Nombre completo**|Package :: Name|Todo|Identifica el elemento de forma única. Prefijo con el nombre completo del paquete que lo contiene.|  
|**Los elementos de trabajo**|0 asociados|Todo|Número de elementos de trabajo asociados a este elemento. Para asociar elementos de trabajo, consulte [vincular elementos de modelo y los elementos de trabajo](../modeling/link-model-elements-and-work-items.md).|  
|**Descripción**|(ninguno)|Todo|Aquí puede realizar anotaciones generales sobre el elemento.|  
|**Color**|(valor predeterminado)|Todo|Color de la forma. A diferencia de otras propiedades, no se trata de una propiedad del elemento que muestra la forma.|  
|**Ruta de acceso de imagen**|(ninguno)|Actor|Ruta de acceso del archivo de imagen que debe usarse en vez del icono de actor predeterminado. El icono debe ser un archivo de recursos incluido en el proyecto de Visual Studio.|  
|**Asuntos**|(ninguno)|Caso de uso|Subsistema u otro tipo propietario del caso de uso.<br /><br /> Para establecerlo, puede colocar el caso de uso en un subsistema del diagrama.|  
|**Visibilidad**|Public|Use Case, Actor, Subsystem|**Pública** : es visible globalmente.<br /><br /> **Paquete** : es visible dentro del paquete.|  
|**IsAbstract**|False|Use Case, Actor, Subsystem|Si es true, no se puede crear una instancia del tipo y, además, se entiende como base para la especialización por parte de otras definiciones.|  
|**Is Indirectly Instantiated**|True|Subsistema|El subsistema solo existe como artefacto de diseño. En tiempo de ejecución, solo existen sus partes.|  
|**Hyperlink**|(ninguno)|Artefacto|Dirección URL o ruta de acceso del diagrama o documento para el que el artefacto proporciona un vínculo.|  
  
 Para obtener una lista de las propiedades de las asociaciones, vea [diagramas de clases de propiedades de las asociaciones de UML](../modeling/properties-of-associations-on-uml-class-diagrams.md).  
  
## <a name="see-also"></a>Vea también  
 [Diagramas de casos de uso UML: referencia](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramas de casos de uso de UML: instrucciones](../modeling/uml-use-case-diagrams-guidelines.md)



