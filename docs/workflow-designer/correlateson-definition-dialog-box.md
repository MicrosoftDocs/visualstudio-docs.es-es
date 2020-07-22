---
title: Diseñador de flujo de trabajo cuadro de diálogo Definición de CorrelatesOn
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d2db5bbfa4f34d86d3bf20cfe6bcc42b3dc00d0
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876130"
---
# <a name="correlateson-definition-dialog-box"></a>Definición CorrelatesOn (cuadro de diálogo)

El cuadro de diálogo **CorrelatesOn** se utiliza en diseñador de flujo de trabajo para editar la <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propiedad de una <xref:System.ServiceModel.Activities.Receive> actividad. Para obtener más información, vea [Diseñador de actividad Receive](../workflow-designer/receive-activity-designer.md).

La correlación entre las actividades <xref:System.ServiceModel.Activities.Receive> especifica cómo se conectan entre sí diferentes operaciones de servicio en un flujo de trabajo.

En la tabla siguiente se describen los elementos de la interfaz de usuario (UI) del cuadro de diálogo **CorrelatesOn** .

|Elemento de UI|Descripción|
|-|-----------------|
|**CorrelatesWith**|La clase <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para enrutar el mensaje hacia la instancia de flujo de trabajo adecuada.|
|**Consultas XPath**|Un par clave-valor que contiene las consultas que se utilizan para extraer los datos de la correlación de los mensajes entrantes. Este valor corresponde a la <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propiedad. Un objeto <xref:System.ServiceModel.MessageQuerySet> contiene las consultas XPath.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Para iniciar el cuadro de diálogo CorrelatesOn

El diseñador de actividades **Receive** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo, siempre que se coloquen normalmente las actividades. Al quitar el diseñador de actividad, se crea una <xref:System.ServiceModel.Activities.Receive> actividad con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de Receive. Para abrir el cuadro de diálogo **definición de CorrelatesOn** , seleccione el diseñador de actividades **Receive** y, en la cuadrícula de propiedades, seleccione el botón de puntos suspensivos junto al texto de la colección para la propiedad **CorrelatesOn** .

## <a name="see-also"></a>Vea también

- <xref:System.ServiceModel.Activities.Receive>
- [Agregar CorrelationInitializers (cuadro de diálogo)](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Cuadro de diálogo Inicializar correlación](../workflow-designer/initialize-correlation-dialog-box.md)