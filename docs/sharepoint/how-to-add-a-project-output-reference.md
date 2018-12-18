---
title: 'Cómo: agregar una referencia de salida del proyecto | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 47b6a3d164bbe1ddcda6d131275427fb1f815198
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755482"
---
# <a name="how-to-add-a-project-output-reference"></a>Cómo: agregar una referencia de salida del proyecto
  Para implementar ensamblados de proyecto que no es de SharePoint (o archivos .xap en proyectos de Silverlight) en SharePoint, debe agregarlos como una referencia de salida del proyecto.  
  
 Este proceso crea una dependencia de compilación de soluciones entre los dos proyectos. Antes de que se genera e implementa el proyecto de SharePoint, se compilan los proyectos asociados a referencias de salida del proyecto.  
  
### <a name="to-add-a-project-output-reference"></a>Para agregar una referencia de salida del proyecto
  
1.  Cargar una solución que contenga al menos un proyecto de SharePoint y un proyecto que no es de SharePoint.  
  
2.  En **el Explorador de soluciones**, elija un elemento en el nodo de proyecto de SharePoint.  
  
3.  En el **propiedades** ventana, elija el **Project Output References** propiedad y, a continuación, elija el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ASP. Elipse del Diseñador de NET Mobile")) situado junto a ella.  
  
4.  En el **Project Output References** diálogo cuadro, elija el **agregar** botón.  
  
5.  En el panel Propiedades, elija la flecha situada junto a la **tipo de implementación** propiedad y, a continuación, elija un valor apropiado para el elemento que no es de SharePoint que se hace referencia, como **ElementFile**.  
  
6.  Elija la flecha situada junto a **nombre del proyecto**, elija el nombre del elemento de proyecto que no es de SharePoint y, a continuación, elija el **Aceptar** botón.  
  
## <a name="see-also"></a>Vea también
 [Proporcionar información de empaquetado e implementación de elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Cómo: marcar los controles como seguros](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
