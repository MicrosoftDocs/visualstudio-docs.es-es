---
title: Información general sobre las opciones de configuración | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e502f78698d830c916b09968e8fa2cfbcd74fbf7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915781"
---
# <a name="configuration-options-overview"></a>Información general de opciones de configuración
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Los proyectos de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] puede admitir varias configuraciones que pueden compilarse depurado, ejecución o implementadas. Una configuración es un tipo de compilación que se describe con un conjunto de propiedades, normalmente modificadores de compilador y las ubicaciones de archivo. De forma predeterminada, las nuevas soluciones contienen dos configuraciones, Debug y Release. Estas configuraciones se pueden aplicar utilizando su configuración predeterminada, o puede modificar para cumplir sus requisitos específicos de la solución o proyecto. Algunos paquetes pueden compilarse de dos maneras: como un editor de ActiveX o como un componente en contexto. Los proyectos no es necesario admitir varias configuraciones, sin embargo. Si hay solo una configuración, dicha configuración se asigna a todas las configuraciones de soluciones.  
  
 Las configuraciones que suelen constan de dos partes: el nombre de configuración (por ejemplo Debug o Release) y la configuración de plataforma. Nombre de la configuración de la plataforma identifica el entorno que establecen los destinos de configuración, como una API o la plataforma del sistema operativo. Los usuarios de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] no se puede crear una plataforma; debe elegir entre las selecciones un proyecto de VSPackage permite. Cuando un instalaciones de usuario un VSPackage, la plataforma de entrega creado durante el desarrollo del paquete pueden exponer cualquier nombre de la plataforma deseada según los criterios establecidos por el creador del paquete. El usuario puede seleccionar a continuación, en la lista de plataformas disponible a través de VSPackage cuando se crean instancias de las páginas de propiedades.  
  
 Nombres de plataforma son opcionales, ya que no todos los proyectos admiten el concepto de plataformas. Cuando una configuración no tiene un nombre de la plataforma, se muestra la cadena "N/A" en la interfaz de usuario.  
  
 Cada solución tiene su propio conjunto de configuraciones, solo uno de los cuales puede estar activa simultáneamente. Una configuración de soluciones es un conjunto de no más de una configuración de cada proyecto. Es "no más de" es debido a la opción para excluir un proyecto de una configuración de soluciones. Los usuarios pueden crear sus propias configuraciones de solución personalizada.  
  
 En la tabla siguiente se muestra la configuración de las configuraciones típicas para un proyecto. Las filas se etiquetan con nombres de configuración y las columnas con nombres de plataforma.  
  
|Nombre de configuración|Plataforma: Win32|Plataforma: Win64|  
|------------------------|----------------------|----------------------|  
|Depuración|\<Configuración de Win32 de depuración >|\<Depurar opciones Win64 >|  
|Versión|\<Configuración de Win32 de versión >|\<Configuración de Win64 versión >|  
|MyConfig|N/D|\<Configuración de MyConfig Win64 >|  
  
> [!NOTE]
>  No se puede crear una configuración de soluciones "MyConfig" que excluye una plataforma "Win32", a menos que el proyecto tiene como destino no es compatible con Win32.  
  
 Cambiar la configuración activa para una solución, selecciona el conjunto de configuraciones de proyecto que se generan, ejecutar, depurar o implementar en esa solución. Por ejemplo, si cambia la configuración de soluciones activas de versión a depuración, todos los proyectos de esa solución se crean automáticamente con la configuración de los proyectos indicado en la configuración de depuración de la solución. Las configuraciones de los proyectos suelen ser también la depuración con nombre, a menos que el usuario ha realizado cambios manuales en el Administrador de configuración del entorno.  
  
 Las propiedades de configuración de solución almacenadas para cada proyecto incluyen el nombre del proyecto, nombre de la configuración de proyecto, las marcas para indicar si o no para compilar o implementar y nombre de la plataforma. Para obtener más información, consulte [configuración de la solución](../../extensibility/internals/solution-configuration.md).  
  
 El usuario puede ver y establecer los parámetros de configuración de soluciones, seleccione la solución en la jerarquía (Explorador de soluciones) y abrir las páginas de propiedades. De forma similar, puede ver y establecer los parámetros de configuración de proyecto, seleccione un proyecto en el Explorador de soluciones y abrir las páginas de propiedades para ese proyecto.  
  
 El usuario también puede crear un proyecto con valores de configuración de la versión y el resto con los valores de configuración de depuración si es necesario. Para obtener más información, consulte [configuración del proyecto para compilar](../../extensibility/internals/project-configuration-for-building.md).  
  
 El diagrama siguiente muestra cómo se implementan las interfaces que admiten las configuraciones de solución y proyecto:  
  
 ![Gráfico de Interfaces de configuración](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
Interfaces de configuración  
  
 Algunas notas relacionadas con el diagrama anterior:  
  
- `IDispatch` está marcado como opcionales en el objeto de configuración. En concreto, es opcional para que las interfaces de configuración en el objeto de exploración.  
  
- `IVsDebuggableProjectCfg` está marcado como opcional en el objeto de configuración, pero es necesario para la compatibilidad con la depuración.  
  
- `IVsProjectCfg2` está marcado como opcional en el objeto de configuración, pero es necesario para la salida de soporte técnico de agrupación.  
  
- La `Config Provider` objeto está marcado como un objeto opcional, pero la opción es dónde implementarla. Puede implementar el objeto en el objeto de proyecto o en un objeto independiente.  
  
- `IVsCfgProvider2` es necesario para la compatibilidad con la plataforma y la edición de la configuración. `IVsCfgProvider` es suficiente si no implementa esa funcionalidad.  
  
- Algunos de estos objetos que se muestra en el diagrama como objetos independientes se pueden combinar en la misma clase cuando sea conveniente según los requisitos de diseño específico. En otros temas de esta sección, sin embargo, los objetos e interfaces asociadas con esos objetos se tratarán según el escenario presentado en el diagrama.  
  
- Algunos objetos se implementan por separado. Por ejemplo, proyecto y solución compilación se producen en subprocesos independientes y el objeto para administrar la vida de la compilación por separado desde el objeto que describe la configuración de la compilación.  
  
  Para obtener más información sobre las interfaces de objeto de configuración y las interfaces del objeto de proveedor de configuración en el diagrama anterior, consulte [objeto de configuración de proyecto](../../extensibility/internals/project-configuration-object.md). Además, [configuración del proyecto para compilar](../../extensibility/internals/project-configuration-for-building.md) proporciona más información sobre las interfaces de generador de configuración y el objeto de dependencia de compilación, y [configuración del proyecto para administrar la implementación](../../extensibility/internals/project-configuration-for-managing-deployment.md) aún más describe las interfaces conectadas al implementador de la configuración y los objetos de dependencia de implementación. Por último, [configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md) describe las interfaces de objeto de salida y de grupo de resultados y el uso de páginas de propiedades para ver y establecer las propiedades dependientes de la configuración.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)   
 [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)

