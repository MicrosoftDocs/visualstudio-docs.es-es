---
title: Referencia de API de extensibilidad del modelado UML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending
- UML API
- UML model, API
ms.assetid: 2b2ffe93-c358-4d28-a5e5-3d0474629b58
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: dff485db59f418fe05cd586335b6f9ceae153428
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785045"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>Referencia de la API para la extensibilidad del modelado UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede escribir código de programa para leer y modificar los modelos creados con Visual Studio. La referencia de la API proporciona información sobre las clases específicas para ayudarle con esto. Para obtener más información orientada a tareas, vea los temas bajo [modelos y diagramas UML ampliar](../modeling/extend-uml-models-and-diagrams.md). Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="assemblies"></a>Ensamblados  
  
|Ensamblado|Qué permite hacer|  
|--------------|--------------------------------|  
|Microsoft.VisualStudio.Uml.Interfaces.dll|-Leer y cambiar los elementos del modelo, como IUseCase, IAssociation y así sucesivamente.<br />-Navegar por las relaciones entre elementos.<br /><br /> Los espacios de nombres y tipos se corresponden con los que se definen en la especificación de UML.|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll|-Crear nuevas instancias de los elementos del modelo<br />-Acceder y modificar formas y diagramas.|  
  
## <a name="see-also"></a>Vea también  
 [Ampliar modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Referencia de API para modelar el SDK de Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)



