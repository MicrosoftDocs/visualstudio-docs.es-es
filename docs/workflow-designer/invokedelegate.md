---
title: InvokeDelegate | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: "3"
ms.author: sdanie
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 56b132403d51a591a8832c1417bec73bde442266
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="invokedelegate"></a>InvokeDelegate
El **InvokeDelegate** diseñador se utiliza para crear y configurar un <xref:System.Activities.Statements.InvokeDelegate> actividad.  
  
## <a name="the-invokedelegate-activity"></a>Actividad InvokeDelegate  
 <xref:System.Activities.Statements.InvokeDelegate> llama a un delegado público.  
  
### <a name="using-the-invokedelegate-activity-designer"></a>Usar el diseñador de actividad InvokeDelegate  
 El **InvokeDelegate** Diseñador de actividad puede encontrarse en el **primitivas** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas** ficha [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (o bien, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **InvokeDelegate** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] expuesta donde se coloquen normalmente las actividades, por ejemplo, como en un <xref:System.Activities.Statements.Sequence>. De esta forma, se crea una actividad <xref:System.Activities.Statements.InvokeDelegate> con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de InvokeDelegate. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **InvokeDelegate** Diseñador de actividad o en la **DisplayName** cuadro de la cuadrícula de propiedades.  
  
### <a name="the-invokedelegate-properties"></a>Las propiedades de InvokeDelegate  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.InvokeDelegate> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.InvokeDelegate>. El valor predeterminado es InvokeDelegate.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|  
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|El nombre del <xref:System.Activities.ActivityDelegate> que se va a llamar cuando se ejecute la actividad. Esta propiedad se puede editar en la superficie del diseñador. Es una propiedad obligatoria.|  
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|La colección de argumentos del delegado llamado. Las claves son los nombres de los objetos de parámetro en el <xref:System.Activities.ActivityDelegate> y los valores son los argumentos cuyas expresiones se evalúan y se asignan a los objetos de parámetro correspondiente. En la cuadrícula de propiedades, haga clic en el botón de puntos suspensivos en el **DelegateArguments** campo, muestra la **DelegateArguments** cuadro de diálogo que le permite establecer esta propiedad. Haga clic en el **crear argumento** campo que desea agregar los argumentos.|  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Definir y consumir delegados de actividad en el Diseñador de flujo de trabajo](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)