---
title: "Cómo: agregar un nuevo elemento a un proyecto de flujo de trabajo (heredado) | Documentos de Microsoft"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- sequential workflows, adding to workflow projects
- workflows, adding new items
- state machine workflows, adding to workflow projects
- activities, adding to workflow projects
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d2b0c644854f8f08ff7aeeb05f92fe3fd359f45e
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-a-new-item-to-a-workflow-project-legacy"></a>Agregar un nuevo elemento a un proyecto de flujo de trabajo (Heredado)
Después de haber creado un proyecto de flujo de trabajo mediante el Diseñador de flujo de trabajo de Windows heredado proporcionado por [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] que tiene como destino el [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], puede agregar [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] elementos y otro familiar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] elementos a su proyecto.

 En la tabla siguiente se enumeran los elementos de [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] que puede agregar a un proyecto de flujo de trabajo.

|Item|Descripción|
|----------|-----------------|
|Actividad|Actividad con la definición de actividad en un archivo de código del diseñador y el código de usuario en un archivo de código independiente.|
|Actividad (con separación de código)|Definición de actividad expresada como marcado del flujo de trabajo y el código de usuario en un archivo de código independiente.|
|Flujo de trabajo secuencial (código)|Flujo de trabajo secuencial con la definición de flujo de trabajo en un archivo de código del diseñador y el código de usuario en un archivo de código independiente.|
|Flujo de trabajo secuencial (con separación de código)|Flujo de trabajo secuencial con la definición de flujo de trabajo expresada como marcado del flujo de trabajo y el código de usuario en un archivo de código independiente.|
|Flujo de trabajo de equipo de estado (código)|Flujo de trabajo de equipo de estado con la definición de flujo de trabajo en un archivo de código del diseñador y el código de usuario en un archivo de código independiente.|
|Flujo de trabajo de equipo de estado (con separación de código)|Flujo de trabajo de estado de equipo con la definición de flujo de trabajo expresada como marcado del flujo de trabajo y el código de usuario en un archivo de código independiente.|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>Para agregar un nuevo elemento a un proyecto de flujo de trabajo

1.  En el **proyecto** menú, haga clic en **agregar un nuevo elemento**.

     El **agregar un nuevo elemento** abre el cuadro de diálogo.

2.  Seleccione un elemento.

     En la tabla anterior se enumeran las opciones disponibles de Windows Workflow Foundation.

3.  Haga clic en **agregar** para agregar el elemento al proyecto de flujo de trabajo.

## <a name="see-also"></a>Vea también

- [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md)