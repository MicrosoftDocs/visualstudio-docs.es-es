---
title: "P&#225;ginas de propiedades | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Opciones de configuración, cambiar propiedades"
  - "páginas de propiedades"
  - "páginas de propiedades, cambie las opciones de configuración"
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# P&#225;ginas de propiedades
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Los usuarios pueden ver y cambiar el proyecto configuración\-dependiente y \- propiedades independientes utilizando las páginas de propiedades.  Un botón de **Páginas de propiedades** está habilitada en la ventana de **Propiedades** o en la barra de herramientas del explorador de soluciones para objetos que proporcionan una vista de la página de propiedades del objeto seleccionado.  Las páginas de propiedades son creados por el entorno y están disponibles para soluciones y proyectos.  Pueden, sin embargo, también se crearon disponibles para los elementos de proyecto que hacen uso de propiedades dependientes.  Esta capacidad puede utilizarse cuando los archivos de un proyecto requieren valores diferentes de modificador del compilador compilar correctamente.  
  
## Utilizando las páginas de propiedades  
 Si una página de propiedades se muestra ya y los cambios de selección \(por ejemplo, una solución a un proyecto\), la información mostrada en los cambios de las páginas para mostrar las propiedades de la nueva selección.  Si no hay propiedades en el objeto que las páginas de propiedades de, la página de propiedades están vacías.  
  
 Si varios objetos son seleccionado, la página de propiedades muestra la intersección de las propiedades para todos los elementos seleccionados.  Si el elemento seleccionado no contiene propiedades dependientes y el botón de **Páginas de propiedades** en la barra de herramientas del explorador de soluciones se hace clic, cambia el foco a la ventana Propiedades.  Para obtener más información sobre la ventana Propiedades y la selección, vea [Extender propiedades](../../extensibility/internals/extending-properties.md).  
  
 Si las propiedades se muestran de varios objetos y cambia el valor de una página de propiedades, todos los valores de los objetos se establecen al nuevo valor aunque se inicialmente diferentes y la página era espacio en blanco cuando las propiedades de un objeto individuales se mostrarán.  
  
 Hay dos tipos generales de cuadros de diálogo de **proyectoPáginas de propiedades** disponibles en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  En el primero, para los proyectos de Visual Basic, por ejemplo, las páginas de propiedades se muestran con un formato de campo, como se muestra en el captura de pantalla siguiente.  En el segundo, que se muestra más adelante en esta sección, los hosts de la página de propiedades una cuadrícula de propiedades similar a la que se encuentra en la ventana Propiedades.  
  
 ![Página Propiedades de Visual Basic](~/extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
Cuadro de diálogo páginas de propiedades del proyecto con formato de campo y la estructura de árbol  
  
 La estructura de árbol en el cuadro de diálogo páginas de propiedades no se compila utilizando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>.  El entorno, basándose en el nombre nivel pasado al <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> y las interfaces de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> , compilarlo.  
  
 Sólo hay dos categorías de nivel superior disponibles en las páginas de propiedades de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] :  
  
-   Propiedades comunes, que muestra información de la independientes para el objeto o los objetos seleccionados.  Como resultado, cuando una de las subcategorías de las propiedades comunes está seleccionado, las opciones de configuración, de la plataforma, y el administrador de configuración a través de la parte superior del cuadro de diálogo no están disponibles.  
  
-   Propiedades de configuración, que contiene información configuración\-dependiente relacionado con los parámetros de depuración, de optimización, y compilación de la solución o proyecto.  
  
 No puede crear ninguna categorías de nivel superior adicional, pero puede elegir no mostrar uno u otro en la implementación de `IVsPropertyPage`.  Si, por ejemplo, no tiene ninguna propiedad de la independientes a mostrar para un objeto, puede decidir no mostrar la categoría de propiedades comunes.  Se muestra propiedades comunes si `ISpecifyPropertyPages` se implementa de objetos y propiedades de configuración de examen del elemento al implementar `ISpecifyPropertyPages` en el objeto de configuración \(el objeto que implementa `IVsCfg`, `IVsProjectCfg`, e interfaces relacionadas\).  
  
 Cada categoría mostrada bajo la categoría de nivel superior representa una página de propiedades independiente.  Las entradas de la categoría y la subcategoría disponibles en el cuadro de diálogo vienen determinadas por la implementación de `ISpecifyPropertyPages` y de `IVsPropertyPage`.  
  
 objetos de`IDispatch` para los elementos del contenedor de selección que tienen propiedades que se van a mostrar en la implementación `ISpecifyPropertyPages` de las páginas de propiedades para enumerar una lista de id. de la clase.  Los id. de clase se pasan como variables a `ISpecifyPropertyPages` y se utilizan para crear instancias de las páginas de propiedades.  La lista de id. de clase también se pasa a `IVsPropertyPage` para crear la estructura de árbol a la izquierda del cuadro de diálogo.  Las páginas de propiedades a devuelven información al objeto de `IDispatch` que implementa `ISpecifyPropertyPages` y rellena la información para cada página.  
  
 Las propiedades del objeto de examen se recuperan utilizando `IDispatch` para cada objeto del contenedor de selección.  
  
 Implementar `Help::DisplayTopicFromF1Keyword` en el paquete VSPackage proporciona la funcionalidad para el botón de Ayuda.  
  
 Para obtener más información, vea `IDispatch` y `ISpecifyPropertyPages`en MSDN Library.  
  
 El segundo tipo de páginas de propiedades se muestran en los hosts de los ejemplos un formulario de la cuadrícula de propiedades, como se muestra en el captura de pantalla siguiente.  
  
 ![Páginas de propiedades de VC](~/extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
Cuadro de diálogo páginas de propiedades con la cuadrícula de propiedades  
  
 Las interfaces `IVSMDPropertyBrowser` y `IVSMDPropertyGrid` \(declarados en vsmanaged.h\) se utilizan para crear y rellenar la cuadrícula de propiedades dentro de un cuadro de diálogo o ventana.  
  
 La arquitectura de proyectos ha cambiado considerablemente de versiones más recientes de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  En particular, la noción del proyecto está activo ha cambiado.  En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], no hay ningún concepto de un proyecto activo.  En entornos de desarrollo anteriores, el proyecto activo era el proyecto se compila y implementan comandos establecerán como valor predeterminado independientemente del contexto.  Ahora, la solución controla y arbitra que compilan y implementan comandos se aplican a qué proyectos.  
  
 Qué estaba previamente un proyecto activo ahora se captura en una de tres maneras diferentes:  
  
-   El proyecto de inicio  
  
     Puede especificar un proyecto o proyectos de la página de propiedades de la solución que se pudo cuando el usuario presiona F5 o selecciona ejecute desde el menú de compilación.  Esto funciona de forma similar al anterior proyecto activo en el sentido de que el nombre se muestra en el explorador de soluciones con la fuente negrita.  
  
     Puede recuperar el proyecto de inicio como propiedad del modelo de automatización llamando a `DTE.Solution.SolutionBuild.StartupProjects`.  En un Paquete, se llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> o métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> .  `IVsSolutionBuildManager` está disponible como servicio por `QueryService` en SID\_SVsSolutionBuildManager.  Para obtener más información, vea [Objeto de configuración de proyecto](../../extensibility/internals/project-configuration-object.md) y [Configuración de soluciones](../../extensibility/internals/solution-configuration.md).  
  
-   Configuración de compilación de soluciones activa  
  
     [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tiene una configuración de soluciones activa, disponible en el modelo de automatización implementando `DTE.Solution.SolutionBuild.ActiveConfiguration`.  Una configuración de soluciones es una colección que contiene una configuración de proyecto para cada proyecto de la solución \(cada proyecto puede tener varias configuraciones, en varias plataformas, con nombres diferentes\).  Para obtener más información relacionada con las páginas de propiedades de la solución, vea [Configuración de soluciones](../../extensibility/internals/solution-configuration.md).  
  
-   Proyecto seleccionado  
  
     Implemente el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> para recuperar la jerarquía del proyecto y el elemento de proyecto o los elementos seleccionados.  DTE, utilice los métodos de `SelectedItems.SelectedItem.Project` y de `SelectedItems.SelectedItem.ProjectItem` .  Hay código muestra en esos encabezados en documentos básicos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [Administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md)   
 [Objeto de configuración de proyecto](../../extensibility/internals/project-configuration-object.md)   
 [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)