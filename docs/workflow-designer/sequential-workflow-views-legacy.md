---
title: Diseñador de flujo de trabajo - vistas de flujos de trabajo secuenciales (heredado)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce1217ea629ae0301b72b444161d61db4fe448b1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976024"
---
# <a name="sequential-workflow-views-legacy"></a>Vistas de flujos de trabajo secuenciales (Heredado)

Visual Studio 2010 proporciona un diseñador de flujo de trabajo heredado de Windows que puede utilizarse como destino la versión 3.5 de .NET Framework o el conocido como WinFX.

El Diseñador de flujo de trabajo proporciona una manera de crear gráficamente aplicaciones de Windows Workflow Foundation (WF) mediante la conocida interfaz de usuario de Visual Studio. Las aplicaciones de Windows Workflow Foundation (WF) se componen de pasos del proceso de flujo de trabajo denominados actividades. Para crear un flujo de trabajo, cree actividades en la superficie de diseño arrastrando sus diseñadores de actividad correspondientes desde **cuadro de herramientas** a la superficie de diseño.

Cuando se crea un flujo de trabajo secuencial, que es un [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040), existen tres vistas del flujo de trabajo. Estas vistas son accesibles desde el **flujo de trabajo** menú y en el menú contextual en la superficie de diseño.

En la tabla siguiente se enumeran el nombre y la descripción de cada vista.

|Opción de menú o pestaña|Descripción|
|----------------------|-----------------|
|**Vista de flujo de trabajo secuencial**|Haga clic en la superficie de diseño y seleccione el **vista flujo de trabajo secuencial** opción en el menú contextual para mostrar el **flujo de trabajo secuencial** vista, que muestra basado en la actividad gráfica representación del flujo de trabajo secuencial. O seleccione **vista flujo de trabajo secuencial** desde el **flujo de trabajo** menú.|
|**Ver controlador de cancelación**|Haga clic en la superficie de diseño y seleccione el **ver controlador de cancelación** opción en el menú contextual para mostrar el **flujo de trabajo secuencial** ver, que muestra la [CancellationHandlerActivity ](http://go.microsoft.com/fwlink?LinkID=65050) actividad asociada con el flujo de trabajo. O seleccione **ver controlador de cancelación** desde el **flujo de trabajo** menú.|
|**Ver controlador de errores**|Haga clic en la superficie de diseño y seleccione el **ver controlador de errores** opción en el menú contextual para mostrar el **errores** ver, que muestra la [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) actividad asociada con el flujo de trabajo. O seleccione **ver controlador de errores** desde el **flujo de trabajo** menú.|

 Para obtener más información acerca de las vistas similares, consulte [vistas de actividad (heredado)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Vea también

- [Vistas de actividad (heredado)](../workflow-designer/activity-views-legacy.md)
- [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md)
- [Modos de creación de flujo de trabajo](http://go.microsoft.com/fwlink?LinkID=65014)