---
title: InvokeDelegate | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0abb68a1cb123be7463d0fe3ec102f438eb8a2ba
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567027"
---
# <a name="invokedelegate"></a>InvokeDelegate

El **InvokeDelegate** diseñador se utiliza para crear y configurar un <xref:System.Activities.Statements.InvokeDelegate> actividad.

## <a name="the-invokedelegate-activity"></a>Actividad InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate> llama a un delegado público.

### <a name="using-the-invokedelegate-activity-designer"></a>Usar el diseñador de actividad InvokeDelegate

El **InvokeDelegate** Diseñador de actividad puede encontrarse en el **primitivas** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas** ficha [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)

El **InvokeDelegate** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie donde se coloquen normalmente las actividades, tal como en un <xref:System.Activities.Statements.Sequence>. De esta forma, se crea una actividad <xref:System.Activities.Statements.InvokeDelegate> con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de InvokeDelegate. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **InvokeDelegate** Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades.

### <a name="the-invokedelegate-properties"></a>Las propiedades de InvokeDelegate

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.InvokeDelegate> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.InvokeDelegate>. El valor predeterminado es InvokeDelegate.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|El nombre del <xref:System.Activities.ActivityDelegate> que se va a llamar cuando se ejecute la actividad. Esta propiedad se puede editar en la superficie del diseñador. Es una propiedad obligatoria.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|La colección de argumentos del delegado llamado. Las claves son los nombres de los objetos <xref:System.Activities.DelegateArgument> incluidos en el <xref:System.Activities.ActivityDelegate> y los valores son los argumentos cuyas expresiones se evalúan y asignan a los objetos <xref:System.Activities.DelegateArgument> correspondientes. En la cuadrícula de propiedades, haga clic en el botón de puntos suspensivos en el **DelegateArguments** campo, muestra el **DelegateArguments** cuadro de diálogo que le permita definir esta propiedad. Haga clic en el **crear argumento** campo para agregar los argumentos.|

## <a name="see-also"></a>Vea también

- [Cómo: Definir y consumir delegados de actividad en el Diseñador de flujo de trabajo](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)