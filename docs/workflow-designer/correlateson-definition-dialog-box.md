---
title: Diseñador de flujo de trabajo cuadro de diálogo Definición de CorrelatesOn
description: Obtenga información acerca de cómo puede usar el cuadro de diálogo CorrelatesOn en Diseñador de flujo de trabajo para editar la propiedad CorrelatesOn de una actividad Receive.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 2be38ba9521762c38c629c2817a7c8e8ca5a709a
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438131"
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

## <a name="see-also"></a>Consulte también

- <xref:System.ServiceModel.Activities.Receive>
- [Agregar CorrelationInitializers (cuadro de diálogo)](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Cuadro de diálogo Inicializar correlación](../workflow-designer/initialize-correlation-dialog-box.md)