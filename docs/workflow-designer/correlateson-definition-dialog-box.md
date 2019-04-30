---
title: 'Diseñador de flujo de trabajo: cuadro de diálogo de definición de CorrelatesOn'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7b7336a3f3b0c2725f4e52116d0add8bf13b90e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949827"
---
# <a name="correlateson-definition-dialog-box"></a>Definición CorrelatesOn (cuadro de diálogo)

El **CorrelatesOn** cuadro de diálogo se usa en el Diseñador de flujo de trabajo para editar el <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propiedad de un <xref:System.ServiceModel.Activities.Receive> actividad. Para obtener más información, consulte [Diseñador de actividad de recepción](../workflow-designer/receive-activity-designer.md).

La correlación entre las actividades <xref:System.ServiceModel.Activities.Receive> especifica cómo se conectan entre sí diferentes operaciones de servicio en un flujo de trabajo.

La tabla siguiente describen los elementos de interfaz de usuario de la **CorrelatesOn** cuadro de diálogo.

|Elemento de la interfaz de usuario|Descripción|
|-|-----------------|
|**CorrelatesWith**|La clase <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para enrutar el mensaje hacia la instancia de flujo de trabajo adecuada.|
|**Consultas XPath**|Un par clave-valor que contiene las consultas que se utilizan para extraer los datos de la correlación de los mensajes entrantes. Este valor corresponde a la <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propiedad. Un objeto <xref:System.ServiceModel.MessageQuerySet> contiene las consultas XPath.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Para iniciar el cuadro de diálogo CorrelatesOn

El **recepción** Diseñador de actividad se puede arrastrar desde **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo, siempre que se coloquen normalmente las actividades. Al colocar el Diseñador de actividad se crea un <xref:System.ServiceModel.Activities.Receive> actividad su valor predeterminado es <xref:System.Activities.Activity.DisplayName%2A> de recepción. Para abrir el **Definition de CorrelatesOn** cuadro de diálogo, seleccione el **recepción** actividad diseñador y, a continuación, en la cuadrícula de propiedades, seleccione el botón de puntos suspensivos junto al texto de la colección para el  **CorrelatesOn** propiedad.

## <a name="see-also"></a>Vea también

- <xref:System.ServiceModel.Activities.Receive>
- [Cuadro de diálogo Agregar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Cuadro de diálogo Inicializar correlación](../workflow-designer/initialize-correlation-dialog-box.md)