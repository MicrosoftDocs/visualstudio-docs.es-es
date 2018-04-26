---
title: 'Diseñador de flujo de trabajo: Cómo: implementar una operación de contrato de Windows Communication Foundation (heredado)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b069d8ca8c1adb72e2869eb59644e8abeff14ae
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Cómo: Implementar una operación de contrato de Windows Communication Foundation (Heredado)

En este tema se describe cómo implementar una operación de contrato de Windows Communication Foundation (WCF) mediante el Diseñador de flujo de trabajo de Windows heredado que tiene como destino la versión 3.5 de .NET Framework o el conocido como WinFX.

Después de arrastrar un **ReceiveActivity** actividad en el cuadro de herramientas a la superficie de diseño de flujo de trabajo, cree un nuevo [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] contrato o importe un contrato existente e implemente las operaciones. Seleccione o cree el contrato y sus operaciones a través de la [elija el cuadro de diálogo de operación (heredado)](../workflow-designer/choose-operation-dialog-box-legacy.md).

## <a name="to-implement-a-wcf-contract-operation"></a>Para implementar una operación de contrato WCF

1.  Haga doble clic en el **ReceiveActivity** actividad en el diseñador o haga clic en los puntos suspensivos junto a la **ServiceOperationInfo** propiedad en el **propiedades** panel.

2.  Realice una de las siguientes acciones:

    -   Haga clic en **agregar contrato** en la esquina superior derecha del cuadro de diálogo. De este modo creará un nuevo contrato y operación [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)].

         -o bien-

    -   Haga clic en **importación** en la esquina superior derecha del cuadro de diálogo. El [examinar y seleccionar un cuadro de diálogo de tipo de .NET (heredado)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) se abre. Busque un ensamblado o proyecto que contenga el contrato deseado. Seleccione el contrato y haga clic en **Aceptar**.

     Después de que se crea o importa un contrato, puede agregarle nuevas operaciones. Para agregar una nueva operación, seleccione el contrato y haga clic en **Agregar operación** en la esquina superior derecha del cuadro de diálogo. Cuando haya terminado de agregar operaciones, continúe con el paso 3.

3.  Seleccione la operación que desea asociar con el **ReceiveActivity** actividad. Puede manipular la definición de la operación cambiando el nombre, los parámetros, las propiedades y los valores de permiso de la operación.

     Para cambiar el nombre, escriba el nuevo nombre en el **nombre de la operación** cuadro de texto.

     Haga clic en el **parámetros** tab para acceder a los parámetros de la operación. Puede cambiar el nombre, el tipo o la dirección de un parámetro, así como agregar o eliminar parámetros de la operación.

     Haga clic en el **propiedades** ficha para tener acceso a la funcionalidad de exchange del mensaje de nivel y se admite de protección de operación de la operación.

     Haga clic en el **permisos** ficha para especificar qué grupos se pueden implementar la operación.

4.  Haga clic en **Aceptar** y **ReceiveActivity** actividad mostrará el nombre de la operación para la operación que está implementando.

5.  Coloque las actividades de flujo de trabajo que se va a usar para la implementación de esa operación dentro de la **ReceiveActivity** actividad.

## <a name="see-also"></a>Vea también

- [Cuadro de diálogo Elegir operación (heredado)](../workflow-designer/choose-operation-dialog-box-legacy.md)
- [Cómo: invocar una operación de contrato WCF (heredado)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)
- [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)