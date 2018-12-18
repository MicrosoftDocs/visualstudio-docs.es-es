---
title: 'Diseñador de flujo de trabajo: cuadro de diálogo inicializar correlación'
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: edfdef1c1f946e2c5f677d0ff1578a40ea7bcd8f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906239"
---
# <a name="initialize-correlation-dialog-box"></a>Inicializar correlación (cuadro de diálogo)

El **inicializar correlación** cuadro de diálogo se usa en el Diseñador de flujo de trabajo para editar el <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propiedad de un <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad. Para obtener más información, consulte [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

La tabla siguiente describen los elementos de interfaz de usuario de la **inicializar correlación** cuadro de diálogo:

|Elemento de la interfaz de usuario|Descripción|
|-|-----------------|
|**Correlación**|El objeto <xref:System.ServiceModel.Activities.CorrelationHandle> de la correlación que se va a inicializar.|
|**Inicializar en**|Un par clave-valor que contiene los datos que se van a inicializar. Este valor corresponde a la <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propiedad. Un ejemplo de un par clave/valor válido es una clave denominada "OrderID" se empareja con una variable denominada OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Para iniciar el cuadro de diálogo Inicializar correlación

Haga clic en **vista** en el **InitializeCorrelation** actividad diseñador o seleccione un <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad en el Diseñador de flujo de trabajo. A continuación, haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propiedad en la cuadrícula de propiedades.

## <a name="see-also"></a>Vea también

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)