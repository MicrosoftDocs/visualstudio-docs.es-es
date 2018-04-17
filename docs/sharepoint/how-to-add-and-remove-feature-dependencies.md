---
title: 'Cómo: agregar y quitar dependencias de características | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: eeda1b63132de49785b2f2ba5743dbd683504a71
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Cómo: Agregar y quitar dependencias de características
  La característica de SharePoint puede depender de otras características para la funcionalidad o datos. En estos casos, puede marcar estas otras características como dependencias para la característica. De esta manera, el servidor de SharePoint se asegura de que se activan las características dependientes antes de que la característica está activada.  
  
## <a name="adding-dependencies"></a>Adición de dependencias  
 Puede agregar otras características de la solución como dependencias. De esta manera, puede asegurarse de que requiere características instaladas y activar antes de que se instala la característica.  
  
#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Para agregar una dependencia en una característica de la solución  
  
1.  Abra el Diseñador de características, expanda el **dependencias de activación de características** nodo y, a continuación, elija la **agregar** botón.  
  
2.  En el **agregar dependencias de activación de características** diálogo cuadro, elija la **agregar una dependencia en las características de la solución** botón de opción, elija el título de la característica que desea agregar como una dependencia y, a continuación, Elija la **agregar** botón.  
  
     Puede agregar más de una característica seleccionando varios títulos mientras presiona la tecla Ctrl.  
  
## <a name="adding-custom-dependencies"></a>Agregar dependencias personalizadas  
 Puede agregar características que ya están implementadas en un servidor de SharePoint como una dependencia. De esta manera, el proceso de activación de SharePoint comprueba para asegurarse de que se activan todas las características dependientes antes de instala la característica.  
  
#### <a name="to-add-a-dependency-by-the-feature-id"></a>Para agregar una dependencia por el identificador de característica  
  
1.  Abra el Diseñador de características, expanda el **dependencias de activación de características** nodo y, a continuación, elija la **agregar** botón.  
  
2.  En el **agregar dependencias de activación de características** diálogo cuadro, elija la **agregar una dependencia personalizada** botón de opción.  
  
3.  En el **Id. de característica** texto cuadro, escriba el GUID de la característica que desea marcar como una dependencia de activación y, a continuación, elija la **agregar** botón.  
  
## <a name="editing-custom-dependencies"></a>Modificar dependencias personalizadas  
 Puede modificar las dependencias personalizadas que agregó anteriormente. Sin embargo, las características dependientes que están en la solución solo va a quitar, no modificar.  
  
#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>Para cambiar una dependencia de una característica de la solución  
  
1.  Abra el Diseñador de características y, a continuación, expanda el **dependencias de activación de características** nodo.  
  
2.  Elija el nombre de la característica que desea modificar y, a continuación, elija la **editar** botón.  
  
3.  En el **Editar dependencia de activación de características personalizada** cuadro de diálogo, cambie el título, el Id. de característica o la descripción y, a continuación, elija la **enviar** botón.  
  
## <a name="removing-dependencies"></a>Quitar las dependencias  
  
#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>Para quitar una dependencia de una característica en la solución  
  
1.  En el Diseñador de características, expanda el **dependencias de activación de características** nodo, elija el nombre de la característica que desea quitar y, a continuación, elija la **quitar** botón.  
  
## <a name="see-also"></a>Vea también  
 [Crear características de SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Cómo: personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Cómo: Agregar y quitar elementos de las características de SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  