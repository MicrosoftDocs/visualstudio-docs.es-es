---
title: Procedimiento Implementar una operación de contrato de Windows Communication Foundation (heredado) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 56866e084eac7dc3a3ac2a0b80baaa2533ccd285
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62931175"
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Procedimiento Implementar una operación de contrato de Windows Communication Foundation (heredado)
En este tema se describe cómo implementar una operación de contrato de [!INCLUDE[indigo1](../includes/indigo1-md.md)] usando [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado que tiene como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Después de arrastrar un **ReceiveActivity** actividad desde el cuadro de herramientas hasta la superficie de diseño de flujo de trabajo, se creará un nuevo [!INCLUDE[indigo2](../includes/indigo2-md.md)] de contrato o importar un contrato existente e implemente las operaciones. Puede seleccionar y crear el contrato y sus operaciones a través de la [elija el cuadro de diálogo de operación (heredado)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
### <a name="to-implement-a-wcf-contract-operation"></a>Para implementar una operación de contrato WCF  
  
1. Haga doble clic en el **ReceiveActivity** actividad en el diseñador o haga clic en el botón de puntos suspensivos junto a la **ServiceOperationInfo** propiedad en el **propiedades** panel.  
  
2. Realice una de las siguientes acciones:  
  
   - Haga clic en **agregar contrato** en la esquina superior derecha del cuadro de diálogo. De este modo creará un nuevo contrato y operación [!INCLUDE[indigo2](../includes/indigo2-md.md)].  
  
      -o bien-  
  
   - Haga clic en **importación** en la esquina superior derecha del cuadro de diálogo. El [examinar y seleccionar un cuadro de diálogo de tipo .NET (heredado)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) se abre. Busque un ensamblado o proyecto que contenga el contrato deseado. Seleccione el contrato y haga clic en **Aceptar**.  
  
     Después de que se crea o importa un contrato, puede agregarle nuevas operaciones. Para agregar una nueva operación, seleccione el contrato y haga clic en **Agregar operación** en la esquina superior derecha del cuadro de diálogo. Cuando haya terminado de agregar operaciones, continúe con el paso 3.  
  
3. Seleccione la operación que desea asociar con el **ReceiveActivity** actividad. Puede manipular la definición de la operación cambiando el nombre, los parámetros, las propiedades y los valores de permiso de la operación.  
  
    Para cambiar el nombre, escriba el nuevo nombre en el **nombre de la operación** cuadro de texto.  
  
    Haga clic en el **parámetros** tab para tener acceso a los parámetros de la operación. Puede cambiar el nombre, el tipo o la dirección de un parámetro, así como agregar o eliminar parámetros de la operación.  
  
    Haga clic en el **propiedades** ficha para tener acceso a la funcionalidad de exchange de operación protección admitidos y nivel de mensaje de la operación.  
  
    Haga clic en el **permisos** tab para especificar qué grupos pueden implementar la operación.  
  
4. Haga clic en **Aceptar** y **ReceiveActivity** actividad mostrará el nombre de la operación para la operación que está implementando.  
  
5. Coloque las actividades de flujo de trabajo que se va a usar para la implementación de esa operación dentro de la **ReceiveActivity** actividad.  
  
## <a name="see-also"></a>Vea también  
 [Elija el cuadro de diálogo de operación (heredado)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Cómo: Invocar una operación de contrato WCF (heredado)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)