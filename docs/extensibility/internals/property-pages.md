---
title: "Páginas de propiedades | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 484d53315f836117b69270a2f43b6b780733b9f7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="property-pages"></a>Páginas de propiedades
Los usuarios pueden ver y cambiar propiedades dependientes de la configuración y - independientes del proyecto con páginas de propiedades. A **páginas de propiedades** botón está habilitado en el **propiedades** ventana o en la barra de herramientas del explorador de soluciones para los objetos que proporcionan una vista de página de propiedades del objeto seleccionado. Páginas de propiedades se crean mediante el entorno y están disponibles para las soluciones y proyectos. Sin embargo, también se pueden ponerse a disposición de los elementos de proyecto que hacen usan de propiedades dependientes de la configuración. Esta funcionalidad podría utilizarse cuando los archivos dentro de un proyecto requieren la configuración de modificador de compilador diferentes que se compila correctamente.  
  
## <a name="using-property-pages"></a>Usar páginas de propiedades  
 Si ya se muestra una página de propiedades y la selección cambia (por ejemplo, de una solución para un proyecto), la información mostrada en los cambios de páginas para mostrar las propiedades de la nueva selección. Si no hay ninguna propiedad en el objeto que admite páginas de propiedades, la página de propiedades está vacía.  
  
 Si se seleccionan varios objetos, la página de propiedades muestra la intersección de las propiedades de todos los elementos seleccionados. Si el elemento seleccionado no contiene propiedades dependientes de la configuración y la **páginas de propiedades** se hace clic en el botón en la barra de herramientas del explorador de soluciones, cambie el foco a la ventana Propiedades. Para obtener más información sobre la ventana Propiedades y la selección, consulte [extender propiedades](../../extensibility/internals/extending-properties.md).  
  
 Si se muestran las propiedades para varios objetos y cambiar un valor en una página de propiedades, todos los valores de los objetos se establecen en el nuevo valor aunque fueran inicialmente diferentes y la página estaba en blanco cuando se muestran propiedades de un objeto individual.  
  
 Hay dos tipos generales de **ProjectProperty páginas** disponibles en los cuadros de diálogo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. En la primera, para los proyectos de Visual Basic, por ejemplo, las páginas de propiedades se muestran con un formato de campo, como se muestra en la siguiente captura de pantalla. En el segundo, se muestra más adelante en esta sección, la propiedad hosts de página una cuadrícula de propiedades similares a los se encuentran en la ventana Propiedades.  
  
 ![Páginas de propiedades de Visual Basic](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
Cuadro de diálogo páginas de propiedades de proyecto con la estructura de árbol y el formato de campo  
  
 La estructura de árbol en el cuadro de diálogo páginas de propiedades no se genera utilizando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. El entorno, según el nombre de nivel pasado por el <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> interfaces, lo genera.  
  
 Hay solo dos categorías de nivel superior disponibles en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] páginas de propiedades:  
  
-   Propiedades comunes, que muestra información de configuración independientes para el objeto u objetos seleccionados. Como resultado, cuando se selecciona una de las subcategorías de propiedades comunes, las opciones de configuración, la plataforma y el Administrador de configuración en la parte superior del cuadro de diálogo no están disponibles.  
  
-   Propiedades de configuración, que contiene información de dependientes de la configuración relacionada con los parámetros de compilación, depuración y optimización de la solución o proyecto.  
  
 No se puede crear cualquier categorías adicionales de nivel superior, pero puede elegir no se muestre una u otra en la implementación de `IVsPropertyPage`. Si, por ejemplo, no tiene las propiedades independientes de la configuración para mostrar de un objeto, puede elegir no se muestre la categoría de propiedades comunes. Mostrar propiedades comunes si `ISpecifyPropertyPages` se implementa del objeto de la búsqueda del elemento y las propiedades de configuración al implementar `ISpecifyPropertyPages` en el objeto de configuración (el objeto que implementa `IVsCfg`, `IVsProjectCfg`y temas relacionados interfaces).  
  
 Cada categoría aparece en una categoría de nivel superior representa una página de propiedades independientes. Entradas de categoría y subcategoría disponibles en el cuadro de diálogo dependen de la implementación de `ISpecifyPropertyPages` y `IVsPropertyPage`.  
  
 `IDispatch`objetos para el contenedor de selección de elementos que tienen propiedades que se mostrarán en implementar páginas de propiedad `ISpecifyPropertyPages` para enumerar una lista de Id. de clase. Los identificadores de clase se pasan como variables a `ISpecifyPropertyPages` y se usan para crear instancias de las páginas de propiedades. La lista de Id. de clase también se pasa a `IVsPropertyPage` para crear la estructura de árbol de la izquierda del cuadro de diálogo. Realizar copias de las páginas de propiedades, a continuación, pasar información a la `IDispatch` objeto que implementa `ISpecifyPropertyPages` y rellene la información para cada página.  
  
 Las propiedades del objeto de examinar se recuperan mediante `IDispatch` para cada objeto en el contenedor de selección.  
  
 Implementar `Help::DisplayTopicFromF1Keyword` en el VSPackage proporciona la funcionalidad para el botón Ayuda.  
  
 Para obtener más información, consulte `IDispatch` y `ISpecifyPropertyPages`en MSDN library.  
  
 El segundo tipo de páginas de propiedades muestra en los hosts de ejemplos una forma de la cuadrícula de propiedades, como se muestra en la siguiente captura de pantalla.  
  
 ![Páginas de propiedad de VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
Cuadro de diálogo páginas de propiedades con la cuadrícula de propiedades  
  
 Las interfaces `IVSMDPropertyBrowser` y `IVSMDPropertyGrid` (declarado en vsmanaged.h) se utilizan para crear y rellenar la cuadrícula de propiedades de un cuadro de diálogo o ventana.  
  
 La arquitectura de proyectos ha cambiado considerablemente desde versiones anteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. En concreto, la noción de proyecto que está activa ha cambiado. En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], no hay ningún concepto de un proyecto activo. En entornos de desarrollo anteriores, el proyecto activo era el proyecto que genere e implemente comandos valor predeterminado sin tener en cuenta el contexto. Ahora, la solución controla y arbitra que compilar e implementar comandos se aplican a los proyectos.  
  
 Ahora, lo que antes eran un proyecto activo se captura en uno de tres maneras diferentes:  
  
-   El proyecto de inicio  
  
     Puede especificar un proyecto o proyectos desde la página de propiedades de la solución que se iniciará cuando el usuario presiona F5 o selecciona la ejecución en el menú Generar. Esto funciona de forma similar del proyecto antiguo activo en el sentido de que su nombre se muestra en el Explorador de soluciones con formato en negrita.  
  
     Puede recuperar el proyecto de inicio como una propiedad en el modelo de automatización mediante una llamada a `DTE.Solution.SolutionBuild.StartupProjects`. En un paquete VSPackage, se llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> métodos. `IVsSolutionBuildManager`está disponible como un servicio por `QueryService` en SID_SVsSolutionBuildManager. Para obtener más información, consulte [objeto de configuración de proyecto](../../extensibility/internals/project-configuration-object.md) y [configuración de la solución](../../extensibility/internals/solution-configuration.md).  
  
-   Configuración de compilación de soluciones activas  
  
     [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]tiene una configuración de soluciones activas, disponible en el modelo de automatización mediante la implementación de `DTE.Solution.SolutionBuild.ActiveConfiguration`. Una configuración de soluciones es una colección que contiene una configuración de proyecto para cada proyecto de la solución (cada proyecto puede tener varias configuraciones, en varias plataformas, con nombres diferentes). Para obtener más información sobre páginas de propiedades de la solución, vea [configuración de la solución](../../extensibility/internals/solution-configuration.md).  
  
-   Proyecto seleccionado actualmente  
  
     Implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> método para recuperar la jerarquía del proyecto y elemento de proyecto o elementos seleccionados. Desde DTE, usaría el `SelectedItems.SelectedItem.Project` y `SelectedItems.SelectedItem.ProjectItem` métodos. No hay código de ejemplo en los encabezados del núcleo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] documentos.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [Administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md)   
 [Objeto de configuración de proyecto](../../extensibility/internals/project-configuration-object.md)   
 [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)