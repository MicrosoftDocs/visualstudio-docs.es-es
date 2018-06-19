---
title: Diseñador de flujo de trabajo - cuadro de diálogo de definición de CorrelatesOn
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 490740f8f2682ad6b82bc60edb5d24e6d410b192
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970303"
---
# <a name="correlateson-definition-dialog-box"></a>Definición CorrelatesOn (cuadro de diálogo)

El **CorrelatesOn** cuadro de diálogo se usa en el Diseñador de flujo de trabajo de Windows para editar la <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propiedad de un <xref:System.ServiceModel.Activities.Receive> actividad. Para obtener más información, consulte el [recepción](../workflow-designer/receive-activity-designer.md) tema.

La correlación entre las actividades <xref:System.ServiceModel.Activities.Receive> especifica cómo se conectan entre sí diferentes operaciones de servicio en un flujo de trabajo.

La tabla siguiente describen los elementos de interfaz de usuario de la **CorrelatesOn** cuadro de diálogo.

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**CorrelatesWith**|La clase <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para enrutar el mensaje hacia la instancia de flujo de trabajo adecuada.|
|**Consultas XPath**|Un par clave-valor que contiene las consultas que se utilizan para extraer los datos de la correlación de los mensajes entrantes. Esto corresponde a la propiedad <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>. Un objeto <xref:System.ServiceModel.MessageQuerySet> contiene las consultas XPath.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Para iniciar el cuadro de diálogo CorrelatesOn

El **recepción** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen normalmente las actividades. Esto crea una actividad <xref:System.ServiceModel.Activities.Receive> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Receive. Seleccione el **recepción** Diseñador de actividad y haga clic en botón de los puntos suspensivos junto al texto (colección) para la **CorrelatesOn** propiedad en la cuadrícula de propiedades para el **definición de CorrelatesOn**  que aparezca el cuadro de diálogo.

## <a name="see-also"></a>Vea también

- <xref:System.ServiceModel.Activities.Receive>
- [Cuadro de diálogo Agregar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Agregar cuadro de diálogo de correlación](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Cuadro de diálogo Inicializar correlación](../workflow-designer/initialize-correlation-dialog-box.md)