---
title: "Configuraci&#243;n del proyecto para la compilaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proyectos [Visual Studio SDK], configuración de creación"
  - "configuraciones de proyecto, crear"
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Configuraci&#243;n del proyecto para la compilaci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La lista de configuraciones de soluciones de una solución dada se administra mediante el cuadro de diálogo de configuraciones de soluciones.  
  
 Un usuario puede crear configuraciones de soluciones adicionales, cada uno con su propio nombre único. Cuando el usuario crea una nueva configuración de soluciones, el IDE predeterminado es el nombre de configuración correspondiente en los proyectos o depuración si no existe ningún nombre correspondiente. El usuario puede cambiar la selección para cumplir requisitos específicos, si es necesario. La única excepción a este comportamiento es cuando el proyecto es compatible con una configuración que coincida con el nombre de la nueva configuración de soluciones. Por ejemplo, suponga que una solución que contiene Project1 y Project2. Project1 tiene configuraciones de proyecto Debug, comercial y MyConfig1. Project2 tiene configuraciones de proyecto Debug, comercial y MyConfig2.  
  
 Si el usuario crea una nueva configuración de solución denominada MyConfig2, Project1 enlaza su configuración de depuración para la configuración de soluciones predeterminada. Project2 también enlaza su configuración MyConfig2 para la configuración de soluciones predeterminada.  
  
> [!NOTE]
>  Enlace distingue mayúsculas de minúsculas.  
  
 Cuando el usuario selecciona el **selección múltiple** elemento en la lista desplegable de configuración, el entorno muestra un cuadro de diálogo que proporciona la lista de las configuraciones disponibles.  
  
 ![Varias configuraciones](../../extensibility/internals/media/vsmultiplecfgs.png "vsMultipleCfgs")  
Varias configuraciones  
  
 En este cuadro de diálogo, el usuario puede seleccionar una o varias configuraciones. Una vez seleccionado, los valores de propiedad que se muestra en el cuadro de diálogo páginas de propiedades reflejan la intersección de los valores de las configuraciones seleccionadas.  
  
 Consulte [Configuración de soluciones](../../extensibility/internals/solution-configuration.md) para obtener información relativa a agregar y cambiar el nombre de las configuraciones de soluciones y proyectos.  
  
 Dependencias del proyecto y el orden de compilación son independientes de configuración de soluciones: es decir, sólo puede establecer el árbol de una dependencia para todos los proyectos de la solución. Con el botón secundario en la solución o proyecto y seleccionando el **dependencias del proyecto** o **orden de generación del proyecto** opción abre la **dependencias del proyecto** cuadro de diálogo. También se puede abrir desde el **proyecto** menú.  
  
 ![Dependencias del proyecto](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
Dependencias del proyecto  
  
 Dependencias del proyecto determinan el orden en que se generan los proyectos. Utilice la ficha orden de generación en el cuadro de diálogo para ver el orden exacto en el que compilar proyectos en una solución y use la ficha dependencias para modificar el orden de generación.  
  
> [!NOTE]
>  En la lista de los proyectos que tienen sus casillas de verificación activadas pero que aparecen atenuados se ha agregado el entorno debido a dependencias explícitas especificado por el <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> o la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> e interfaces, no se puede cambiar. Por ejemplo, agregando una referencia al proyecto desde un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] proyecto a otro proyecto agrega automáticamente una dependencia de generación que sólo se puede quitar eliminando la referencia. No se puede seleccionar proyectos cuyas casillas de verificación están desactivadas y aparecerán atenuadas porque al hacerlo, se crearía un bucle de dependencia \(por ejemplo, sería dependientes Project2 Project1 y Project2 sería dependientes Project1\), lo que detendría la generación.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] procesos de compilación incluyen las operaciones de vínculo que se invocan con un solo comando de generación y compilación típico. También se admiten otros dos procesos de compilación: una operación de limpieza para eliminar todos los elementos de salida de una compilación anterior y una comprobación de actualización para determinar si un elemento de salida en una configuración ha cambiado.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> los objetos devuelven correspondiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> \(devuelto por <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>\) para administrar los procesos de compilación. Para informar del estado de una operación de compilación mientras se está produciendo, configuraciones de realizan llamadas a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, una interfaz implementada por el entorno y cualquier otro objeto interesados en los eventos de estado de compilación.  
  
 Una vez creado, opciones de configuración se pueden utilizar para determinar si se permite o no se pueden ejecutar bajo el control del depurador. Implementan configuraciones <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> para admitir la depuración.  
  
 Después de implementar las dependencias del proyecto, se pueden manipular mediante programación las dependencias a través del modelo de automatización. Se llama a <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> en el modelo de automatización. No hay ninguna interfaz de nivel de API de VSIP disponible que permiten la manipulación directa de las configuraciones de administrador de compilación de soluciones y sus propiedades.  
  
 Además, puede proporcionar una cuadrícula en la ventana de dependencias de proyecto. Para obtener más información, consulta [Mostrar cuadrícula de propiedades](../../extensibility/internals/properties-display-grid.md).  
  
## Vea también  
 [Administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md)   
 [Configuración del proyecto para administrar la implementación](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)