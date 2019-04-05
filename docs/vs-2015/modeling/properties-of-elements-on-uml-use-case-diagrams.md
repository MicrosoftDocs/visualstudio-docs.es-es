---
title: Propiedades de elementos de UML diagramas de casos de uso | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties
- vs.teamarch.usecasediagram.shapes.properties
helpviewer_keywords:
- use case diagrams, properties
ms.assetid: 2728fb26-a275-4fce-8a2c-5a78af6bee04
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dbe2a9f3d46be72ae1e463da7c6173ef0571bc89
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988181"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>Propiedades de los elementos de diagramas de casos de uso UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En un diagrama de caso de uso UML, cada elemento del diagrama tiene propiedades. Para ver las propiedades de un elemento, haga clic en el elemento en el diagrama o en **Explorador de modelos UML** y, a continuación, haga clic en **propiedades**. Las propiedades aparecen en la **propiedades** ventana.  
  
> [!NOTE]
>  Este tema trata sobre las propiedades de los elementos de los diagramas de caso de uso UML. Para obtener más información sobre cómo leer diagramas de actividades UML, vea [diagramas de casos de uso de UML: referencia](../modeling/uml-use-case-diagrams-reference.md). Para obtener más información sobre cómo dibujar diagramas de actividades UML, vea [diagramas de casos de uso de UML: Directrices](../modeling/uml-use-case-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Propiedades de los elementos  
  
|Property|Default|Elemento|Descripción|  
|--------------|-------------|-------------|-----------------|  
|**Name**|Nombre predeterminado|Todas|Identifica el elemento.|  
|**Nombre completo**|Paquete:: Name|Todas|Identifica de forma única el elemento. Prefijo con el nombre completo del paquete que lo contiene.|  
|**Los elementos de trabajo**|0 asociados|Todas|Número de elementos de trabajo asociados a este elemento. Para asociar elementos de trabajo, consulte [vincular elementos de modelo y los elementos de trabajo](../modeling/link-model-elements-and-work-items.md).|  
|**Descripción**|(ninguno)|Todas|Aquí puede realizar anotaciones generales sobre el elemento.|  
|**Color**|(predeterminado)|Todas|Color de la forma. A diferencia de otras propiedades, no se trata de una propiedad del elemento que muestra la forma.|  
|**Ruta de acceso de imagen**|(ninguno)|Actor|Ruta de acceso del archivo de imagen que debe usarse en vez del icono de actor predeterminado. El icono debe ser un archivo de recursos incluido en el proyecto de Visual Studio.|  
|**Asuntos**|(ninguno)|Caso de uso|Subsistema u otro tipo propietario del caso de uso.<br /><br /> Para establecerlo, puede colocar el caso de uso en un subsistema del diagrama.|  
|**Visibilidad**|Public|Use Case, Actor, Subsystem|**Pública** : es visible globalmente.<br /><br /> **Paquete** : es visible dentro del paquete.|  
|**IsAbstract**|False|Use Case, Actor, Subsystem|Si es true, no se puede crear una instancia del tipo y, además, se entiende como base para la especialización por parte de otras definiciones.|  
|**Is Indirectly Instantiated**|True|Subsistema|El subsistema solo existe como artefacto de diseño. En tiempo de ejecución, solo existen sus partes.|  
|**Hyperlink**|(ninguno)|Artifact|Dirección URL o ruta de acceso del diagrama o documento para el que el artefacto proporciona un vínculo.|  
  
 Para obtener una lista de las propiedades de las asociaciones, vea [diagramas de clases de propiedades de las asociaciones de UML](../modeling/properties-of-associations-on-uml-class-diagrams.md).  
  
## <a name="see-also"></a>Vea también  
 [Diagramas de casos de uso UML: Referencia](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramas de casos de uso UML: directrices](../modeling/uml-use-case-diagrams-guidelines.md)
