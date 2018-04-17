---
title: 'Cómo: agregar actividades al cuadro de herramientas (heredado) | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 779735cb1d163db9e7b05e2892d01a991a4a4c2c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Cómo: Agregar actividades al cuadro de herramientas (Heredado)
Al compilar una solución de flujo de trabajo con el Diseñador de flujo de trabajo de Windows heredado que tiene como destino el [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], las actividades personalizadas se pueden agregar al proyecto de flujo de trabajo y sus diseñadores colocados en el **cuadro de herramientas** para fácil acceso. También puede agregar actividades directamente a la **cuadro de herramientas** desde una biblioteca de vínculos dinámicos (DLL).

### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Para agregar al cuadro de herramientas una actividad de una DLL

1.  Haga clic en la superficie de la ventana de cuadro de herramientas en **Windows Workflow**y, a continuación, haga clic en **elegir elementos**.

2.  En el **elegir elementos del cuadro de herramientas** cuadro de diálogo, haga clic en el **componentes de System.Activities** ficha y, a continuación, haga clic en **examinar** desde la parte inferior derecha de la ventana.

3.  Seleccione el archivo DLL desde el directorio de archivo que contiene la implementación de la actividad personalizada para agregar a la **cuadro de herramientas**y, a continuación, haga clic en **abiertos**.

4.  Haga clic en **Aceptar** para terminar de agregar la actividad al cuadro de herramientas.

## <a name="see-also"></a>Vea también

- [Usar el diseñador de actividad Legacy](../workflow-designer/using-the-legacy-activity-designer.md)
- [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)