---
title: 'Cómo: agregar una referencia de salida del proyecto | Documentos de Microsoft'
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
ms.openlocfilehash: 97bfe044ef89691afdb1a8e845867ce2e177dbb9
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767968"
---
# <a name="how-to-add-a-project-output-reference"></a>Cómo: agregar una referencia de salida del proyecto
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
  
  