---
title: "Cómo: agregar una referencia de salida del proyecto | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0114971baa164858add68f2f1d6f571407ba5320
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-project-output-reference"></a>Cómo: Agregar una referencia de salida del proyecto
  Para implementar los ensamblados del proyecto no es de SharePoint (o los archivos .xap en proyectos de Silverlight) en SharePoint, agréguelos como una referencia de salida del proyecto.  
  
 Este proceso crea una dependencia de compilación de soluciones entre los dos proyectos. Proyectos asociados con referencias de salida del proyecto se generan antes de que se genera y se implementa el proyecto de SharePoint.  
  
### <a name="to-add-a-project-output-reference"></a>Para agregar una referencia de salida del proyecto  
  
1.  Cargar una solución que contenga al menos un proyecto de SharePoint y un proyecto no es de SharePoint.  
  
2.  En **el Explorador de soluciones**, elija un elemento en el nodo de proyecto de SharePoint.  
  
3.  En el **propiedades** ventana, elija la **referencias de salida del proyecto** propiedad y, a continuación, elija el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ASP. Elipse del Diseñador de Mobile NET")) situado junto a ella.  
  
4.  En el **referencias de salida del proyecto** diálogo cuadro, elija la **agregar** botón.  
  
5.  En el panel Propiedades, elija la flecha situada junto a la **tipo de implementación** propiedad y, a continuación, elija un valor adecuado para el elemento de SharePoint no se hace referencia, como **ElementFile**.  
  
6.  Elija la flecha situada junto a **nombre del proyecto**, elija el nombre del elemento de proyecto no es de SharePoint y, a continuación, elija la **Aceptar** botón.  
  
## <a name="see-also"></a>Vea también  
 [Proporcionar información empaquetado e implementación de elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Cómo: marcar los controles como controles seguros](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  