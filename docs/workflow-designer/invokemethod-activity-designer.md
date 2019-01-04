---
title: Diseñador de flujo de trabajo - Diseñador de actividades InvokeMethod
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cd0b30d3695d13b51b988dfee31829d03e4b661d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53946949"
---
# <a name="invokemethod-activity-designer"></a>Diseñador de actividades InvokeMethod

**InvokeMethod** diseñador se utiliza para crear y configurar un <xref:System.Activities.Statements.InvokeMethod> actividad.

## <a name="the-invokemethod-activity"></a>La actividad InvokeMethod

<xref:System.Activities.Statements.InvokeMethod> llama a un método público de un objeto o tipo especificados.

### <a name="use-the-invokemethod-activity-designer"></a>Utilice el Diseñador de actividades InvokeMethod

Acceso a la **InvokeMethod** Diseñador de actividad en el **primitivas** categoría de la **cuadro de herramientas**. El **InvokeMethod** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo, donde cada vez que se coloquen normalmente las actividades, tal como en un <xref:System.Activities.Statements.Sequence>. Al colocar el Diseñador de actividad se crea un <xref:System.Activities.Statements.InvokeMethod> actividad su valor predeterminado es <xref:System.Activities.Activity.DisplayName%2A> de InvokeMethod. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **InvokeMethod** Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades.

### <a name="the-invokemethod-properties"></a>Propiedades InvokeMethod

La tabla siguiente muestra la <xref:System.Activities.Statements.InvokeMethod> propiedades y se describe cómo se usan en el diseñador. Estas propiedades se pueden editar en cuadrícula de propiedades y algunas de ellas en la superficie del Diseñador de flujo de trabajo.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.InvokeMethod>. El valor predeterminado es InvokeMethod.<br /><br /> Aunque el <xref:System.Activities.Activity.DisplayName%2A> no es estrictamente necesaria, es mejor usar uno.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|El nombre del método que se va a llamar cuando se ejecute la actividad. El método llamado debe declararse como **pública**. Esta propiedad se puede editar en la superficie del diseñador y es obligatoria.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|La colección de parámetros del método al que se ha llamado. Los parámetros se deben agregar a la colección en el mismo orden que aparecen en la firma de método. Para mostrar el **parámetros** cuadro de diálogo donde puede establecer esta propiedad, haga clic en el botón de puntos suspensivos en el **parámetros** campo de la cuadrícula de propiedades. Haga clic en el **crear argumento** para agregar los parámetros.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|El valor devuelto de la llamada al método.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|Especifica si el método se llama de forma asincrónica. El valor predeterminado es **False**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Objeto que contiene el método al que se va a llamar. Esta propiedad se puede editar en la superficie del diseñador.<br /><br /> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> o <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> son obligatorias para que se establezcan.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Tipo de <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Esta propiedad se puede editar en la superficie del diseñador. Esta propiedad solo se debe establecer si el método llamado es estático.|

Para pasar parámetros como C# **out** parámetro (por ejemplo, `Method1(out myParam))`, utilice **OutArgument** en lugar de **InOutArgument**

Los métodos con argumentos llamados **TargetObject** o **resultado** no se puede invocar mediante el <xref:System.Activities.Statements.InvokeMethod> actividad. Esto se debe a que la actividad <xref:System.Activities.Statements.InvokeMethod> registra <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> y <xref:System.Activities.Statements.InvokeMethod.Result%2A> en <xref:System.Activities.Activity.CacheMetadata%2A>.

El algoritmo para registrar los parámetros en <xref:System.Activities.Activity.CacheMetadata%2A> se muestra en la siguiente lista:

1.  Registre el argumento <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.

2.  Registre el argumento <xref:System.Activities.Statements.InvokeMethod.Result%2A>.

3.  Recorra en iteración la colección <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> y registre cada argumento.

La excepción resultante es de tipo <xref:System.Activities.InvalidWorkflowException> con el siguiente mensaje: 'InvokeMethod': Una variable, RuntimeArgument o DelegateArgument ya existe con el nombre 'TargetObject'. En un ámbito de entorno, los nombres deben ser únicos.

Esta restricción no se aplica a <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> y <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>. No son argumentos de flujo de trabajo y, por tanto, no se registran en el <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> colección de la <xref:System.Activities.Statements.InvokeMethod> actividad en el <xref:System.Activities.Activity.CacheMetadata%2A> método.

## <a name="see-also"></a>Vea también

- [Elementos primitivos](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)