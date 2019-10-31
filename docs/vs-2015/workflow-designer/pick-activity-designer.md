---
title: Diseñador de actividad Pick | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: daefc48cfff2c5c73d9ecf14316777becf4d83c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672593"
---
# <a name="pick-activity-designer"></a>Diseñador de actividades Pick
La actividad <xref:System.Activities.Statements.Pick> proporciona un flujo de control basado en eventos. La actividad ejecuta una de las diversas bifurcaciones en respuesta a un evento desencadenador.

## <a name="the-pick-activity"></a>Actividad Pick
 Una actividad <xref:System.Activities.Statements.Pick> contiene una colección de objetos <xref:System.Activities.Statements.PickBranch>, uno de los cuales puede ejecutar la actividad <xref:System.Activities.Statements.Pick> a causa de algún evento de entrada que actúa como un desencadenador. De esta forma, [!INCLUDE[wfd1](../includes/wfd1-md.md)] proporciona un modelado de flujo de control basado en eventos. Cada clase <xref:System.Activities.Statements.PickBranch> contiene una propiedad <xref:System.Activities.Statements.PickBranch.Trigger%2A> y una propiedad <xref:System.Activities.Statements.PickBranch.Action%2A>. Al comienzo de una ejecución de la actividad <xref:System.Activities.Statements.Pick>, se programan todas las actividades de desencadenador de los elementos <xref:System.Activities.Statements.PickBranch>. Cuando se completa la primera actividad, se programa la actividad de acción correspondiente y el resto de actividades de desencadenador se cancelan.

### <a name="how-to-use-the-pick-activity-designer"></a>Usar el diseñador de actividad Pick
 El diseñador de actividades **Pick** se puede encontrar en la categoría **flujo de control** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña cuadro de **herramientas** en [!INCLUDE[wfd2](../includes/wfd2-md.md)] (de forma alternativa, seleccione **barra de herramientas** en el menú **Ver** o Ctrl + Alt. + X).

 El diseñador de actividades **Pick** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie [!INCLUDE[wfd2](../includes/wfd2-md.md)], donde se coloquen normalmente los diseñadores de actividad, por ejemplo, dentro de un diseñador de actividad **Sequence** . Después de colocarlo en [!INCLUDE[wfd2](../includes/wfd2-md.md)], crea una actividad <xref:System.Activities.Statements.Pick> que, de forma predeterminada, contiene dos actividades <xref:System.Activities.Statements.PickBranch> vacías como elementos, con los nombres para mostrar Branch1 y Branch2. Estos valores de propiedad de <xref:System.Activities.Statements.PickBranch.DisplayName%2A> respectivos se pueden editar en el encabezado del diseñador de actividades **PickBranch** o en la ventana **propiedades** para cada bifurcación.

 Hay dos maneras de agregar actividades <xref:System.Activities.Statements.PickBranch> a la colección de un objeto <xref:System.Activities.Statements.Pick>: arrastrar y colocar el diseñador **PickBranch** desde el cuadro de **herramientas** o mediante el menú contextual desde la superficie de diseño de **Pick** . Para obtener más información, vea el tema [PickBranch](../workflow-designer/pickbranch-activity-designer.md) . Observe que el único elemento que se puede colocar dentro de un diseñador de actividad **Pick** es un diseñador de actividad **PickBranch** .

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Propiedades de la actividad Pick en el Diseñador de flujo de trabajo
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Pick> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie del diseñador.

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.Pick> en el encabezado. El valor predeterminado es Pick. El valor se puede editar en la cuadrícula de propiedades o directamente en el encabezado del diseñador de actividades.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|

## <a name="see-also"></a>Vea también
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md) [Selección de actividades](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e) [Uso de la actividad de selección](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)