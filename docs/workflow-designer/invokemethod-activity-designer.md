---
title: "Dise&#241;ador de actividades InvokeMethod | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.InvokeMethod.UI"
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;ador de actividades InvokeMethod
El diseñador **InvokeMethod** se utiliza para crear y configurar una actividad <xref:System.Activities.Statements.InvokeMethod>.  
  
## Actividad InvokeMethod  
 <xref:System.Activities.Statements.InvokeMethod> llama a un método público de un objeto o tipo especificados.  
  
### Utilizar el diseñador de actividades InvokeMethod  
 El diseñador de actividades **de InvokeMethod** se puede encontrar en la categoría **Primitivas** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] de la pestaña **Cuadro de herramientas**. \(De forma alternativa, seleccione **Barra de herramientas** en el menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **InvokeMethod** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se coloquen normalmente las actividades, como en una clase <xref:System.Activities.Statements.Sequence>.De esta forma, se crea una actividad <xref:System.Activities.Statements.InvokeMethod> con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de InvokeMethod.El valor <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **InvokeMethod** o en el cuadro **DisplayName** de la cuadrícula de propiedades.  
  
### Propiedades InvokeMethod  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.InvokeMethod> y se describe cómo se utilizan en el diseñador.Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo de la actividad <xref:System.Activities.Statements.InvokeMethod>.El valor predeterminado es InvokeMethod.<br /><br /> Pese a que la propiedad <xref:System.Activities.Activity.DisplayName%2A> no es obligatoria, se recomienda utilizar una.|  
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|El nombre del método que se va a llamar cuando se ejecute la actividad.El método al que se llama deberá declararse como **public**.Esta propiedad se puede editar en la superficie del diseñador.Es una propiedad obligatoria.|  
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|La colección de parámetros del método al que se ha llamado.Los parámetros se deben agregar a la colección en el mismo orden que aparecen en la firma de método.En la cuadrícula de propiedades, haga clic en el botón con los puntos suspensivos en el campo **Parámetros** para que aparezca el cuadro de diálogo **Parámetros**, donde podrá establecer esta propiedad.Haga clic en el botón **Crear argumento** para agregar los parámetros.|  
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|El valor devuelto de la llamada al método.|  
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|Especifica si el método se llama de forma asincrónica.El valor predeterminado es **False**.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Objeto que contiene el método al que se va a llamar.Esta propiedad se puede editar en la superficie del diseñador.<br /><br /> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> o <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> son obligatorias para que se establezcan.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|El tipo de <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.Esta propiedad se puede editar en la superficie del diseñador.Esta propiedad solo se debe establecer si el método llamado es estático.|  
  
 Para pasar parámetros como un parámetro **out** de C\# \(por ejemplo, `Method1(out myParam)),` debería utilizar **OutArgument** en lugar de **InOutArgument**  
  
 Los métodos **TargetObject** o **Result** con argumentos llamados no se pueden invocar mediante la actividad <xref:System.Activities.Statements.InvokeMethod>.Esto se debe a que la actividad <xref:System.Activities.Statements.InvokeMethod> registra <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> y <xref:System.Activities.Statements.InvokeMethod.Result%2A> en <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
 El algoritmo para registrar los parámetros en <xref:System.Activities.Activity.CacheMetadata%2A> se muestra en la siguiente lista:  
  
1.  Registre el argumento <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.  
  
2.  Registre el argumento <xref:System.Activities.Statements.InvokeMethod.Result%2A>.  
  
3.  Recorra en iteración la colección <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> y registre cada argumento.  
  
 La excepción resultante es de tipo <xref:System.Activities.InvalidWorkflowException> con el siguiente mensaje: 'InvokeMethod': Ya existe una variable, RuntimeArgument o DelegateArgument con el nombre 'TargetObject.'En un ámbito de entorno, los nombres deben ser únicos.  
  
 Esta restricción no se aplica a <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> ni a <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> porque no son los argumentos de flujo de trabajo y por consiguiente, no se registran en la colección <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> de la actividad <xref:System.Activities.Statements.InvokeMethod> en el método <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
## Vea también  
 [Primitivas](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)