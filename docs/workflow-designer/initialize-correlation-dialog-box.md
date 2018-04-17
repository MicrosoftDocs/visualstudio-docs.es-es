---
title: Inicializar el cuadro de diálogo de correlación | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aac62d4439c2280e977ef929c79bb103348c170a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="initialize-correlation-dialog-box"></a>Inicializar correlación (cuadro de diálogo)

El **inicializar correlación** cuadro de diálogo se usa en el Diseñador de flujo de trabajo de Windows para editar la <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propiedad de un <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad. Para obtener más información, consulte el [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) tema.

 La tabla siguiente describen los elementos de interfaz de usuario de la **inicializar correlación** cuadro de diálogo.

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**Correlación**|El objeto <xref:System.ServiceModel.Activities.CorrelationHandle> de la correlación que se va a inicializar.|
|**Inicializar en**|Un par clave-valor que contiene los datos que se van a inicializar. Esto corresponde a la propiedad <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Un ejemplo de un par clave-valor válido sería una clave denominada "OrderID" emparejado con una variable denominada OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Para iniciar el cuadro de diálogo Inicializar correlación

-   Haga clic en **vista** en el **InitializeCorrelation** actividad diseñador o seleccione un <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad en [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] y, a continuación, haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propiedad en la cuadrícula de propiedades.

## <a name="see-also"></a>Vea también

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)