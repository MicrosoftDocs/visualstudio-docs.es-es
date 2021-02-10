---
title: Diseñador de actividades Diseñador de flujo de trabajo-InvokeMethod
description: Obtenga información sobre la actividad InvokeMethod y cómo puede utilizar el diseñador de actividades InvokeMethod para crear y configurar una actividad InvokeMethod.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2ba7234ee0c5a4ab8096c020cb44345f17830540
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931219"
---
# <a name="invokemethod-activity-designer"></a>Diseñador de actividades InvokeMethod

El diseñador **InvokeMethod** se usa para crear y configurar una <xref:System.Activities.Statements.InvokeMethod> actividad.

## <a name="the-invokemethod-activity"></a>La actividad InvokeMethod

<xref:System.Activities.Statements.InvokeMethod> llama a un método público de un objeto o tipo especificados.

### <a name="use-the-invokemethod-activity-designer"></a>Usar el diseñador de actividades InvokeMethod

Obtenga acceso al diseñador de actividades **InvokeMethod** en la categoría **primitivas** del **cuadro de herramientas**. El diseñador de actividades **InvokeMethod** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de diseñador de flujo de trabajo donde se colocan normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence> . Al quitar el diseñador de actividad, se crea una <xref:System.Activities.Statements.InvokeMethod> actividad con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de invokeMethod. <xref:System.Activities.Activity.DisplayName%2A>Se puede editar en el encabezado del diseñador de actividades **InvokeMethod** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-invokemethod-properties"></a>Propiedades de InvokeMethod

En la tabla siguiente se muestran las <xref:System.Activities.Statements.InvokeMethod> propiedades y se describe cómo se usan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades y algunas se pueden editar en Diseñador de flujo de trabajo superficie.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.InvokeMethod>. El valor predeterminado es InvokeMethod.<br /><br /> Aunque <xref:System.Activities.Activity.DisplayName%2A> no es estrictamente necesario, es mejor usar uno.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|El nombre del método que se va a llamar cuando se ejecute la actividad. El método al que se llama debe declararse como **público**. Esta propiedad se puede editar en la superficie del diseñador y es obligatoria.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|La colección de parámetros del método al que se ha llamado. Los parámetros se deben agregar a la colección en el mismo orden que aparecen en la firma de método. Para mostrar el cuadro de diálogo **parámetros** donde puede establecer esta propiedad, haga clic en el botón de puntos suspensivos del campo **parámetros** de la cuadrícula de propiedades. Haga clic en el botón **crear argumento** para agregar los parámetros.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|El valor devuelto de la llamada al método.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|Especifica si el método se llama de forma asincrónica. El valor predeterminado es **False**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Objeto que contiene el método al que se va a llamar. Esta propiedad se puede editar en la superficie del diseñador.<br /><br /> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> o <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> son obligatorias para que se establezcan.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Tipo de <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Esta propiedad se puede editar en la superficie del diseñador. Esta propiedad solo se debe establecer si el método llamado es estático.|

Para pasar parámetros como un parámetro **out** de C# (por ejemplo, `Method1(out myParam))` , utilice **outargument** en lugar de **InOutArgument**

Los métodos con argumentos denominados **TargetObject** o **result** no se pueden invocar mediante la <xref:System.Activities.Statements.InvokeMethod> actividad. Esto se debe a que la actividad <xref:System.Activities.Statements.InvokeMethod> registra <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> y <xref:System.Activities.Statements.InvokeMethod.Result%2A> en <xref:System.Activities.Activity.CacheMetadata%2A>.

El algoritmo para registrar los parámetros en <xref:System.Activities.Activity.CacheMetadata%2A> se muestra en la siguiente lista:

1. Registre el argumento <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.

2. Registre el argumento <xref:System.Activities.Statements.InvokeMethod.Result%2A>.

3. Recorra en iteración la colección <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> y registre cada argumento.

La excepción resultante es de tipo <xref:System.Activities.InvalidWorkflowException> con el siguiente mensaje: 'InvokeMethod': Ya existe una variable, RuntimeArgument o DelegateArgument con el nombre 'TargetObject.' En un ámbito de entorno, los nombres deben ser únicos.

Esta restricción no se aplica a <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> y <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> . No son argumentos de flujo de trabajo y, por tanto, no se registran en la <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> colección de la <xref:System.Activities.Statements.InvokeMethod> actividad en el <xref:System.Activities.Activity.CacheMetadata%2A> método.

## <a name="see-also"></a>Vea también

- [Elementos primitivos](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)
