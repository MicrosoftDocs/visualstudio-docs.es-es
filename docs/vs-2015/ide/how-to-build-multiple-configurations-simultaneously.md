---
title: Procedimiento Compilar varias configuraciones simultáneamente | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 16a509c5a8fa46620e60fb5f1497c38d97ff6330
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068319"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Procedimiento Compilar varias configuraciones simultáneamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede compilar la mayoría de los tipos de proyectos con varias o incluso todas sus configuraciones de compilación al mismo tiempo usando el cuadro de diálogo **Compilación por lotes**. Sin embargo, no puede compilar los siguientes tipos de proyectos en varias configuraciones de compilación al mismo tiempo:  
  
1. Aplicaciones de [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] compiladas para Windows mediante JavaScript.  
  
2. Todos los proyectos de Visual Basic.  
  
   Para más información sobre las configuraciones de compilación, vea [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).  
  
### <a name="to-build-a-project-in-multiple-build-configurations"></a>Para compilar un proyecto en varias configuraciones de compilación  
  
1. En la barra de menús, elija **Compilar**, **Compilación por lotes**.  
  
2. En la columna **Compilar**, seleccione las casillas de las configuraciones en las que quiere compilar un proyecto.  
  
    > [!TIP]
    >  Para editar o crear una configuración de compilación para una solución, en la barra de menús elija **Compilar**, **Administrador de configuración** para abrir el cuadro de diálogo **Administrador de configuración**. Después de editar una configuración de compilación para una solución, en el cuadro de diálogo **Compilación por lotes**, elija el botón **Recompilar** para actualizar todas las configuraciones para los proyectos de la solución.  
  
3. Elija los botones **Compilar** o **Recompilar** para compilar el proyecto con las configuraciones que especificó.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md)   
 [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md)   
 [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
