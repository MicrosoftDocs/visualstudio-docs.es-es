---
title: "Diseñador de actividades InvokeMethod | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 1fe242e3e4fd2a885373d776f79f50071fa83c1f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="invokemethod-activity-designer"></a>Diseñador de actividades InvokeMethod
**InvokeMethod** diseñador se utiliza para crear y configurar un <xref:System.Activities.Statements.InvokeMethod> actividad.  
  
## <a name="the-invokemethod-activity"></a>Actividad InvokeMethod  
 <xref:System.Activities.Statements.InvokeMethod> llama a un método público de un objeto o tipo especificados.  
  
### <a name="using-the-invokemethod-activity-designer"></a>Utilizar el diseñador de actividades InvokeMethod  
 El **InvokeMethod** Diseñador de actividad puede encontrarse en el **primitivas** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas** ficha [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (o bien, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **InvokeMethod** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] expuesta donde se coloquen normalmente las actividades, por ejemplo, como en un <xref:System.Activities.Statements.Sequence>. De esta forma, se crea una actividad <xref:System.Activities.Statements.InvokeMethod> con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de InvokeMethod. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **InvokeMethod** Diseñador de actividad o en la **DisplayName** cuadro de la cuadrícula de propiedades.  
  
### <a name="the-invokemethod-properties"></a>Propiedades InvokeMethod  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.InvokeMethod> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.InvokeMethod>. El valor predeterminado es InvokeMethod.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|  
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|El nombre del método que se va a llamar cuando se ejecute la actividad. El método llamado debe declararse como **público**. Esta propiedad se puede editar en la superficie del diseñador. Es una propiedad obligatoria.|  
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|La colección de parámetros del método al que se ha llamado. Los parámetros se deben agregar a la colección en el mismo orden que aparecen en la firma de método. En la cuadrícula de propiedades, haga clic en el botón de puntos suspensivos en el **parámetros** campo, muestra la **parámetros** cuadro de diálogo que le permite establecer esta propiedad. Haga clic en el **crear argumento** botón para agregar los parámetros.|  
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|El valor devuelto de la llamada al método.|  
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|Especifica si el método se llama de forma asincrónica. El valor predeterminado es **False**.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Objeto que contiene el método al que se va a llamar. Esta propiedad se puede editar en la superficie del diseñador.<br /><br /> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> o <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> son obligatorias para que se establezcan.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Tipo de <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Esta propiedad se puede editar en la superficie del diseñador. Esta propiedad solo se debe establecer si el método llamado es estático.|  
  
 Pasar parámetros como C# **out** parámetro (por ejemplo, `Method1(out myParam)),` debe usar **OutArgument** en lugar de **InOutArgument**  
  
 Métodos con argumentos llamados **TargetObject** o **resultado** no se puede invocar mediante la <xref:System.Activities.Statements.InvokeMethod> actividad. Esto se debe a que la actividad <xref:System.Activities.Statements.InvokeMethod> registra <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> y <xref:System.Activities.Statements.InvokeMethod.Result%2A> en <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
 El algoritmo para registrar los parámetros en <xref:System.Activities.Activity.CacheMetadata%2A> se muestra en la siguiente lista:  
  
1.  Registre el argumento <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.  
  
2.  Registre el argumento <xref:System.Activities.Statements.InvokeMethod.Result%2A>.  
  
3.  Recorra en iteración la colección <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> y registre cada argumento.  
  
 La excepción resultante es de tipo <xref:System.Activities.InvalidWorkflowException> con el siguiente mensaje: 'InvokeMethod': Ya existe una variable, RuntimeArgument o DelegateArgument con el nombre 'TargetObject.' En un ámbito de entorno, los nombres deben ser únicos.  
  
 Esta restricción no se aplica a <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> ni a <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> porque no son los argumentos de flujo de trabajo y por consiguiente, no se registran en la colección <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> de la actividad <xref:System.Activities.Statements.InvokeMethod> en el método <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Tipos primitivos](../workflow-designer/primitives-activity-designers.md)   
 [Asignar](../workflow-designer/assign-activity-designer.md)   
 [Retraso](../workflow-designer/delay-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)