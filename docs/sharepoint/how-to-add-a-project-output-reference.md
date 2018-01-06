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
ms.assetid: 9d6bc25e-bf0d-4483-a691-2ad7a796fa80
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7ced5627420f5ac90da2cae1a2930dbd0b973dbc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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
  
  