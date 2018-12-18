---
title: Inicializar el cuadro de diálogo de correlación | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 0782053ca12efbb1c19433ab395176f2545a67c3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49278569"
---
# <a name="initialize-correlation-dialog-box"></a>Inicializar correlación (cuadro de diálogo)
El **inicializar correlación** cuadro de diálogo se usa en [!INCLUDE[wfd1](../includes/wfd1-md.md)] para editar el <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propiedad de un <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad. [!INCLUDE[crdefault](../includes/crdefault-md.md)] el [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) tema.  
  
 La tabla siguiente describen los elementos de interfaz de usuario de la **inicializar correlación** cuadro de diálogo.  
  
|Elemento de la interfaz de usuario|Descripción|  
|----------------|-----------------|  
|**Correlación**|El objeto <xref:System.ServiceModel.Activities.CorrelationHandle> de la correlación que se va a inicializar.|  
|**Inicializar en**|Un par clave-valor que contiene los datos que se van a inicializar. Esto corresponde a la propiedad <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Un ejemplo de par clave-valor válido sería una clave denominada "OrderID" que se asocia a una variable denominada OrderID.|  
  
## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Para iniciar el cuadro de diálogo Inicializar correlación  
  
-   Haga clic en **vista** en el **InitializeCorrelation** actividad diseñador o seleccione un <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad en [!INCLUDE[wfd2](../includes/wfd2-md.md)] y, a continuación, haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propiedad en la cuadrícula de propiedades.  
  
## <a name="see-also"></a>Vea también  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)