---
title: Procedimiento Implementar una operación de contrato de Windows Communication Foundation (heredado) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f6f54e781dfae15b4b1c1159d73ac3495b35c21
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603864"
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Procedimiento Implementar una operación de contrato de Windows Communication Foundation (heredado)
En este tema se describe cómo implementar una operación de contrato de [!INCLUDE[indigo1](../includes/indigo1-md.md)] usando [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado que tiene como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Después de arrastrar una actividad **ReceiveActivity** desde el cuadro de herramientas a la superficie de diseño de flujo de trabajo, creará un nuevo contrato de [!INCLUDE[indigo2](../includes/indigo2-md.md)] o importará un contrato existente e implementará las operaciones. Seleccione y/o cree el contrato y sus operaciones a través del [cuadro de diálogo elegir operación (heredado)](../workflow-designer/choose-operation-dialog-box-legacy.md).

### <a name="to-implement-a-wcf-contract-operation"></a>Para implementar una operación de contrato WCF

1. Haga doble clic en la actividad **ReceiveActivity** en el diseñador o haga clic en los puntos suspensivos junto a la propiedad **ServiceOperationInfo** en el panel de **propiedades** .

2. Realice una de las siguientes acciones:

   - Haga clic en **Agregar contrato** en la esquina superior derecha del cuadro de diálogo. De este modo creará un nuevo contrato y operación [!INCLUDE[indigo2](../includes/indigo2-md.md)].

      O bien,

   - Haga clic en **importar** en la esquina superior derecha del cuadro de diálogo. Se abre el [cuadro de diálogo examinar y seleccionar un tipo .net (heredado)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) . Busque un ensamblado o proyecto que contenga el contrato deseado. Seleccione el contrato y haga clic en **Aceptar**.

     Después de que se crea o importa un contrato, puede agregarle nuevas operaciones. Para agregar una nueva operación, seleccione el contrato y haga clic en **Agregar operación** en la esquina superior derecha del cuadro de diálogo. Cuando haya terminado de agregar operaciones, continúe con el paso 3.

3. Seleccione la operación que desea asociar a la actividad **ReceiveActivity** . Puede manipular la definición de la operación cambiando el nombre, los parámetros, las propiedades y los valores de permiso de la operación.

    Para cambiar el nombre, escriba el nuevo nombre en el cuadro de texto nombre de la **operación** .

    Haga clic en la pestaña **parámetros** para tener acceso a los parámetros de la operación. Puede cambiar el nombre, el tipo o la dirección de un parámetro, así como agregar o eliminar parámetros de la operación.

    Haga clic en la pestaña **propiedades** para tener acceso al nivel de protección de operaciones y a la funcionalidad de intercambio de mensajes admitida de la operación.

    Haga clic en la pestaña **permisos** para especificar qué grupos pueden implementar la operación.

4. Haga clic en **Aceptar** y la actividad **ReceiveActivity** mostrará el nombre de la operación que está implementando.

5. Coloque las actividades de flujo de trabajo que va a usar para la implementación de esa operación dentro de la actividad **ReceiveActivity** .

## <a name="see-also"></a>Vea también
 En el [cuadro de diálogo elegir operación (heredado)](../workflow-designer/choose-operation-dialog-box-legacy.md) [How: Invocar una operación de contrato WCF (heredada) ](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) [actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)