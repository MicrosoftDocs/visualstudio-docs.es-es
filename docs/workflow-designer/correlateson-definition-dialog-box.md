---
title: 'Diseñador de flujo de trabajo: cuadro de diálogo de definición de CorrelatesOn'
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4bdc8dd059679c0ba1407585525d30a28dfd8440
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988289"
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
- [Agregar cuadro de diálogo de correlación](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Cuadro de diálogo Inicializar correlación](../workflow-designer/initialize-correlation-dialog-box.md)