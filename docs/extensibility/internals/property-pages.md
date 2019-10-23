---
title: Páginas de propiedades | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51487b35686da9676f201a157ddb8e47afb75ce8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725057"
---
# <a name="property-pages"></a>Páginas de propiedades
Los usuarios pueden ver y cambiar las propiedades dependientes e independientes de la configuración del proyecto mediante páginas de propiedades. Un botón **páginas de propiedades** está habilitado en la ventana **propiedades** o en explorador de soluciones barra de herramientas para los objetos que proporcionan una vista de página de propiedades del objeto seleccionado. El entorno crea las páginas de propiedades y están disponibles para las soluciones y los proyectos. Sin embargo, también pueden estar disponibles para los elementos de proyecto que hacen uso de las propiedades dependientes de la configuración. Esta capacidad se puede usar cuando los archivos de un proyecto requieren una configuración de conmutador de compilador diferente para compilar correctamente.

## <a name="using-property-pages"></a>Usar páginas de propiedades
 Si ya se muestra una página de propiedades y la selección cambia (por ejemplo, de una solución a un proyecto), la información que se muestra en las páginas cambia para mostrar las propiedades de la nueva selección. Si no hay ninguna propiedad en el objeto que admita páginas de propiedades, la página de propiedades está vacía.

 Si se seleccionan varios objetos, la página de propiedades muestra la intersección de las propiedades de todos los elementos seleccionados. Si el elemento seleccionado no contiene propiedades dependientes de la configuración y se hace clic en el botón **páginas de propiedades** de la barra de herramientas explorador de soluciones, se centra en los cambios en el ventana Propiedades. Para obtener más información sobre el ventana Propiedades y la selección, vea [extender propiedades](../../extensibility/internals/extending-properties.md).

 Si se muestran las propiedades de varios objetos y se cambia un valor en una página de propiedades, todos los valores de los objetos se establecen en el nuevo valor aunque se hayan distinto inicialmente y la página estuviera en blanco cuando se mostraban las propiedades de un objeto individual.

 Hay dos tipos generales de cuadros de diálogo de **páginas de ProjectProperty** disponibles en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. En el primero, para los proyectos de Visual Basic, por ejemplo, las páginas de propiedades se muestran con un formato de campo, tal como se muestra en la captura de pantalla siguiente. En el segundo, que se muestra más adelante en esta sección, la página de propiedades hospeda una cuadrícula de propiedades similar a la que se encuentra en la ventana Propiedades.

 ![Visual Basic páginas de propiedades](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Cuadro de diálogo páginas de propiedades del proyecto con formato de campo y estructura de árbol

 La estructura de árbol del cuadro de diálogo páginas de propiedades no se genera mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. El entorno, basado en el nombre de nivel que le ha pasado el <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> y las interfaces <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>, lo compila.

 Solo hay dos categorías de nivel superior disponibles en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] páginas de propiedades:

- Propiedades comunes, que muestra información independiente de la configuración para el objeto o los objetos seleccionados. Como resultado, cuando se selecciona una de las subcategorías de propiedades comunes, las opciones de configuración, plataforma y Configuration Manager en la parte superior del cuadro de diálogo no están disponibles.

- Propiedades de configuración, que contienen información dependiente de la configuración relacionada con la depuración, la optimización y los parámetros de compilación de la solución o el proyecto.

  No puede crear categorías de nivel superior adicionales, pero puede elegir no mostrar una u otra en la implementación de `IVsPropertyPage`. Por ejemplo, si no tiene propiedades independientes de la configuración para mostrar para un objeto, puede elegir no mostrar la categoría propiedades comunes. Las propiedades comunes se muestran si se implementa `ISpecifyPropertyPages` desde el objeto de exploración del elemento y las propiedades de configuración al implementar `ISpecifyPropertyPages` en el objeto de configuración (el objeto que implementa `IVsCfg`, `IVsProjectCfg` e interfaces relacionadas).

  Cada categoría mostrada en una categoría de nivel superior representa una página de propiedades independiente. Las entradas de categoría y subcategoría disponibles en el cuadro de diálogo se determinan mediante la implementación de `ISpecifyPropertyPages` y `IVsPropertyPage`.

  `IDispatch` objetos para los elementos del contenedor de selección que tienen propiedades que se van a mostrar en las páginas de propiedades implementa `ISpecifyPropertyPages` para enumerar una lista de identificadores de clase. Los identificadores de clase se pasan como variables a `ISpecifyPropertyPages` y se usan para crear instancias de las páginas de propiedades. La lista de identificadores de clase también se pasa a `IVsPropertyPage` para crear la estructura de árbol a la izquierda del cuadro de diálogo. A continuación, las páginas de propiedades devuelven información al objeto `IDispatch` que implementa `ISpecifyPropertyPages` y rellena la información de cada página.

  Las propiedades del objeto Browse se recuperan mediante `IDispatch` por cada objeto del contenedor de selección.

  La implementación de `Help::DisplayTopicFromF1Keyword` en el VSPackage proporciona la funcionalidad para el botón ayuda.

  Para obtener más información, vea `IDispatch` y `ISpecifyPropertyPages`in MSDN Library.

  El segundo tipo de páginas de propiedades que se muestran en los ejemplos hospeda un formulario de la cuadrícula propiedades, tal como se muestra en la captura de pantalla siguiente.

  ![Páginas de propiedades VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Cuadro de diálogo páginas de propiedades con cuadrícula de propiedades

  Las interfaces `IVSMDPropertyBrowser` y `IVSMDPropertyGrid` (declaradas en vsmanaged. h) se usan para crear y rellenar la cuadrícula de propiedades dentro de un cuadro de diálogo o ventana.

  La arquitectura de los proyectos ha cambiado considerablemente respecto a las versiones anteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. En concreto, la noción de qué proyecto está activo ha cambiado. En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], no hay ningún concepto de proyecto activo. En los entornos de desarrollo anteriores, el proyecto activo era el proyecto en el que los comandos de compilación e implementación se utilizaban de forma predeterminada, independientemente del contexto. Ahora, la solución controla y arbitra los comandos de compilación e implementación que se aplican a los proyectos.

  Lo que antes era un proyecto activo ahora se captura de tres maneras diferentes:

- Proyecto de inicio

   Puede especificar un proyecto o proyectos de la página de propiedades de la solución que se iniciará cuando el usuario presione F5 o seleccione Ejecutar en el menú compilar. Esto funciona de forma similar al proyecto activo anterior en el sentido de que su nombre se muestra en Explorador de soluciones con una fuente en negrita.

   Puede recuperar el proyecto de inicio como una propiedad en el modelo de automatización llamando a `DTE.Solution.SolutionBuild.StartupProjects`. En un VSPackage, se llama a los métodos <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A>. `IVsSolutionBuildManager` está disponible como servicio `QueryService` en SID_SVsSolutionBuildManager. Para obtener más información, consulte [objeto de configuración de proyecto](../../extensibility/internals/project-configuration-object.md) y configuración de [soluciones](../../extensibility/internals/solution-configuration.md).

- Configuración de compilación de soluciones activas

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tiene una configuración de soluciones activa, disponible en el modelo de automatización implementando `DTE.Solution.SolutionBuild.ActiveConfiguration`. Una configuración de soluciones es una colección que contiene una configuración de proyecto para cada proyecto de la solución (cada proyecto puede tener varias configuraciones, en varias plataformas, con nombres distintos). Para obtener más información sobre las páginas de propiedades de la solución, vea [configuración de soluciones](../../extensibility/internals/solution-configuration.md).

- Proyecto seleccionado actualmente

   Implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> para recuperar la jerarquía del proyecto y los elementos seleccionados del proyecto. En DTE, usaría los métodos `SelectedItems.SelectedItem.Project` y `SelectedItems.SelectedItem.ProjectItem`. Hay código de ejemplo bajo esos encabezados en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] documentos principales.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Objeto de configuración del proyecto](../../extensibility/internals/project-configuration-object.md)
- [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)