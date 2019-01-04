---
title: Configuración para la compilación de proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f320a23fa75dccdb4c273bc851832f3b762696d1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910222"
---
# <a name="project-configuration-for-building"></a>Configuración del proyecto para la compilación
La lista de configuraciones de soluciones para una solución determinada se administra mediante el cuadro de diálogo de configuraciones de soluciones.  
  
 Un usuario puede crear configuraciones de solución adicionales, cada uno con su propio nombre único. Cuando el usuario crea una nueva configuración de soluciones, el IDE tiene como valor predeterminado el nombre de configuración correspondiente en los proyectos o depuración si no existe ningún nombre correspondiente. El usuario puede cambiar la selección para satisfacer necesidades específicas, si es necesario. La única excepción a este comportamiento es cuando el proyecto admite una configuración que coincida con el nombre de la nueva configuración de solución. Por ejemplo, suponga que una solución contiene Proyecto1 y Proyecto2. Project1 tiene configuraciones de proyecto MyConfig1, comercial y depuración. Project2 tiene configuraciones de proyecto MyConfig2, comercial y depuración.  
  
 Si el usuario crea una nueva configuración de solución denominada MyConfig2, Proyecto1 enlaza su configuración de depuración para la configuración de soluciones de forma predeterminada. Project2 también enlaza su configuración MyConfig2 a la configuración de soluciones de forma predeterminada.  
  
> [!NOTE]
>  Enlace distingue mayúsculas de minúsculas.  
  
 Cuando el usuario selecciona el **selección múltiple** elemento en la lista desplegable de configuración, el entorno muestra un cuadro de diálogo que proporciona la lista de configuraciones disponibles.  
  
 ![Varias configuraciones](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs")  
Varias configuraciones  
  
 En este cuadro de diálogo, el usuario puede seleccionar una o varias configuraciones. Una vez seleccionado, los valores de propiedad que se muestra en el cuadro de diálogo páginas de propiedades reflejan la intersección de los valores de las configuraciones seleccionadas.  
  
 Consulte [configuración de la solución](../../extensibility/internals/solution-configuration.md) para obtener información relativa a la adición y cambiar el nombre de las configuraciones de soluciones y proyectos.  
  
 Dependencias del proyecto y el orden de compilación sean independientes de la configuración de solución: es decir, solo puede establecer árbol una dependencia para todos los proyectos de la solución. Con el botón secundario en la solución o proyecto y seleccionando el **dependencias del proyecto** o **orden de compilación de proyecto** opción abre el **dependencias del proyecto** cuadro de diálogo. También se puede abrir desde el **proyecto** menú.  
  
 ![Dependencias del proyecto](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
Dependencias del proyecto  
  
 Dependencias del proyecto determinan el orden en que se generan los proyectos. Utilice la pestaña de orden de compilación en el cuadro de diálogo para ver el orden exacto en el que compilar proyectos dentro de una solución y use la ficha dependencias para modificar el orden de compilación.  
  
> [!NOTE]
>  En la lista de los proyectos que tienen sus casillas activadas pero atenuadas se han agregado por el entorno debido a dependencias explícitas, especificado por el <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> e interfaces, no se puede cambiar. Por ejemplo, agregando una referencia de proyecto desde un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] proyecto a otro proyecto agrega automáticamente una dependencia de compilación que solo se puede quitar mediante la eliminación de la referencia. No se puede seleccionar proyectos cuyas casillas de verificación están desactivadas y aparecen atenuadas porque si lo hace, crearía un bucle de dependencia (por ejemplo, sería depende Project2 Project1 y Project2 sería depende Project1), que se detendría la generación.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] los procesos de compilación incluyen las compilación típico y operaciones de vínculo que se invocan con un solo comando de compilación. También se admiten otros dos procesos de compilación: una operación de limpieza para eliminar todos los elementos de salida de una compilación anterior y una comprobación para determinar si ha cambiado un elemento de salida en una configuración actualizada.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> los objetos devuelven correspondiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (devuelto desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>) para administrar sus procesos de compilación. Para informar del estado de una operación de compilación mientras se lleva a cabo, las configuraciones de realizan llamadas a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, una interfaz implementada por el entorno y cualquier otro objeto que está interesado en eventos de estado de compilación.  
  
 Una vez compilada, opciones de configuración pueden utilizarse para determinar si se puede ejecutar bajo el control del depurador. Implementan configuraciones <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> para admitir la depuración.  
  
 Después de implementar las dependencias del proyecto, puede manipular mediante programación las dependencias a través del modelo de automatización. Se llama a <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> en el modelo de automatización. No hay ninguna interfaz de nivel de API de VSIP disponible que permiten la manipulación directa de las configuraciones de administrador de compilación de soluciones y sus propiedades.  
  
 Además, puede proporcionar una cuadrícula en la ventana de las dependencias del proyecto. Para obtener más información, consulte [Mostrar cuadrícula de propiedades](../../extensibility/internals/properties-display-grid.md).  
  
## <a name="see-also"></a>Vea también  
 [Administración de las opciones de configuración](../../extensibility/internals/managing-configuration-options.md)   
 [Configuración del proyecto para administrar la implementación](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)