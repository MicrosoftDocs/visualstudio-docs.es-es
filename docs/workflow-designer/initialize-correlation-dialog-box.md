---
title: 'Diseñador de flujo de trabajo: inicializar el cuadro de diálogo correlación'
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
ms.openlocfilehash: 04f0a3bb70dbab31e0faa5c38caac9b54c6154fe
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114776"
---
# <a name="initialize-correlation-dialog-box"></a>Inicializar correlación (cuadro de diálogo)

El cuadro de diálogo **inicializar correlación** se utiliza en diseñador de flujo de trabajo para editar la propiedad <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> de una actividad <xref:System.ServiceModel.Activities.InitializeCorrelation>. Para obtener más información, vea [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

En la tabla siguiente se describen los elementos de la interfaz de usuario (IU) del cuadro de diálogo **inicializar correlación** :

|Elemento de la interfaz de usuario|Descripción|
|-|-----------------|
|**Correlación**|El objeto <xref:System.ServiceModel.Activities.CorrelationHandle> de la correlación que se va a inicializar.|
|**Inicializar el**|Un par clave-valor que contiene los datos que se van a inicializar. Este valor corresponde a la propiedad <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Un ejemplo de par clave-valor válido es una clave denominada "OrderID" emparejada con una variable denominada OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Para iniciar el cuadro de diálogo Inicializar correlación

Haga clic en **Ver** en el diseñador de actividades **InitializeCorrelation** o seleccione una actividad <xref:System.ServiceModel.Activities.InitializeCorrelation> en diseñador de flujo de trabajo. A continuación, haga clic en el botón de puntos suspensivos junto a la propiedad <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> en la cuadrícula de propiedades.

## <a name="see-also"></a>Vea también

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
