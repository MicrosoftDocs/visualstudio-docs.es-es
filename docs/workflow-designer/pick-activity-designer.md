---
title: Diseñador de flujo de trabajo - Diseñador de actividades Pick
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 710c7728069a7166d67ab39239b360634fb80509
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269506"
---
# <a name="pick-activity-designer"></a>Diseñador de actividades Pick

La actividad <xref:System.Activities.Statements.Pick> proporciona un flujo de control basado en eventos. La actividad ejecuta una de las diversas bifurcaciones en respuesta a un evento desencadenador.

## <a name="the-pick-activity"></a>Actividad Pick

Una actividad <xref:System.Activities.Statements.Pick> contiene una colección de objetos <xref:System.Activities.Statements.PickBranch>, uno de los cuales puede ejecutar la actividad <xref:System.Activities.Statements.Pick> a causa de algún evento de entrada que actúa como un desencadenador. De esta manera, el Diseñador de flujo de trabajo proporciona modelado de flujo de control basado en eventos. Cada clase <xref:System.Activities.Statements.PickBranch> contiene una propiedad <xref:System.Activities.Statements.PickBranch.Trigger%2A> y una propiedad <xref:System.Activities.Statements.PickBranch.Action%2A>. Al principio de un <xref:System.Activities.Statements.Pick> ejecución de la actividad, todas las actividades de desencadenador de la <xref:System.Activities.Statements.PickBranch> elementos están programados. Cuando se completa la primera actividad, se programa la actividad de acción correspondiente y el resto de actividades de desencadenador se cancelan.

### <a name="how-to-use-the-pick-activity-designer"></a>Usar el diseñador de actividad Pick

Acceso a la **elegir** Diseñador de actividad en el **flujo de Control** categoría de la **cuadro de herramientas**. El **elegir** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde normalmente se colocan los diseñadores de actividad, por ejemplo, en un  **Secuencia** Diseñador de actividad. Después de colocarlo en el Diseñador de flujo de trabajo, crea un <xref:System.Activities.Statements.Pick> actividad, que de forma predeterminada contiene dos vacío <xref:System.Activities.Statements.PickBranch> actividades como elementos con nombres Branch1 y Branch2 para mostrar. Los respectivos <xref:System.Activities.Statements.PickBranch.DisplayName%2A> se pueden editar los valores de propiedad en el **PickBranch** encabezado del Diseñador de actividad o dentro del **propiedades** ventana para cada bifurcación.

Hay dos maneras de agregar <xref:System.Activities.Statements.PickBranch> actividades a la colección de un <xref:System.Activities.Statements.Pick> objeto: arrastrando y colocando el **PickBranch** diseñador desde el **cuadro de herramientas** o mediante el menú contextual desde el **elegir** superficie de diseño. Para obtener más información, consulte el [PickBranch](../workflow-designer/pickbranch-activity-designer.md) tema. Tenga en cuenta que el único elemento que se puede colocar dentro un **elegir** Diseñador de actividad es un **PickBranch** Diseñador de actividad.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Propiedades de la actividad Pick en el Diseñador de flujo de trabajo

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Pick> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie del diseñador.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.Pick> en el encabezado. El valor predeterminado es Pick. El valor se puede editar en la cuadrícula de propiedades o directamente en el encabezado del diseñador de actividades.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|

## <a name="see-also"></a>Vea también

- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)
- [Actividad Pick](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Uso de la actividad Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)