---
title: Diseñador de actividades InvokeMethod | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fcfba979ba7fce4aeffab1fe9e9a5a3728e513af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658999"
---
# <a name="invokemethod-activity-designer"></a>Diseñador de actividades InvokeMethod
El diseñador **InvokeMethod** se usa para crear y configurar una <xref:System.Activities.Statements.InvokeMethod> actividad.

## <a name="the-invokemethod-activity"></a>Actividad InvokeMethod
 <xref:System.Activities.Statements.InvokeMethod> llama a un método público de un objeto o tipo especificados.

### <a name="using-the-invokemethod-activity-designer"></a>Utilizar el diseñador de actividades InvokeMethod
 El diseñador de actividades **InvokeMethod** se puede encontrar en la categoría **primitivas** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** [!INCLUDE[wfd2](../includes/wfd2-md.md)] . (de forma alternativa, seleccione **barra de herramientas** en el menú **Ver** o Ctrl + Alt + X).

 El diseñador de actividades **InvokeMethod** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie donde se colocan normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence> . De esta forma, se crea una actividad <xref:System.Activities.Statements.InvokeMethod> con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de InvokeMethod. <xref:System.Activities.Activity.DisplayName%2A>Se puede editar en el encabezado del diseñador de actividades **InvokeMethod** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-invokemethod-properties"></a>Propiedades InvokeMethod
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.InvokeMethod> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nombre de propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nombre descriptivo de la actividad <xref:System.Activities.Statements.InvokeMethod>. El valor predeterminado es InvokeMethod.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Verdadero|El nombre del método que se va a llamar cuando se ejecute la actividad. El método al que se llama debe declararse como **público**. Esta propiedad se puede editar en la superficie del diseñador. Es una propiedad obligatoria.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|Falso|La colección de parámetros del método al que se ha llamado. Los parámetros se deben agregar a la colección en el mismo orden que aparecen en la firma de método. En la cuadrícula de propiedades, haga clic en el botón de puntos suspensivos del campo **parámetros** y se mostrará el cuadro de diálogo **parámetros** para permitirle establecer esta propiedad. Haga clic en el botón **crear argumento** para agregar los parámetros.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|Falso|El valor devuelto de la llamada al método.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Verdadero|Especifica si el método se llama de forma asincrónica. El valor predeterminado es **False**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|Falso|Objeto que contiene el método al que se va a llamar. Esta propiedad se puede editar en la superficie del diseñador.<br /><br /> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> o <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> son obligatorias para que se establezcan.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|Falso|Tipo de <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Esta propiedad se puede editar en la superficie del diseñador. Esta propiedad solo se debe establecer si el método llamado es estático.|

 Para pasar parámetros como un parámetro **out** de C# (por ejemplo, `Method1(out myParam)),` debe usar **outargument** en lugar de **InOutArgument**

 Los métodos con argumentos denominados **TargetObject** o **result** no se pueden invocar mediante la <xref:System.Activities.Statements.InvokeMethod> actividad. Esto se debe a que la actividad <xref:System.Activities.Statements.InvokeMethod> registra <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> y <xref:System.Activities.Statements.InvokeMethod.Result%2A> en <xref:System.Activities.Activity.CacheMetadata%2A>.

 El algoritmo para registrar los parámetros en <xref:System.Activities.Activity.CacheMetadata%2A> se muestra en la siguiente lista:

1. Registre el argumento <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.

2. Registre el argumento <xref:System.Activities.Statements.InvokeMethod.Result%2A>.

3. Recorra en iteración la colección <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> y registre cada argumento.

   La excepción resultante es de tipo <xref:System.Activities.InvalidWorkflowException> con el siguiente mensaje: 'InvokeMethod': Ya existe una variable, RuntimeArgument o DelegateArgument con el nombre 'TargetObject.' En un ámbito de entorno, los nombres deben ser únicos.

   Esta restricción no se aplica a <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> ni a <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> porque no son los argumentos de flujo de trabajo y por consiguiente, no se registran en la colección <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> de la actividad <xref:System.Activities.Statements.InvokeMethod> en el método <xref:System.Activities.Activity.CacheMetadata%2A>.

## <a name="see-also"></a>Consulte también
 Retardo de [asignación](../workflow-designer/assign-activity-designer.md) [Delay](../workflow-designer/delay-activity-designer.md) de [primitivas](../workflow-designer/primitives-activity-designers.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)