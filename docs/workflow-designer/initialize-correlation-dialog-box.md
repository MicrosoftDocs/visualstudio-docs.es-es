---
title: 'Diseñador de flujo de trabajo: inicializar el cuadro de diálogo correlación'
description: Obtenga información sobre cómo puede usar el cuadro de diálogo inicializar correlación en el Diseñador de flujo de trabajo para editar la propiedad CorrelationData de una actividad InitializeCorrelation.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a35911fef39315580f402e174b0f32d443a33cf
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437806"
---
# <a name="initialize-correlation-dialog-box"></a>Inicializar correlación (cuadro de diálogo)

El cuadro de diálogo **inicializar correlación** se utiliza en diseñador de flujo de trabajo para editar la <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propiedad de una <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad. Para obtener más información, vea [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

En la tabla siguiente se describen los elementos de la interfaz de usuario (IU) del cuadro de diálogo **inicializar correlación** :

|Elemento de UI|Descripción|
|-|-----------------|
|**Correlación**|El objeto <xref:System.ServiceModel.Activities.CorrelationHandle> de la correlación que se va a inicializar.|
|**Inicializar el**|Un par clave-valor que contiene los datos que se van a inicializar. Este valor corresponde a la <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propiedad. Un ejemplo de par clave-valor válido es una clave denominada "OrderID" emparejada con una variable denominada OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Para iniciar el cuadro de diálogo Inicializar correlación

Haga clic en **Ver** en el diseñador de actividades **InitializeCorrelation** o seleccione una <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad en diseñador de flujo de trabajo. A continuación, haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propiedad en la cuadrícula de propiedades.

## <a name="see-also"></a>Consulte también

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
