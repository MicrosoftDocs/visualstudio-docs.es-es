---
title: "Información general sobre las opciones de configuración | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0edfe84e26a9331b8c40ec24b00387768bdbba82
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-options-overview"></a>Información general de opciones de configuración
Los proyectos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] puede admitir varias configuraciones que se pueden compilar depurado, ejecución o implementado. Una configuración es un tipo de compilación se describe con un conjunto de propiedades, normalmente modificadores del compilador y ubicaciones de archivos. De forma predeterminada, las nuevas soluciones contienen dos configuraciones, Debug y Release. Estas configuraciones pueden aplicarse utilizando su configuración predeterminada, o modificar para cumplir sus requisitos específicos de la solución o proyecto. Algunos paquetes pueden crearse de dos maneras: como un editor de ActiveX o como un componente en contexto. Proyectos no es necesario admitir varias configuraciones, sin embargo. Si hay una sola configuración, dicha configuración se asigna a todas las configuraciones de soluciones.  
  
 Las configuraciones que suelen estar formadas por dos partes: el nombre de configuración (como depuración o lanzamiento) y la configuración de plataforma. Nombre de la configuración de la plataforma identifica el entorno que establece el destino de la configuración, por ejemplo, una API o la plataforma del sistema operativo. Los usuarios de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no se puede crear una plataforma; deben elegir desde las selecciones de un proyecto de VSPackage permite. Cuando un usuario la instalación de un paquete VSPackage, la plataforma de entrega que se crea durante el desarrollo del paquete puede surgir cualquier nombre de la plataforma deseado según los criterios establecidos por el creador del paquete. El usuario puede seleccionar a continuación, en la lista de plataformas ponerse a disposición a través de VSPackage cuando se crean instancias de las páginas de propiedades.  
  
 Nombres de plataforma son opcionales, ya que no todos los proyectos admiten el concepto de plataformas. Cuando una configuración no tiene un nombre de la plataforma, se muestra la cadena "N/A" en la interfaz de usuario.  
  
 Cada solución tiene su propio conjunto de configuraciones, solo uno de los cuales puede estar activa simultáneamente. Una configuración de soluciones es un conjunto de no más de una configuración de cada proyecto. El es "no supere" es debido a la opción para excluir un proyecto de una configuración de soluciones. Los usuarios pueden crear sus propias configuraciones de solución personalizada.  
  
 En la tabla siguiente se muestra el programa de instalación de configuraciones típicas para un proyecto. Las filas se etiquetan con nombres de configuración y las columnas con nombres de plataforma.  
  
|Nombre de configuración|Plataforma: Win32|Plataforma: Win64|  
|------------------------|----------------------|----------------------|  
|Depuración|\<Depurar la configuración de Win32 >|\<Depurar Win64 configuración >|  
|Versión|\<Opciones de configuración de Win32 >|\<Opciones de configuración de Win64 >|  
|MyConfig|N/D|\<Configuración de MyConfig Win64 >|  
  
> [!NOTE]
>  No se puede crear una configuración de solución de "MyConfig" que excluye una plataforma "Win32", a menos que el proyecto tiene como destino no es compatible con Win32.  
  
 Cambiar la configuración activa para una solución, selecciona el conjunto de configuraciones de proyecto que se generan, ejecutar, depurar o implementar en esa solución. Por ejemplo, si cambia la configuración de soluciones activas de versión para la depuración, se generan automáticamente a todos los proyectos de esa solución con la configuración de los proyectos que se indica en la configuración de depuración de la solución. Las configuraciones de los proyectos suelen ser también depuración con nombre a menos que el usuario ha realizado cambios manuales en el Administrador de configuración del entorno.  
  
 Las propiedades de configuración de solución almacenadas para cada proyecto incluyen el nombre del proyecto, el nombre de la configuración de proyecto, el marcas para indicar si o no para compilar o implementar y el nombre de la plataforma. Para obtener más información, consulte [configuración de la solución](../../extensibility/internals/solution-configuration.md).  
  
 El usuario puede ver y establecer los parámetros de configuración de soluciones, seleccione la solución en la jerarquía (Explorador de soluciones) y abrir las páginas de propiedades. De forma similar, puede ver y establecer parámetros de configuración de proyecto, seleccione un proyecto en el Explorador de soluciones y abrir las páginas de propiedades de ese proyecto.  
  
 El usuario también puede compilar un proyecto con opciones de configuración de la versión y el resto de configuración Debug si es necesario. Para obtener más información, consulte [configuración del proyecto para compilar](../../extensibility/internals/project-configuration-for-building.md).  
  
 El diagrama siguiente muestra cómo se implementan las interfaces que admiten las configuraciones de solución y proyecto:  
  
 ![Gráfico de Interfaces de configuración](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
Interfaces de configuración  
  
 Unas anotaciones relacionadas con el diagrama anterior:  
  
-   `IDispatch`se marcan como opcionales en el objeto de configuración. En concreto, es opcional para que las interfaces de configuración en el objeto de búsqueda.  
  
-   `IVsDebuggableProjectCfg`se marca el objeto de configuración es opcional, pero es necesario para la compatibilidad con la depuración.  
  
-   `IVsProjectCfg2`está marcado opcional en el objeto de configuración, pero es necesario para la salida de soporte técnico de agrupación.  
  
-   La `Config Provider` objeto se marca como un objeto opcional, pero la opción es donde puede implementarla. Puede implementar el objeto en el objeto de proyecto o en un objeto independiente.  
  
-   `IVsCfgProvider2`es necesario para la compatibilidad con la plataforma y la edición de la configuración. `IVsCfgProvider`es suficiente si no implementa esa funcionalidad.  
  
-   Algunos de estos objetos que se muestra en el diagrama como objetos independientes se pueden combinar en la misma clase en la práctica según sus requisitos de diseño específicas. En otros temas de esta sección, sin embargo, los objetos e interfaces asociadas con esos objetos se analizarán según el escenario presentado en el diagrama.  
  
-   Algunos objetos que se implementan por separado. Por ejemplo, proyecto y solución compilación se producen en subprocesos independientes y el objeto que se va a administrar la vida de la compilación por separado desde el objeto que describe la configuración de la compilación.  
  
 Para obtener más información sobre las interfaces del objeto de configuración e interfaces de objeto de proveedor de configuración en el diagrama anterior, vea [objeto de configuración de proyecto](../../extensibility/internals/project-configuration-object.md). Además, [configuración del proyecto para compilar](../../extensibility/internals/project-configuration-for-building.md) proporciona más información sobre las interfaces de generador de configuración y el objeto de dependencia de compilación, y [configuración de proyecto de implementación de administración de](../../extensibility/internals/project-configuration-for-managing-deployment.md) Además se describen las interfaces conectadas al implementador de la configuración y los objetos de dependencia de implementación. Por último, [configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md) describe las interfaces de grupo de resultados y el objeto de salida y el uso de páginas de propiedades para ver y establecer las propiedades dependientes de la configuración.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Configuración del proyecto para una compilación](../../extensibility/internals/project-configuration-for-building.md)   
 [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)