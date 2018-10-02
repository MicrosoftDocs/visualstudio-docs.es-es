---
title: 'Cómo: crear proyectos de flujo de trabajo (heredado) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 6fb33b391f05baf91a4c35be0d949f66a885e228
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582674"
---
# <a name="how-to-create-workflow-projects-legacy"></a>Cómo: Crear proyectos de flujo de trabajo (Heredado)
Siga estos pasos para crear un proyecto de [!INCLUDE[wf](../includes/wf-md.md)] que tenga como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]. Este procedimiento usa [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado proporcionado por [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
### <a name="to-create-a-workflow-project"></a>Para crear un proyecto de flujo de trabajo  
  
1.  Inicie [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)].  
  
2.  En el menú **Archivo**, elija **Nuevo** y después seleccione **Proyecto**.  
  
     Aparece el cuadro de diálogo **Nuevo proyecto** .  
  
3.  Seleccione el **.NET Framework 3.0** opción o el **.NET Framework 3.5** opción en la lista desplegable situada en la parte superior de la **nuevo proyecto** ventana para tener acceso al diseñador heredado.  
  
    > [!NOTE]
    >  La opción predeterminada de [!INCLUDE[vs2010](../includes/vs2010-md.md)] es **.NET Framework 4**. Esta opción se usa para crear aplicaciones [!INCLUDE[wf](../includes/wf-md.md)] que tienen como destino [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] y no usa el diseñador heredado.  
  
4.  En el **tipos de proyecto** panel, seleccione proyectos de Visual C# o proyectos de Visual Basic y, a continuación, seleccione **flujo de trabajo**.  
  
5.  En el **plantillas** panel, seleccione una de las plantillas de proyecto instaladas:  
  
    -   Aplicación de consola de flujos de trabajo secuenciales  
  
    -   Biblioteca de flujos de trabajo secuenciales  
  
    -   Biblioteca de flujos de trabajo de actividad  
  
    -   Aplicación de consola de flujos de trabajo de equipo de estado  
  
    -   Biblioteca de flujos de trabajo de equipo de estado  
  
    -   Proyecto de flujo de trabajo vacío  
  
6.  En el **nombre** , escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.  
  
7.  En el **ubicación** cuadro, escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para navegar hasta el directorio.  
  
     Si desea que un directorio de soluciones creado para el proyecto, seleccione el **crear directorio para la solución** casilla de verificación y escriba un nombre en el **nombre de la solución** cuadro.  
  
8.  Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md)