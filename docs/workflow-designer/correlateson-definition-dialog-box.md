---
title: Diseñador de flujo de trabajo cuadro de diálogo Definición de CorrelatesOn
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 401f72f55f23779f7c6257437034a4ebc294d219
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650598"
---
# <a name="correlateson-definition-dialog-box"></a>Definición CorrelatesOn (cuadro de diálogo)

El cuadro de diálogo **CorrelatesOn** se utiliza en diseñador de flujo de trabajo para editar la propiedad <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> de una actividad <xref:System.ServiceModel.Activities.Receive>. Para obtener más información, vea [Diseñador de actividad Receive](../workflow-designer/receive-activity-designer.md).

La correlación entre las actividades <xref:System.ServiceModel.Activities.Receive> especifica cómo se conectan entre sí diferentes operaciones de servicio en un flujo de trabajo.

En la tabla siguiente se describen los elementos de la interfaz de usuario (UI) del cuadro de diálogo **CorrelatesOn** .

|Elemento de la interfaz de usuario|Descripción|
|-|-----------------|
|**CorrelatesWith**|La clase <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para enrutar el mensaje hacia la instancia de flujo de trabajo adecuada.|
|**Consultas XPath**|Un par clave-valor que contiene las consultas que se utilizan para extraer los datos de la correlación de los mensajes entrantes. Este valor corresponde a la propiedad <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>. Un objeto <xref:System.ServiceModel.MessageQuerySet> contiene las consultas XPath.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Para iniciar el cuadro de diálogo CorrelatesOn

El diseñador de actividades **Receive** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo, siempre que se coloquen normalmente las actividades. Al quitar el diseñador de actividad, se crea una actividad <xref:System.ServiceModel.Activities.Receive> con una <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Receive. Para abrir el cuadro de diálogo **definición de CorrelatesOn** , seleccione el diseñador de actividades **Receive** y, en la cuadrícula de propiedades, seleccione el botón de puntos suspensivos junto al texto de la colección para la propiedad **CorrelatesOn** .

## <a name="see-also"></a>Vea también

- <xref:System.ServiceModel.Activities.Receive>
- [Cuadro de diálogo Agregar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Cuadro de diálogo Inicializar correlación](../workflow-designer/initialize-correlation-dialog-box.md)