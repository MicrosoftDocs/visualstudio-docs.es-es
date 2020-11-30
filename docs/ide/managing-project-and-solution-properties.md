---
title: Administrar propiedades de soluciones y proyectos
description: Aprenda a administrar las propiedades del proyecto y las propiedades de la solución en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b7b89588e778a142e7dd49e1a3051a9aa188ff1
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871397"
---
# <a name="manage-project-and-solution-properties"></a>Administrar propiedades de soluciones y proyectos

Los proyectos tienen propiedades que controlan muchos aspectos de la compilación, la depuración, las pruebas y la implementación. Algunas propiedades están presentes en todos los tipos de proyecto, mientras que otras son exclusivas de plataformas o idiomas específicos. Para acceder a las propiedades del proyecto, haga clic con el botón derecho en el nodo del proyecto en el **Explorador de soluciones** y elija **Propiedades** o escriba **propiedades** en el cuadro de búsqueda de la barra de menús y elija **Ventana de propiedades** en los resultados.

![Menú contextual del proyecto](../ide/media/vs2015_proj_prop_menu.gif)

Los proyectos de .NET también pueden tener un nodo de propiedades en el propio árbol del proyecto.

![Nodo de propiedades en el árbol del explorador de soluciones](../ide/media/vs2015_props_se.png)

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Administrar propiedades de soluciones y proyectos (Visual Studio para Mac)](/visualstudio/mac/managing-solutions-and-project-properties).

## <a name="project-properties"></a>Propiedades de proyecto

Las propiedades del proyecto se organizan en grupos y cada grupo tiene su propia página de propiedades. Es posible que las páginas varíen para lenguajes y tipos de proyecto diferentes.

### <a name="c-visual-basic-and-f-projects"></a>Proyectos de C#, Visual Basic y F#

En los proyectos de C#, Visual Basic y F#, las propiedades se exponen en el **Diseñador de proyectos**. En la siguiente ilustración se muestra la página **Propiedad de compilación** de un proyecto de WPF en C#:

![Diseñador de proyectos de Visual Studio](../ide/media/vs2015_proppage_build.png)

Para obtener información sobre estas páginas de propiedades en el **Diseñador de proyectos**, vea [Referencia de propiedades del proyecto](../ide/reference/project-properties-reference.md).

> [!TIP]
> Las soluciones tienen algunas propiedades, al igual que los elementos de proyecto; estas propiedades son accesibles desde la [ventana Propiedades](../ide/reference/properties-window.md), no desde el **Diseñador de proyectos**.

### <a name="c-and-javascript-projects"></a>Proyectos de C++ y JavaScript

Los proyectos de C++ y JavaScript tienen una interfaz de usuario diferente para administrar las propiedades del proyecto. Esta ilustración muestra una página de propiedades de un proyecto de C++ (las páginas de JavaScript son similares):

![Propiedades de proyecto de Visual C&#43;&#43;](../ide/media/vs2015_projprops_cpp.png)

Para obtener información sobre las propiedades de proyectos de C++, vea [Trabajar con configuraciones de proyecto (C++)](/cpp/build/working-with-project-properties). Para obtener más información sobre las propiedades de JavaScript, vea [Página de propiedades, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Propiedades de la solución

Para obtener acceso a las propiedades de la solución, haga clic con el botón derecho en el nodo de la solución en el **Explorador de soluciones** y seleccione **Propiedades**. En el cuadro de diálogo puede establecer configuraciones de proyecto para las compilaciones de **depuración** o **versión**, elegir los proyectos que van a conformar el proyecto de inicio al presionar **F5** y establecer opciones de análisis de código.

## <a name="see-also"></a>Consulte también

- [Soluciones y proyectos en Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
- [Administrar propiedades de soluciones y proyectos (Visual Studio para Mac)](/visualstudio/mac/managing-solutions-and-project-properties)
