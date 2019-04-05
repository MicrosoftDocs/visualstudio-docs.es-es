---
title: Cuadro de diálogo de definición de CorrelatesOn | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fd03e1a8615e75d3f00f79eb10b7a7ff97f0eb33
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "59002804"
---
# <a name="correlateson-definition-dialog-box"></a>Definición CorrelatesOn (cuadro de diálogo)
El **CorrelatesOn** cuadro de diálogo se usa en [!INCLUDE[wfd1](../includes/wfd1-md.md)] para editar el <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propiedad de un <xref:System.ServiceModel.Activities.Receive> actividad. [!INCLUDE[crdefault](../includes/crdefault-md.md)] el [recepción](../workflow-designer/receive-activity-designer.md) tema.  
  
 La correlación entre las actividades <xref:System.ServiceModel.Activities.Receive> especifica cómo se conectan entre sí diferentes operaciones de servicio en un flujo de trabajo.  
  
 La tabla siguiente describen los elementos de interfaz de usuario de la **CorrelatesOn** cuadro de diálogo.  
  
|Elemento de la interfaz de usuario|Descripción|  
|----------------|-----------------|  
|**CorrelatesWith**|La clase <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para enrutar el mensaje hacia la instancia de flujo de trabajo adecuada.|  
|**Consultas XPath**|Un par clave-valor que contiene las consultas que se utilizan para extraer los datos de la correlación de los mensajes entrantes. Esto corresponde a la propiedad <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>. Un objeto <xref:System.ServiceModel.MessageQuerySet> contiene las consultas XPath.|  
  
## <a name="to-launch-the-correlateson-dialog-box"></a>Para iniciar el cuadro de diálogo CorrelatesOn  
 El **recepción** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie donde se coloquen normalmente las actividades. Esto crea una actividad <xref:System.ServiceModel.Activities.Receive> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Receive. Seleccione el **recepción** Diseñador de actividad y haga clic en el botón de puntos suspensivos situado junto al texto (colección) para el **CorrelatesOn** propiedad en la cuadrícula de propiedades para el **Definition de CorrelatesOn**  cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ServiceModel.Activities.Receive>   
 [Agregar cuadro de diálogo CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md)   
 [Cuadro de diálogo Inicializar correlación](../workflow-designer/initialize-correlation-dialog-box.md)