---
title: Cuadro de diálogo inicializar correlación | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ab913027a6a992494dad609b98ab11dbc6ae61c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659052"
---
# <a name="initialize-correlation-dialog-box"></a>Inicializar correlación (cuadro de diálogo)
El cuadro de diálogo **inicializar correlación** se utiliza en [!INCLUDE[wfd1](../includes/wfd1-md.md)] para editar la <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propiedad de una <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad. [!INCLUDE[crdefault](../includes/crdefault-md.md)] el tema [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) .

 En la tabla siguiente se describen los elementos de la interfaz de usuario (IU) del cuadro de diálogo **inicializar correlación** .

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**correlación**|El objeto <xref:System.ServiceModel.Activities.CorrelationHandle> de la correlación que se va a inicializar.|
|**Inicializar el**|Un par clave-valor que contiene los datos que se van a inicializar. Esto corresponde a la propiedad <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Un ejemplo de par clave-valor válido sería una clave denominada "OrderID" que se asocia a una variable denominada OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Para iniciar el cuadro de diálogo Inicializar correlación

- Haga clic en **Ver** en el diseñador de actividades **InitializeCorrelation** o seleccione una <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad en [!INCLUDE[wfd2](../includes/wfd2-md.md)] y, a continuación, haga clic en el botón de puntos suspensivos junto a la <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propiedad en la cuadrícula de propiedades.

## <a name="see-also"></a>Consulte también
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)