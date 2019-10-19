---
title: 'Cómo: agregar un nuevo elemento a un proyecto de flujo de trabajo (heredado) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflows, adding to workflow projects
- workflows, adding new items
- state machine workflows, adding to workflow projects
- activities, adding to workflow projects
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 46f6e9daafc2688b9bea75cba9eddd8c8a53c9bb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656669"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project-legacy"></a>Agregar un nuevo elemento a un proyecto de flujo de trabajo (Heredado)
Después de haber creado un proyecto de flujo de trabajo usando [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado proporcionado por [!INCLUDE[vs2010](../includes/vs2010-md.md)] que tiene como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], puede agregar elementos de [!INCLUDE[wf](../includes/wf-md.md)] y otros elementos conocidos de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] al proyecto.

 En la tabla siguiente se enumeran los elementos de [!INCLUDE[wf2](../includes/wf2-md.md)] que puede agregar a un proyecto de flujo de trabajo.

|Elemento|Descripción|
|----------|-----------------|
|Actividad|Actividad con la definición de actividad en un archivo de código del diseñador y el código de usuario en un archivo de código independiente.|
|Actividad (con separación de código)|Definición de actividad expresada como marcado del flujo de trabajo y el código de usuario en un archivo de código independiente.|
|Flujo de trabajo secuencial (código)|Flujo de trabajo secuencial con la definición de flujo de trabajo en un archivo de código del diseñador y el código de usuario en un archivo de código independiente.|
|Flujo de trabajo secuencial (con separación de código)|Flujo de trabajo secuencial con la definición de flujo de trabajo expresada como marcado del flujo de trabajo y el código de usuario en un archivo de código independiente.|
|Flujo de trabajo de equipo de estado (código)|Flujo de trabajo de equipo de estado con la definición de flujo de trabajo en un archivo de código del diseñador y el código de usuario en un archivo de código independiente.|
|Flujo de trabajo de equipo de estado (con separación de código)|Flujo de trabajo de estado de equipo con la definición de flujo de trabajo expresada como marcado del flujo de trabajo y el código de usuario en un archivo de código independiente.|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>Para agregar un nuevo elemento a un proyecto de flujo de trabajo

1. En el menú **proyecto** , haga clic en **Agregar un nuevo elemento**.

     Se abre el cuadro de diálogo **Agregar un nuevo elemento** .

2. Seleccione un elemento.

     En la tabla anterior se enumeran las opciones disponibles de Windows Workflow Foundation.

3. Haga clic en **Agregar** para agregar el elemento al proyecto de flujo de trabajo.

## <a name="see-also"></a>Vea también
 [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md)