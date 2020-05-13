---
title: Páginas de propiedades ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac788f51bcdc52cd39469a272909890333c5016b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706056"
---
# <a name="property-pages"></a>Páginas de propiedades
Los usuarios pueden ver y cambiar las propiedades independientes y dependientes de la configuración del proyecto mediante páginas de propiedades. Un botón **Páginas** de propiedades está habilitado en la ventana **Propiedades** o en la barra de herramientas del Explorador de soluciones para los objetos que proporcionan una vista de página de propiedades del objeto seleccionado. Las páginas de propiedades son creadas por el entorno y están disponibles para soluciones y proyectos. Sin embargo, también pueden estar disponibles para los elementos de proyecto que hacen uso de propiedades dependientes de la configuración. Esta funcionalidad se puede usar cuando los archivos de un proyecto requieren una configuración de conmutador del compilador diferente para compilar correctamente.

## <a name="using-property-pages"></a>Uso de páginas de propiedades
 Si ya se muestra una página de propiedades y la selección cambia (por ejemplo, de una solución a un proyecto), la información que se muestra en las páginas cambia para mostrar las propiedades de la nueva selección. Si no hay propiedades en el objeto que admiten páginas de propiedades, la página de propiedades está vacía.

 Si se seleccionan varios objetos, la página de propiedades muestra la intersección de las propiedades de todos los elementos seleccionados. Si el elemento seleccionado no contiene propiedades dependientes de la configuración y se hace clic en el botón **Páginas** de propiedades de la barra de herramientas del Explorador de soluciones, el foco cambia a la ventana Propiedades. Para obtener más información sobre la ventana Propiedades y la selección, consulte [Ampliación de propiedades](../../extensibility/internals/extending-properties.md).

 Si se muestran propiedades para varios objetos y se cambia un valor en una página de propiedades, todos los valores de los objetos se establecen en el nuevo valor, incluso si inicialmente eran diferentes y la página estaba en blanco cuando se mostraban las propiedades de un objeto individual.

 Hay dos tipos generales de cuadros [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de diálogo **Páginas** de propiedades de proyecto disponibles en . En el primero, para proyectos de Visual Basic, por ejemplo, las páginas de propiedades se muestran con un formato de campo, como se muestra en la siguiente captura de pantalla. En la segunda, que se muestra más adelante en esta sección, la página de propiedades hospeda una cuadrícula de propiedades similar a la que se encuentra en la ventana Propiedades.

 ![Páginas de propiedades de Visual Basic](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Cuadro de diálogo Páginas de propiedades del proyecto con formato de campo y estructura de árbol

 La estructura de árbol del cuadro de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>diálogo Páginas de propiedades no se crea mediante . El entorno, basado en el nombre <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> nivel que le pasan las interfaces y las, lo compila.

 Solo hay dos categorías de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nivel superior disponibles en las páginas de propiedades:

- Propiedades comunes, que muestra información independiente de la configuración para el objeto u objetos seleccionados. Como resultado, cuando se selecciona una de las subcategorías Propiedades comunes, las opciones Configuración, Plataforma y Administrador de configuración en la parte superior del cuadro de diálogo no están disponibles.

- Propiedades de configuración, que contiene información dependiente de la configuración relacionada con los parámetros de depuración, optimización y compilación para la solución o el proyecto.

  No puede crear ninguna categoría de nivel superior adicional, pero puede optar por `IVsPropertyPage`no mostrar una u otra en la implementación de . Si, por ejemplo, no tiene ninguna propiedad independiente de la configuración para mostrar para un objeto, puede optar por no mostrar la categoría Propiedades comunes. Mostrar propiedades comunes `ISpecifyPropertyPages` si se implementa desde el objeto de exploración del elemento y propiedades de configuración cuando se implementa `ISpecifyPropertyPages` en el objeto de configuración (el objeto que implementa `IVsCfg`, `IVsProjectCfg`, e interfaces relacionadas).

  Cada categoría que se muestra en una categoría de nivel superior representa una página de propiedades independiente. Las entradas de categoría y subcategoría disponibles en `ISpecifyPropertyPages` `IVsPropertyPage`el cuadro de diálogo se determinan mediante la implementación de y .

  `IDispatch`Los objetos de los elementos del contenedor de `ISpecifyPropertyPages` selección que tienen propiedades que se mostrarán en las páginas de propiedades se implementan para enumerar una lista de ID de clase. Los ID de clase se pasan `ISpecifyPropertyPages` como variables y se usan para crear instancias de las páginas de propiedades. La lista de iDs de `IVsPropertyPage` clase también se pasa para crear la estructura de árbol a la izquierda del cuadro de diálogo. A continuación, las páginas `IDispatch` de propiedades `ISpecifyPropertyPages` devuelven información al objeto que implementa y rellena la información de cada página.

  Las propiedades del objeto de `IDispatch` exploración se recuperan mediante para cada objeto del contenedor de selección.

  Implementar `Help::DisplayTopicFromF1Keyword` en el VSPackage proporciona la funcionalidad para el botón Ayuda.

  Para obtener más `IDispatch` `ISpecifyPropertyPages`información, consulte y en la biblioteca MSDN.

  El segundo tipo de páginas de propiedades que se muestran en los ejemplos hospeda una forma de la cuadrícula de propiedades, como se muestra en la siguiente captura de pantalla.

  ![Páginas de propiedades de VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Cuadro de diálogo Páginas de propiedades con cuadrícula de propiedades

  Las interfaces `IVSMDPropertyGrid` y (declaradas `IVSMDPropertyBrowser` en vsmanaged.h) se utilizan para crear y rellenar la cuadrícula de propiedades dentro de un cuadro de diálogo o ventana.

  La arquitectura de los proyectos ha [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]cambiado considerablemente con respecto a versiones anteriores de . En particular, la noción de qué proyecto está activo ha cambiado. En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], no hay ningún concepto de un proyecto activo. En entornos de desarrollo anteriores, el proyecto activo era el proyecto que compilar e implementar comandos sería de forma predeterminada independientemente del contexto. Ahora, la solución controla y arbita qué comandos de compilación e implementación se aplican a qué proyectos.

  Lo que antes era un proyecto activo ahora se captura de una de tres maneras diferentes:

- El proyecto Startup

   Puede especificar un proyecto o proyectos desde la página de propiedades de la solución que se iniciará cuando el usuario presione F5 o seleccione Ejecutar en el menú Generar. Esto funciona de una manera similar al proyecto activo anterior en el sentido de que su nombre se muestra en el Explorador de soluciones con fuente en negrita.

   Puede recuperar el proyecto de inicio como una `DTE.Solution.SolutionBuild.StartupProjects`propiedad en el modelo de automatización llamando a . En un VSPackage, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> se <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> llama a los métodos o. `IVsSolutionBuildManager`está disponible como `QueryService` un servicio por SID_SVsSolutionBuildManager. Para obtener más información, vea Objeto de configuración de [proyecto](../../extensibility/internals/project-configuration-object.md) y Configuración de la [solución](../../extensibility/internals/solution-configuration.md).

- Configuración de compilación de soluciones activas

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]tiene una configuración de solución activa, `DTE.Solution.SolutionBuild.ActiveConfiguration`disponible en el modelo de automatización mediante la implementación de . Una configuración de solución es una colección que contiene una configuración de proyecto para cada proyecto de la solución (cada proyecto puede tener varias configuraciones, en varias plataformas, con nombres diferentes). Para obtener más información relacionada con las páginas de propiedades de la solución, vea Configuración de la [solución](../../extensibility/internals/solution-configuration.md).

- Proyecto actualmente seleccionado

   Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> el método para recuperar la jerarquía del proyecto y el elemento de proyecto o los elementos seleccionados. Desde DTE, usaría `SelectedItems.SelectedItem.Project` `SelectedItems.SelectedItem.ProjectItem` los métodos y. Hay código de ejemplo en esos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] encabezados en los documentos principales.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Objeto de configuración del proyecto](../../extensibility/internals/project-configuration-object.md)
- [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)
