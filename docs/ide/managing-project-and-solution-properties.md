---
title: "Administrar propiedades de soluciones y proyectos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d727efc0-1096-4ede-84b6-31a65da22ac0
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Administrar propiedades de soluciones y proyectos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los proyectos tienen propiedades que controlan muchos aspectos de la compilación, la depuración, las pruebas y la implementación.  Algunas propiedades están presentes en todos los tipos de proyecto, mientras que otras son exclusivas de plataformas o idiomas específicos.  Para acceder a las propiedades del proyecto, haga clic con el botón derecho en el nodo del proyecto en el Explorador de soluciones y elija Propiedades, o escriba propiedades en el cuadro de búsqueda **Inicio rápido** de la barra de menús.  
  
 ![Menú contextual del proyecto](../ide/media/vs2015_proj_prop_menu.png "vs2015\_proj\_prop\_menu")  
  
 Los proyectos de .NET también tienen un nodo de propiedades en el propio árbol del proyecto.  
  
 ![Nodo de propiedades en el árbol del explorador de soluciones](../ide/media/vs2015_props_se.png "VS2015\_Props\_SE")  
  
> [!TIP]
>  Las soluciones tienen algunas propiedades, al igual que los elementos de proyecto; estas propiedades son accesibles desde la [Ventana Propiedades](../ide/reference/properties-window.md), no desde el **Diseñador de proyectos**.  
  
## Propiedades del proyecto  
 Las propiedades del proyecto se organizan en grupos. Cada grupo tiene su propia página de propiedades y las páginas pueden ser diferentes según el lenguaje y el tipo de proyecto.  
  
### Proyectos de C\# y Visual Basic  
 En los proyectos de C\# y Visual Basic, las propiedades se exponen en el **Diseñador de proyectos**.  En la siguiente ilustración se muestra la página Propiedad de compilación de un proyecto de WPF en C\#:  
  
 ![Diseñador de proyectos de Visual Studio](../ide/media/vs2015_proppage_build.png "VS2015\_PropPage\_Build")  
  
 Para obtener información sobre estas páginas de propiedades en el Diseñador de proyectos, consulte [Referencia de propiedades del proyecto](../ide/reference/project-properties-reference.md).  
  
### Proyectos de C\+\+ y JavaScript  
 Los proyectos de C\+\+ y JavaScript tienen una interfaz de usuario diferente para administrar las propiedades del proyecto.  Esta ilustración muestra una página de propiedades de un proyecto de C\+\+ \(las páginas de JavaScript son similares\):  
  
 ![Propiedades de proyecto de Visual C&#43;&#43;](../ide/media/vs2015_projprops_cpp.png "VS2015\_ProjProps\_cpp")  
  
 Para obtener información sobre las propiedades de proyectos de C\+\+, vea [Trabajar con configuraciones de proyecto](/visual-cpp/ide/working-with-project-properties).  Para obtener más información sobre las propiedades de JavaScript, vea [Página de propiedades, JavaScript](../ide/reference/property-pages-javascript.md).  
  
## Propiedades de la solución  
 Para acceder a las propiedades de la solución, haga clic con el botón derecho en el nodo de la solución en el **Explorador de soluciones** y elija **Propiedades**.  En el diálogo puede establecer configuraciones de proyecto para las compilaciones de depuración o de versión, elegir los proyectos que conformarán el proyecto de inicio al presionar F5 y establecer opciones de análisis de código.  
  
## Vea también  
 [Soluciones y proyectos](../ide/solutions-and-projects-in-visual-studio.md)