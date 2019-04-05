---
title: Filtrar Agregar actividades al cuadro de herramientas (heredado) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 51c9d43a1dee05d1b1cb77e50aa2d54d4f4e7f2c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996868"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Filtrar Agregar actividades al cuadro de herramientas (heredado)
Al compilar una solución de flujo de trabajo con heredado [!INCLUDE[wfd1](../includes/wfd1-md.md)] que tiene como destino el [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], se pueden agregar actividades personalizadas para el proyecto de flujo de trabajo y sus diseñadores colocados en el **cuadro de herramientas** para fácil acceso. También puede agregar actividades directamente a la **cuadro de herramientas** desde una biblioteca de vínculos dinámicos (DLL).  
  
### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Para agregar al cuadro de herramientas una actividad de una DLL  
  
1.  Haga clic en la superficie de la ventana del cuadro de herramientas en **flujo de trabajo de Windows**y, a continuación, haga clic en **elegir elementos**.  
  
2.  En el **elegir elementos del cuadro de herramientas** cuadro de diálogo, haga clic en el **componentes de System.Activities** pestaña y, a continuación, haga clic en **examinar** desde el lado inferior derecho de la ventana.  
  
3.  Seleccione el archivo DLL desde el directorio del archivo que contiene la implementación de la actividad personalizada para agregar a la **cuadro de herramientas**y, a continuación, haga clic en **abierto**.  
  
4.  Haga clic en **Aceptar** para terminar de agregar la actividad al cuadro de herramientas.  
  
## <a name="see-also"></a>Vea también  
 [Usar el Diseñador de actividad Legacy](../workflow-designer/using-the-legacy-activity-designer.md)   
 [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)