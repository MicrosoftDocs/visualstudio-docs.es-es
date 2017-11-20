---
title: "Cómo: implementar una operación de contrato de Windows Communication Foundation (heredado) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 02d6a544b660a110c618bdcb7d3b778fd82ceaaa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Cómo: Implementar una operación de contrato de Windows Communication Foundation (Heredado)
En este tema se describe cómo implementar una operación de contrato de [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] usando [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado que tiene como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Después de arrastrar un **ReceiveActivity** actividad en el cuadro de herramientas a la superficie de diseño de flujo de trabajo, cree un nuevo [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] contrato o importe un contrato existente e implemente las operaciones. Seleccione o cree el contrato y sus operaciones a través de la [elija el cuadro de diálogo de operación (heredado)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
### <a name="to-implement-a-wcf-contract-operation"></a>Para implementar una operación de contrato WCF  
  
1.  Haga doble clic en el **ReceiveActivity** actividad en el diseñador o haga clic en los puntos suspensivos junto a la **ServiceOperationInfo** propiedad en el **propiedades** panel.  
  
2.  Realice una de las siguientes acciones:  
  
    -   Haga clic en **agregar contrato** en la esquina superior derecha del cuadro de diálogo. De este modo creará un nuevo contrato y operación [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)].  
  
         O bien  
  
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
 [Elija el cuadro de diálogo de operación (heredado)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Cómo: invocar una operación de contrato WCF (heredado)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)