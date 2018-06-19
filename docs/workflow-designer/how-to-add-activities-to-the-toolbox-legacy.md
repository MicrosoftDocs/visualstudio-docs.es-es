---
title: 'Diseñador de flujo de trabajo: Cómo: agregar actividades al cuadro de herramientas (heredado)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99a8e1cef2ff5ddd526133355c608fa5218573d1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969432"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Cómo: Agregar actividades al cuadro de herramientas (Heredado)

Al compilar una solución de flujo de trabajo con el Diseñador de flujo de trabajo de Windows heredado que tiene como destino la versión 3.5 de .NET Framework o el conocido como WinFX, se pueden agregar actividades personalizadas para el proyecto de flujo de trabajo y sus diseñadores colocados en el **cuadro de herramientas** para fácil acceso. También puede agregar actividades directamente a la **cuadro de herramientas** desde una biblioteca de vínculos dinámicos (DLL).

## <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Para agregar al cuadro de herramientas una actividad de una DLL

1.  Haga clic en la superficie de la ventana de cuadro de herramientas en **Windows Workflow**y, a continuación, haga clic en **elegir elementos**.

2.  En el **elegir elementos del cuadro de herramientas** cuadro de diálogo, haga clic en el **componentes de System.Activities** ficha y, a continuación, haga clic en **examinar** desde la parte inferior derecha de la ventana.

3.  Seleccione el archivo DLL desde el directorio de archivo que contiene la implementación de la actividad personalizada para agregar a la **cuadro de herramientas**y, a continuación, haga clic en **abiertos**.

4.  Haga clic en **Aceptar** para terminar de agregar la actividad al cuadro de herramientas.

## <a name="see-also"></a>Vea también

- [Usar el diseñador de actividad Legacy](../workflow-designer/using-the-legacy-activity-designer.md)
- [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)