---
title: 'Cómo: agregar una referencia de salida del proyecto | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bea0f39ae161d8b695f872cb634c35d0cb205c91
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016754"
---
# <a name="how-to-add-a-project-output-reference"></a>Cómo: agregar una referencia de salida del proyecto
  Para implementar ensamblados de proyecto que no sean de SharePoint (o archivos. xap en proyectos de Silverlight) en SharePoint, agréguelos como una referencia de salida del proyecto.

 Este proceso crea una dependencia de compilación de la solución entre los dos proyectos. Los proyectos asociados a las referencias de salida del proyecto se compilan antes de que se compile e implemente el proyecto de SharePoint.

### <a name="to-add-a-project-output-reference"></a>Para agregar una referencia de salida del proyecto

1. Cargue una solución que contenga al menos un proyecto de SharePoint y un proyecto que no sea de SharePoint.

2. En **Explorador de soluciones**, elija un elemento en el nodo de proyecto de SharePoint.

3. En la ventana **propiedades** , elija la propiedad **referencias de resultados del proyecto** y, a continuación, elija el botón de puntos suspensivos (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")) situado junto a él.

4. En el cuadro de diálogo **referencias de salida del proyecto** , elija el botón **Agregar** .

5. En el panel Propiedades, elija la flecha situada junto a la propiedad **tipo de implementación** y, a continuación, elija un valor adecuado para el elemento que no es de SharePoint al que se hace referencia, como **ElementFile**.

6. Elija la flecha situada junto a **nombre del proyecto**, elija el nombre del elemento de proyecto que no es de SharePoint y, a continuación, elija el botón **Aceptar** .

## <a name="see-also"></a>Consulte también
- [Proporcionar información de empaquetado e implementación en los elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Cómo: marcar controles como controles seguros](../sharepoint/how-to-mark-controls-as-safe-controls.md)
- [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
