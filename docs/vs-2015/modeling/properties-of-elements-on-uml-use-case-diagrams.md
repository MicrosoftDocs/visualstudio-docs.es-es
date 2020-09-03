---
title: Propiedades de los elementos de diagramas de casos de uso de UML | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db3dc649d979c87960a42d38ffa211e352be175b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671412"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>Propiedades de los elementos de diagramas de casos de uso UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En un diagrama de caso de uso UML, cada elemento del diagrama tiene propiedades. Para ver las propiedades de un elemento, haga clic con el botón secundario en el elemento del diagrama o en el **Explorador de modelos UML** y, a continuación, haga clic en **propiedades**. Las propiedades aparecen en la ventana **propiedades** .

> [!NOTE]
> Este tema trata sobre las propiedades de los elementos de los diagramas de caso de uso UML. Para obtener más información sobre cómo leer diagramas de actividades UML, vea [diagramas de casos de uso de UML: referencia](../modeling/uml-use-case-diagrams-reference.md). Para obtener más información sobre cómo dibujar diagramas de actividades UML, vea [diagramas de casos de uso de UML: instrucciones](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Propiedades de los elementos

|Propiedad|Valor predeterminado|Elemento|Descripción|
|--------------|-------------|-------------|-----------------|
|**Name**|Nombre predeterminado|Todo|Identifica el elemento.|
|**Nombre completo**|Package :: Name|Todo|Identifica de forma única el elemento. Prefijo con el nombre completo del paquete que lo contiene.|
|**Elementos de trabajo**|0 asociados|Todo|Número de elementos de trabajo asociados a este elemento. Para asociar elementos de trabajo, vea [vincular elementos de modelo y elementos de trabajo](../modeling/link-model-elements-and-work-items.md).|
|**Descripción**|(ninguno)|Todo|Aquí puede realizar anotaciones generales sobre el elemento.|
|**Color**|(predeterminado).|Todo|Color de la forma. A diferencia de otras propiedades, no se trata de una propiedad del elemento que muestra la forma.|
|**Ruta de la imagen**|(ninguno)|Actor|Ruta de acceso del archivo de imagen que debe usarse en vez del icono de actor predeterminado. El icono debe ser un archivo de recursos incluido en el proyecto de Visual Studio.|
|**Cuestiones**|(ninguno)|Caso de uso|Subsistema u otro tipo propietario del caso de uso.<br /><br /> Para establecerlo, puede colocar el caso de uso en un subsistema del diagrama.|
|**Visibilidad**|Público|Use Case, Actor, Subsystem|**Pública** : es visible globalmente.<br /><br /> **Package** : es visible dentro del paquete.|
|**IsAbstract**|Falso|Use Case, Actor, Subsystem|Si es true, no se puede crear una instancia del tipo y, además, se entiende como base para la especialización por parte de otras definiciones.|
|**Se crean instancias indirectamente**|Verdadero|Subsystem|El subsistema solo existe como artefacto de diseño. En tiempo de ejecución, solo existen sus partes.|
|**Hipervínculo**|(ninguno)|Artefacto|Dirección URL o ruta de acceso del diagrama o documento para el que el artefacto proporciona un vínculo.|

 Para obtener una lista de las propiedades de las asociaciones, vea [propiedades de las asociaciones de diagramas de clases de UML](../modeling/properties-of-associations-on-uml-class-diagrams.md).

## <a name="see-also"></a>Consulte también
 [Diagramas de casos de uso de UML: referencia](../modeling/uml-use-case-diagrams-reference.md) [diagramas de casos de uso de UML: instrucciones](../modeling/uml-use-case-diagrams-guidelines.md)
