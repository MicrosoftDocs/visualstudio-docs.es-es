---
title: 'Cómo: agregar actividades al cuadro de herramientas (heredado) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3f982372f0189871c4f3d294c07a9e3cfc44391
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656622"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Cómo: Agregar actividades al cuadro de herramientas (Heredado)
Al compilar una solución de flujo de trabajo con el [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado que tiene como destino el [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], se pueden agregar actividades personalizadas al proyecto de flujo de trabajo y sus diseñadores colocados en el **cuadro de herramientas** para facilitar el acceso. También puede Agregar actividades directamente al cuadro de **herramientas** desde una biblioteca de vínculos dinámicos (dll).

### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Para agregar al cuadro de herramientas una actividad de una DLL

1. Haga clic con el botón secundario en la superficie de la ventana cuadro de herramientas en **flujo de trabajo de Windows**y haga clic en **elegir elementos**.

2. En el cuadro de diálogo **elegir elementos del cuadro de herramientas** , haga clic en la pestaña **componentes de System. Activities** y, a continuación, haga clic en **examinar** en la parte inferior derecha de la ventana.

3. Seleccione el archivo DLL en el directorio de archivos que contiene la implementación de la actividad personalizada que se va a agregar al **cuadro de herramientas**y, a continuación, haga clic en **abrir**.

4. Haga clic en **Aceptar** para terminar de agregar la actividad al cuadro de herramientas.

## <a name="see-also"></a>Vea también
 Usar las [actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md) [del diseñador de actividades](../workflow-designer/using-the-legacy-activity-designer.md) heredadas