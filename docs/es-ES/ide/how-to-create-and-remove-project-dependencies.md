---
title: 'Cómo: Crear y quitar dependencias del proyecto | Microsoft Docs'
ms.custom: ''
ms.date: 06/21/2017
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ProjectDependenciesDlg
helpviewer_keywords:
- vs.build.projectdependencies
- project dependencies
- builds [Visual Studio], setting up
- project build configurations, dependencies
- dependencies, project
- projects [Visual Studio], dependencies
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4b9a655f61c7e91a1626038781601401a539bbb1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Cómo: Crear y quitar dependencias del proyecto
Al compilar una solución que contiene varios proyectos, puede ser necesario compilar determinados proyectos primero para generar código que usan otros proyectos. Cuando un proyecto consume código ejecutable generado por otro proyecto, al proyecto que genera el código se le hace referencia como una dependencia de proyecto del proyecto que consume el código. Dichas relaciones de dependencia pueden definirse en el cuadro de diálogo **Dependencias del proyecto**.  

### <a name="to-assign-dependencies-to-projects"></a>Para asignar dependencias a los proyectos  

1.  En el **Explorador de soluciones**, seleccione un proyecto.  

2.  En el menú **Proyecto**, pulse **Dependencias del proyecto**.  

     Se abre el cuadro de diálogo **Dependencias del proyecto**.  

    > [!NOTE]
    >  La opción **Dependencias del proyecto** solo está disponible en una solución con más de un proyecto.  

3.  En la pestaña **Dependencias**, seleccione un proyecto del menú desplegable **Proyecto**.  

4.  En el campo **Depende de**, seleccione la casilla de cualquier otro proyecto que debe compilarse antes de que lo haga este proyecto.  

 Su solución debe constar de más de un proyecto antes de que pueda crear dependencias de proyecto.  

### <a name="to-remove-dependencies-from-projects"></a>Para quitar las dependencias de los proyectos  

1.  En el **Explorador de soluciones**, seleccione un proyecto.  

2.  En el menú **Proyecto**, pulse **Dependencias del proyecto**.  

     Se abre el cuadro de diálogo **Dependencias del proyecto**.  

    > [!NOTE]
    >  La opción **Dependencias del proyecto** solo está disponible en una solución con más de un proyecto.  

3.  En la pestaña **Dependencias**, seleccione un proyecto del menú desplegable **Proyecto**.  

4.  En el campo **Depende de**, desactive las casillas junto a cualquier otro proyecto que ya no son dependencias de este proyecto.  

## <a name="see-also"></a>Vea también  
 [Compilar y limpiar proyectos y soluciones en Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Compilar y generar](../ide/compiling-and-building-in-visual-studio.md)   
 [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md)   
 [Administración de propiedades de soluciones y proyectos](managing-project-and-solution-properties.md)

