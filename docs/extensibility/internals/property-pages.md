---
title: Páginas de propiedades | Microsoft Docs
description: Obtenga información sobre cómo trabajar con páginas de propiedades para el nuevo tipo de proyecto en el SDK de Visual Studio, que permite a los usuarios ver y cambiar las propiedades del proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 88ebf99ef2361a232c4a5c4c02b9a140155d66e9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903416"
---
# <a name="property-pages"></a>Páginas de propiedades
Los usuarios pueden ver y cambiar las propiedades dependientes de la configuración del proyecto e independientes mediante páginas de propiedades. Un **botón Páginas de**  propiedades está habilitado en la ventana Propiedades o en Explorador de soluciones barra de herramientas para los objetos que proporcionan una vista de página de propiedades del objeto seleccionado. El entorno crea páginas de propiedades y están disponibles para soluciones y proyectos. Sin embargo, también pueden estar disponibles para los elementos de proyecto que usan propiedades dependientes de la configuración. Esta funcionalidad se puede usar cuando los archivos dentro de un proyecto requieren una configuración de modificador del compilador diferente para compilarse correctamente.

## <a name="using-property-pages"></a>Usar páginas de propiedades
 Si ya se muestra una página de propiedades y la selección cambia (por ejemplo, de una solución a un proyecto), la información mostrada en las páginas cambia para mostrar las propiedades de la nueva selección. Si no hay ninguna propiedad en el objeto que admita páginas de propiedades, la página de propiedades está vacía.

 Si se seleccionan varios objetos, la página de propiedades muestra la intersección de las propiedades de todos los elementos seleccionados. Si el elemento seleccionado no contiene propiedades  dependientes de la configuración y se hace clic en el botón Páginas de propiedades de la barra de herramientas Explorador de soluciones, el foco cambia al ventana Propiedades. Para obtener más información relacionada con el ventana Propiedades y la selección, vea [Extender propiedades](../../extensibility/internals/extending-properties.md).

 Si se muestran propiedades para varios objetos y se cambia un valor en una página de propiedades, todos los valores de los objetos se establecen en el nuevo valor incluso si inicialmente eran diferentes y la página estaba en blanco cuando se mostraron las propiedades de un objeto individual.

 Hay dos tipos generales de cuadros de diálogo **ProjectProperty Pages** disponibles en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . En la primera, para Visual Basic, por ejemplo, las páginas de propiedades se muestran con un formato de campo, como se muestra en la captura de pantalla siguiente. En la segunda, que se muestra más adelante en esta sección, la página de propiedades hospeda una cuadrícula de propiedades similar a la que se encuentra en la ventana Propiedades.

 ![Visual Basic páginas de propiedades](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Cuadro de diálogo Páginas de propiedades del proyecto con formato de campo y estructura de árbol

 La estructura de árbol del cuadro de diálogo Páginas de propiedades no se ha creado mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . El entorno, basado en el nombre de nivel pasado por y las <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> interfaces, lo compila.

 Solo hay dos categorías de nivel superior disponibles en las [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] páginas de propiedades:

- Propiedades comunes, que muestra información independiente de la configuración para el objeto u objetos seleccionados. Como resultado, cuando se selecciona una de las subcategorías Propiedades comunes, las opciones Configuración, Plataforma y Administrador de configuración de la parte superior del cuadro de diálogo no están disponibles.

- Propiedades de configuración, que contiene información dependiente de la configuración relacionada con los parámetros Depuración, Optimización y Compilación para la solución o el proyecto.

  No puede crear categorías de nivel superior adicionales, pero puede optar por no mostrar una u otra en la implementación de `IVsPropertyPage` . Si, por ejemplo, no tiene ninguna propiedad independiente de la configuración para mostrar para un objeto, puede optar por no mostrar la categoría Propiedades comunes. Las propiedades comunes se muestran si se implementa desde el objeto de exploración del elemento y las propiedades de configuración al implementar en el objeto de configuración (el objeto que implementa , y las `ISpecifyPropertyPages` `ISpecifyPropertyPages` `IVsCfg` `IVsProjectCfg` interfaces relacionadas).

  Cada categoría mostrada en una categoría de nivel superior representa una página de propiedades independiente. Las entradas de categoría y subcategoría disponibles en el cuadro de diálogo están determinadas por la implementación de `ISpecifyPropertyPages` y `IVsPropertyPage` .

  `IDispatch` Los objetos para los elementos del contenedor de selección que tienen propiedades que se mostrarán en las páginas de propiedades implementan para `ISpecifyPropertyPages` enumerar una lista de los ID de clase. Los IDs de clase se pasan como variables a y se usan para crear `ISpecifyPropertyPages` instancias de las páginas de propiedades. La lista de los IDs de clase también se pasa a para crear la estructura de `IVsPropertyPage` árbol a la izquierda del cuadro de diálogo. A continuación, las páginas de propiedades pasan información al objeto que implementa y `IDispatch` rellena la información de cada `ISpecifyPropertyPages` página.

  Las propiedades del objeto browse se recuperan mediante `IDispatch` para cada objeto del contenedor de selección.

  La implementación `Help::DisplayTopicFromF1Keyword` en el VSPackage proporciona la funcionalidad del botón Ayuda.

  Para obtener más información, `IDispatch` vea y en MSDN `ISpecifyPropertyPages` Library.

  El segundo tipo de páginas de propiedades que se muestran en los ejemplos hospeda un formulario de la cuadrícula de propiedades, como se muestra en la captura de pantalla siguiente.

  ![Páginas de propiedades de VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Cuadro de diálogo Páginas de propiedades con cuadrícula de propiedades

  Las interfaces `IVSMDPropertyBrowser` y (declaradas en vsmanaged.h) se usan para crear y rellenar la cuadrícula de propiedades dentro de un cuadro `IVSMDPropertyGrid` de diálogo o ventana.

  La arquitectura de los proyectos ha cambiado considerablemente con las versiones anteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . En concreto, ha cambiado la noción de qué proyecto está activo. En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , no hay ningún concepto de un proyecto activo. En entornos de desarrollo anteriores, el proyecto activo era el proyecto que compilaba e implementaba comandos de forma predeterminada, independientemente del contexto. Ahora, la solución controla y desasoye qué comandos de compilación e implementación se aplican a los proyectos.

  Lo que antes era un proyecto activo ahora se captura de tres maneras diferentes:

- El proyecto de inicio

   Puede especificar un proyecto o proyectos desde la página de propiedades de la solución que se iniciarán cuando el usuario presione F5 o seleccione Ejecutar en el menú Compilar. Esto funciona de forma similar al proyecto activo anterior en el sentido de que su nombre se muestra en Explorador de soluciones con fuente en negrita.

   Puede recuperar el proyecto de inicio como una propiedad en el modelo de automatización llamando a `DTE.Solution.SolutionBuild.StartupProjects` . En un VSPackage, se llama a los <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> métodos o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> . `IVsSolutionBuildManager` está disponible como servicio en `QueryService` SID_SVsSolutionBuildManager. Para obtener más información, vea [Project Configuration Object y](../../extensibility/internals/project-configuration-object.md) Solution [Configuration](../../extensibility/internals/solution-configuration.md).

- Configuración de compilación de soluciones activas

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tiene una configuración de solución activa, disponible en el modelo de automatización mediante la implementación de `DTE.Solution.SolutionBuild.ActiveConfiguration` . Una configuración de solución es una colección que contiene una configuración de proyecto para cada proyecto de la solución (cada proyecto puede tener varias configuraciones, en varias plataformas, con nombres diferentes). Para obtener más información relacionada con las páginas de propiedades de la solución, vea [Configuración de la solución](../../extensibility/internals/solution-configuration.md).

- Proyecto seleccionado actualmente

   Implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> método para recuperar la jerarquía del proyecto y el elemento de proyecto o los elementos seleccionados. En DTE, usaría los `SelectedItems.SelectedItem.Project` `SelectedItems.SelectedItem.ProjectItem` métodos y . Hay código de ejemplo bajo esos encabezados en los documentos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] principales.

## <a name="see-also"></a>Consulta también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Objeto de configuración del proyecto](../../extensibility/internals/project-configuration-object.md)
- [Configuración de la solución](../../extensibility/internals/solution-configuration.md)
