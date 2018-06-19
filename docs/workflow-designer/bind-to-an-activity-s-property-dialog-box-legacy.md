---
title: 'Diseñador de flujo de trabajo: enlazar a una actividad&#39;cuadro de diálogo de propiedades de s (heredado)'
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Workflow.ComponentModel.Design.ActivityBindForm.UI
helpviewer_keywords:
- Bind to an Activity's Property dialog box
ms.assetid: 19ebb207-e0a9-4642-8f5f-a5e31395c683
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8922864a32c08d8feaed11e530314176557a785f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970990"
---
# <a name="bind-to-an-activitys-property-dialog-box-legacy"></a>Enlazar con un cuadro de diálogo de propiedades de una actividad (Heredado)

Este tema se describe cómo utilizar el **enlazar a una propiedad de Activity** cuadro de diálogo en el Diseñador de flujo de trabajo de Windows heredado. Use el Diseñador de flujo de trabajo heredado cuando deba tener como destino la versión 3.5 de .NET Framework o el conocido como WinFX.

 Un tipo de instancia de propiedad de dependencia se puede enlazar con la propiedad pública o evento de otra actividad. Para obtener más información sobre el enlace de actividad, vea [mediante propiedades de dependencia](http://go.microsoft.com/fwlink?LinkID=65007).

 Seleccione una propiedad que se va a enlazar se usa el **enlazar a una propiedad de Activity** cuadro de diálogo. Abra este cuadro de diálogo haciendo clic en los puntos suspensivos **[...]**  al final del cuadro de texto de la propiedad seleccionada en el **propiedades** ventana, o haga clic en el icono de exclamación azul que aparece junto al nombre de propiedad en el Explorador de propiedades.

 La tabla siguiente describen los elementos de interfaz de usuario de la **enlazar a una propiedad de Activity** cuadro de diálogo.

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**Enlazar a un miembro existente**|Seleccione el miembro con el que desee enlazar en el panel de vista de árbol. El panel que hay debajo de la vista de árbol muestra un mensaje que indica si el miembro es de un tipo válido para enlazar o no. Haga clic en **Aceptar** para enlazar con el miembro seleccionado válido.|
|**Enlazar a un nuevo miembro**|Cree un nuevo campo de miembro o propiedad con el que enlazar. Escriba un **nombre del nuevo miembro**. Elija si desea crear una propiedad de dependencia o un campo público seleccionando **Crear campo** o **crear propiedad**. Haga clic en **Aceptar** para crear el nuevo miembro.|

## <a name="see-also"></a>Vea también

- [Uso de propiedades de la actividad](http://go.microsoft.com/fwlink?LinkID=65013)
- [Uso de las propiedades de dependencia](http://go.microsoft.com/fwlink?LinkID=65007)
- [Ayuda de la interfaz de usuario del diseñador heredado para Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)