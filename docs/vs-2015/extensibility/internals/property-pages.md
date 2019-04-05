---
title: Páginas de propiedades | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a45e4a98326fe829b8f87a4ecfce669118cd9d0e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997750"
---
# <a name="property-pages"></a>Páginas de propiedades
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Los usuarios pueden ver y cambiar propiedades dependientes de la configuración y - independiente del proyecto con páginas de propiedades. Un **páginas de propiedades** botón está habilitado en el **propiedades** ventana o en la barra de herramientas del explorador de soluciones para los objetos que proporcionan una vista de página de propiedades del objeto seleccionado. Páginas de propiedades se crean el entorno y están disponibles para los proyectos y soluciones. Sin embargo, puede también ser disponible para elementos de proyecto que hacen usan de las propiedades dependientes de la configuración. Esta funcionalidad podría utilizarse cuando los archivos dentro de un proyecto requieren configuración del conmutador de compilador diferentes que se compila correctamente.  
  
## <a name="using-property-pages"></a>Usar páginas de propiedades  
 Si ya se muestra una página de propiedades y la selección cambia (por ejemplo, de una solución a un proyecto), la información mostrada en los cambios de las páginas para mostrar las propiedades de la nueva selección. Si no hay ninguna propiedad en el objeto que admite páginas de propiedades, la página de propiedades está vacía.  
  
 Si se seleccionan varios objetos, la página de propiedades muestra la intersección de las propiedades de todos los elementos seleccionados. Si el elemento seleccionado no contiene las propiedades dependientes de la configuración y el **páginas de propiedades** se hace clic en el botón de la barra de herramientas del explorador de soluciones, cambie el foco a la ventana Propiedades. Para obtener más información sobre la ventana Propiedades y la selección, consulte [extender propiedades](../../extensibility/internals/extending-properties.md).  
  
 Si se muestran las propiedades de varios objetos y cambiar un valor en una página de propiedades, todos los valores para los objetos se establecen en el nuevo valor aunque fueran inicialmente diferentes y la página estaba en blanco cuando se muestran las propiedades de un objeto individual.  
  
 Hay dos tipos generales de **ProjectProperty páginas** disponibles en los cuadros de diálogo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. En el primero, para los proyectos de Visual Basic, por ejemplo, las páginas de propiedades se muestran con un formato de campo, como se muestra en la captura de pantalla siguiente. En el segundo, se muestra más adelante en esta sección, la propiedad hosts página una cuadrícula de propiedades similar a la que se encuentra en la ventana Propiedades.  
  
 ![Páginas de propiedades de Visual Basic](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
Cuadro de diálogo páginas de propiedades de proyecto con la estructura de árbol y el formato de campo  
  
 La estructura de árbol en el cuadro de diálogo páginas de propiedades no se compila con <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. El entorno, en función del nombre de nivel le pasado por el <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> interfaces, lo crea.  
  
 Hay solo dos categorías de nivel superior en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] páginas de propiedades:  
  
- Propiedades comunes, que muestra información de configuración independientes para el objeto u objetos seleccionados. Como resultado, cuando se selecciona una de las subcategorías de propiedades comunes, no están disponibles las opciones de configuración, plataforma y Configuration Manager en la parte superior del cuadro de diálogo.  
  
- Propiedades de configuración, que contiene información de dependiente de la configuración relacionada con los parámetros de compilación, la optimización y depuración de la solución o proyecto.  
  
  No se puede crear todas las categorías de nivel superior adicionales, pero puede elegir no se muestre una u otra en la implementación de `IVsPropertyPage`. Si, por ejemplo, no tiene las propiedades independientes de la configuración que se muestra en un objeto, puede elegir no se muestre la categoría de propiedades comunes. Mostrar propiedades comunes si `ISpecifyPropertyPages` se implementa desde el objeto de examen del elemento y las propiedades de configuración cuando implemente `ISpecifyPropertyPages` en el objeto de configuración (el objeto que implementa `IVsCfg`, `IVsProjectCfg`y relacionados interfaces).  
  
  Cada categoría aparece en la categoría de nivel superior representa una página de propiedades independientes. Entradas de categoría y subcategoría disponibles en el cuadro de diálogo están determinadas por la implementación de `ISpecifyPropertyPages` y `IVsPropertyPage`.  
  
  `IDispatch` objetos de elementos que tienen propiedades que se mostrarán en implementar páginas de propiedades en el contenedor de selección `ISpecifyPropertyPages` para enumerar una lista de Id. de clase. Los identificadores de clase se pasan como variables a `ISpecifyPropertyPages` y se usan para crear instancias de las páginas de propiedades. También pasa a la lista de Id. de clase `IVsPropertyPage` para crear la estructura de árbol de la izquierda del cuadro de diálogo. Realizar copias de las páginas de propiedades, a continuación, pasar información a la `IDispatch` objeto que implementa `ISpecifyPropertyPages` y rellena la información para cada página.  
  
  Las propiedades del objeto de exploración se recuperan mediante `IDispatch` para cada objeto en el contenedor de selección.  
  
  Implementar `Help::DisplayTopicFromF1Keyword` en el VSPackage proporciona la funcionalidad para el botón Ayuda.  
  
  Para obtener más información, consulte `IDispatch` y `ISpecifyPropertyPages`en MSDN library.  
  
  El segundo tipo de páginas de propiedades muestra en los hosts de ejemplos un formulario de la cuadrícula de propiedades, como se muestra en la captura de pantalla siguiente.  
  
  ![Las páginas de propiedad VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
  Cuadro de diálogo páginas de propiedades con la cuadrícula de propiedades  
  
  Las interfaces `IVSMDPropertyBrowser` y `IVSMDPropertyGrid` (declarado en vsmanaged.h) se usan para crear y rellenar la cuadrícula de propiedades dentro de un cuadro de diálogo o ventana.  
  
  La arquitectura de proyectos se ha cambiado considerablemente desde las versiones anteriores de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. En concreto, la noción de proyecto al que está activa ha cambiado. En [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], no hay ningún concepto de un proyecto activo. En entornos de desarrollo anterior, el proyecto activo era el proyecto de compilación e implementación de comandos sería predeterminado a independientemente del contexto. Ahora, la solución controla y arbitra que compile e implemente los comandos se aplican a los proyectos.  
  
  Ahora, que anteriormente era un proyecto activo se captura en uno de tres maneras diferentes:  
  
- El proyecto de inicio  
  
   Puede especificar un proyecto o proyectos de la página de propiedades de la solución que se iniciará cuando el usuario presiona F5 o selecciona la ejecución en el menú compilar. Esto funciona de forma similar al antiguo proyecto activo en el sentido de que su nombre se muestra en el Explorador de soluciones con la fuente en negrita.  
  
   Puede recuperar el proyecto de inicio como una propiedad en el modelo de automatización mediante una llamada a `DTE.Solution.SolutionBuild.StartupProjects`. En un VSPackage, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> métodos. `IVsSolutionBuildManager` está disponible como un servicio por `QueryService` en SID_SVsSolutionBuildManager. Para obtener más información, consulte [objeto de configuración de proyecto](../../extensibility/internals/project-configuration-object.md) y [configuración de la solución](../../extensibility/internals/solution-configuration.md).  
  
- Configuración de compilación de soluciones activas  
  
   [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tiene una configuración de soluciones activas, disponible en el modelo de automatización mediante la implementación `DTE.Solution.SolutionBuild.ActiveConfiguration`. Una configuración de soluciones es una colección que contiene una configuración de proyecto para cada proyecto de la solución (cada proyecto puede tener varias configuraciones en varias plataformas, con nombres diferentes). Para obtener más información sobre páginas de propiedades de la solución, vea [configuración de la solución](../../extensibility/internals/solution-configuration.md).  
  
- Proyecto seleccionado actualmente  
  
   Implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> método para recuperar la jerarquía del proyecto y elemento de proyecto o elementos seleccionados. De DTE, usaría el `SelectedItems.SelectedItem.Project` y `SelectedItems.SelectedItem.ProjectItem` métodos. No hay código de ejemplo bajo los encabezados en el núcleo de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] documentos.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [Administración de las opciones de configuración](../../extensibility/internals/managing-configuration-options.md)   
 [Objeto de configuración de proyecto](../../extensibility/internals/project-configuration-object.md)   
 [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)
