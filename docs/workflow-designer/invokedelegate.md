---
title: "InvokeDelegate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "InvokeDelegate Designer"
  - "System.Activities.Statements.InvokeDelegate.UI"
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 3
---
# InvokeDelegate
El diseñador de **InvokeDelegate** se usa para crear y configurar una actividad <xref:System.Activities.Statements.InvokeDelegate>.  
  
## La actividad InvokeDelegate  
 <xref:System.Activities.Statements.InvokeDelegate> llama a un delegado público.  
  
### Usar el diseñador de actividades InvokeDelegate  
 El diseñador de actividades **InvokeDelegate** se puede encontrar en la categoría **Primitivas** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] de la pestaña **Cuadro de herramientas**. \(De forma alternativa, seleccione **Barra de herramientas** en el menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **InvokeDelegate** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se coloquen normalmente las actividades, como en una clase <xref:System.Activities.Statements.Sequence>.De esta forma, se crea una actividad <xref:System.Activities.Statements.InvokeDelegate> con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de InvokeDelegate.<xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **InvokeDelegate** o en el cuadro **DisplayName** de la cuadrícula de propiedades.  
  
### Las propiedades de InvokeDelegate  
 En la tabla siguiente se muestran las propiedades de <xref:System.Activities.Statements.InvokeDelegate> y se describe cómo se usan en el diseñador.Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo de la actividad <xref:System.Activities.Statements.InvokeDelegate>.El valor predeterminado es InvokeDelegate.<br /><br /> Aunque el valor de propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|  
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|El nombre del <xref:System.Activities.Statements.ActivityDelegate> al que se va a llamar cuando se ejecute la actividad.Esta propiedad se puede editar en la superficie del diseñador.Es una propiedad obligatoria.|  
|<xref:System.Activities.Statements.InvokeMethod.DelegateArguments%2A>|False|La colección de argumentos del delegado llamado.Las claves son los nombres de los objetos <xref:System.Activities.Statements.ActivityDelegateParameter> incluidos en el <xref:System.Activities.Statements.ActivityDelegate> y los valores son los argumentos cuyas expresiones se evalúan y asignan a los objetos <xref:System.Activities.Statements.ActivityDelegateParameter> correspondientes.En la cuadrícula de propiedades, haga clic en el botón con los puntos suspensivos en el campo **DelegateArguments** para que aparezca el cuadro de diálogo **DelegateArguments**, donde podrá establecer esta propiedad.Haga clic en el campo **Crear argumento** para agregar los argumentos.|  
  
## Vea también  
 [Definir y consumir delegados de actividad en el Diseñador de flujo de trabajo](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)