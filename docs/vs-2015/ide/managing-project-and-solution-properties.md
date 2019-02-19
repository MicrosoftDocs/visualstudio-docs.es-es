---
title: Administrar propiedades de soluciones y proyectos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d727efc0-1096-4ede-84b6-31a65da22ac0
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f3e9ff4acbfd6df1980a3882311b3d3c4611e064
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54758126"
---
# <a name="managing-project-and-solution-properties"></a>Administrar propiedades de soluciones y proyectos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los proyectos tienen propiedades que controlan muchos aspectos de la compilación, la depuración, las pruebas y la implementación. Algunas propiedades están presentes en todos los tipos de proyecto, mientras que otras son exclusivas de plataformas o idiomas específicos. Para obtener acceso a las propiedades del proyecto, haga clic con el botón derecho en el nodo del proyecto en el Explorador de soluciones y seleccione Propiedades, o escriba propiedades en el cuadro de búsqueda **Inicio rápido** de la barra de menús.  
  
 ![Menú contextual del proyecto](../ide/media/vs2015-proj-prop-menu.gif "vs2015_proj_prop_menu")  
  
 Los proyectos de .NET también tienen un nodo de propiedades en el propio árbol del proyecto.  
  
 ![Nodo de propiedades en el árbol del Explorador de soluciones](../ide/media/vs2015-props-se.png "VS2015_Props_SE")  
  
> [!TIP]
>  Las soluciones tienen algunas propiedades, al igual que los elementos de proyecto; estas propiedades son accesibles desde la [ventana Propiedades](../ide/reference/properties-window.md), no desde el **Diseñador de proyectos**.  
  
## <a name="project-properties"></a>Propiedades del proyecto  
 Las propiedades del proyecto se organizan en grupos. Cada grupo tiene su propia página de propiedades y las páginas pueden ser diferentes según el lenguaje y el tipo de proyecto.  
  
### <a name="c-and-visual-basic-projects"></a>Proyectos de C# y Visual Basic  
 En los proyectos de C# y Visual Basic, las propiedades se exponen en el **Diseñador de proyectos**. En la siguiente ilustración se muestra la página Propiedad de compilación de un proyecto de WPF en C#:  
  
 ![Diseñador de proyectos de Visual Studio](../ide/media/vs2015-proppage-build.png "VS2015_PropPage_Build")  
  
 Para obtener información sobre estas páginas de propiedades en el Diseñador de proyectos, vea [Referencia de propiedades del proyecto](../ide/reference/project-properties-reference.md).  
  
### <a name="c-and-javascript-projects"></a>Proyectos de C++ y JavaScript  
 Los proyectos de C++ y JavaScript tienen una interfaz de usuario diferente para administrar las propiedades del proyecto. Esta ilustración muestra una página de propiedades de un proyecto de C++ (las páginas de JavaScript son similares):  
  
 ![Propiedades de proyecto de Visual C&#43;&#43;](../ide/media/vs2015-projprops-cpp.png "VS2015_ProjProps_cpp")  
  
 Para obtener información sobre las propiedades de proyectos de C++, vea [Trabajar con configuraciones de proyecto](http://msdn.microsoft.com/library/9b0d6f8b-7d4e-4e61-aa75-7d14944816cd). Para más información sobre las propiedades de JavaScript, vea [Página de propiedades, JavaScript](../ide/reference/property-pages-javascript.md).  
  
## <a name="solution-properties"></a>Propiedades de la solución  
 Para obtener acceso a las propiedades de la solución, haga clic con el botón derecho en el nodo de la solución en el **Explorador de soluciones** y seleccione **Propiedades**. En el diálogo puede establecer configuraciones de proyecto para las compilaciones de depuración o de versión, elegir los proyectos que conformarán el proyecto de inicio al presionar F5 y establecer opciones de análisis de código.  
  
## <a name="see-also"></a>Vea también  
 [Soluciones y proyectos en Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
