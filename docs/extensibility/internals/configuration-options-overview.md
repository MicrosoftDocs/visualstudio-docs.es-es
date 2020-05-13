---
title: Descripción general de las opciones de configuración ( Configuration Options Overview ) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d5ac25fcef7b942b791402baf17982c9810e92a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709407"
---
# <a name="configuration-options-overview"></a>Visión general de las opciones de configuración
Los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyectos en pueden admitir varias configuraciones que se pueden compilar, depurar, ejecutar o implementar. Una configuración es un tipo de compilación descrito con un conjunto con nombre de propiedades, normalmente modificadores del compilador y ubicaciones de archivos. De forma predeterminada, las nuevas soluciones contienen dos configuraciones, *Depurar* y *Liberar*. Estas configuraciones se pueden aplicar utilizando su configuración predeterminada o modificarse para satisfacer los requisitos específicos de la solución o del proyecto. Algunos paquetes se pueden crear de dos maneras: como un editor ActiveX o como un componente in situ. Sin embargo, los proyectos no necesitan admitir varias configuraciones. Si solo hay una configuración disponible, esa configuración se asigna a todas las configuraciones de la solución.

 Las configuraciones suelen constar de dos partes: el nombre de configuración (como *Depurar* o *Liberar)* y la configuración de la plataforma. El nombre de plataforma de una configuración identifica el entorno al que se dirige la configuración, como un conjunto de API o una plataforma de sistema operativo. Los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usuarios de no pueden crear una plataforma; deben elegir entre las selecciones que permite un proyecto vsPackage. Cuando un usuario instala un VSPackage, la plataforma de entrega creada durante el desarrollo del paquete puede mostrar cualquier nombre de plataforma deseado en función de los criterios establecidos por el creador del paquete. A continuación, el usuario puede seleccionar de la lista de plataformas disponibles a través de VSPackage cuando se crean instancias de las páginas de propiedades.

 Los nombres de plataforma son opcionales, ya que no todos los proyectos admiten el concepto de plataformas. Cuando una configuración carece de un nombre de plataforma, la cadena **N/A** se muestra en la interfaz de usuario.

 Cada solución tiene su propio conjunto de configuraciones, solo una de las cuales puede estar activa a la vez. Una configuración de solución es un conjunto de no más de una configuración de cada proyecto. La estipulación "no más que" se debe a la opción de excluir un proyecto de una configuración de solución. Los usuarios pueden crear sus propias configuraciones de solución personalizadas.

 En la tabla siguiente se muestra la configuración típica de un proyecto. Las filas se etiquetan con nombres de configuración y las columnas con nombres de plataforma.

|Nombre de la configuración|Plataforma: Win32|Plataforma: Win64|
|------------------------|----------------------|----------------------|
|*Depurar*|\<Configuración de depuración de Win32>|\<Depurar configuración de Win64>|
|*Release*|\<Suelte la configuración de Win32>|\<Suelte la configuración de Win64>|
|*MyConfig*|N/D|\<Configuración de MyConfig Win64>|

> [!NOTE]
> No puede crear una configuración de solución *MyConfig* que excluya una plataforma Win32 a menos que el proyecto al que se dirige no admita Win32.

 Al cambiar la configuración activa de una solución, se selecciona el conjunto de configuraciones de proyecto que se compila, ejecuta, depura o implementa en esa solución. Por ejemplo, si cambia la configuración de la solución activa de *Release* a *Debug*, todos los proyectos dentro de esa solución se compilan automáticamente con la configuración de los proyectos indicada en la configuración de depuración de la solución. Las configuraciones de los proyectos también se denominan *Depurar* a menos que el usuario haya realizado cambios manuales en Configuration Manager del entorno.

 Las propiedades de configuración de la solución almacenadas para cada proyecto incluyen el nombre del proyecto, el nombre de configuración del proyecto, las marcas para indicar si se va a compilar o implementar y el nombre de la plataforma. Para obtener más información, consulte Configuración de la [solución](../../extensibility/internals/solution-configuration.md).

 El usuario puede ver y establecer los parámetros de configuración de la solución seleccionando la solución en la jerarquía (Explorador de soluciones) y abriendo las páginas de propiedades. De forma similar, puede ver y establecer parámetros de configuración del proyecto seleccionando un proyecto en el Explorador de soluciones y abriendo las páginas de propiedades de ese proyecto.

 El usuario también puede crear un proyecto mediante la configuración de versión y todo lo demás con los valores de configuración de depuración si es necesario. Para obtener más información, consulte [Configuración del proyecto para la creación](../../extensibility/internals/project-configuration-for-building.md).

 En el diagrama siguiente se muestra cómo se implementan las interfaces que admiten las configuraciones de soluciones y proyectos:

 ![Gráfico de interfaces de configuración](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces") Interfaces de configuración

 Algunas notas relacionadas con el diagrama anterior:

- `IDispatch`se marca como opcional en el objeto de configuración. Específicamente, es opcional tener las interfaces de configuración en el objeto de exploración.

- `IVsDebuggableProjectCfg`se marca como opcional en el objeto de configuración, pero es necesario para la compatibilidad con la depuración.

- `IVsProjectCfg2`se marca como opcional en el objeto de configuración, pero es necesario para la compatibilidad con la agrupación de salida.

- El objeto Config Provider se marca como un objeto opcional, pero la opción es dónde implementarlo. Puede implementar el objeto en el objeto de proyecto o en un objeto independiente.

- `IVsCfgProvider2`es necesario para el soporte de la plataforma y la edición de la configuración. `IVsCfgProvider`es suficiente si no implementa esa funcionalidad.

- Algunos de estos objetos que se muestran en el diagrama como objetos independientes se pueden combinar en la misma clase cuando sea práctico en función de sus requisitos de diseño específicos. En otros temas de esta sección, sin embargo, los objetos e interfaces asociados con esos objetos se tratarán según el escenario presentado en el diagrama.

- Algunos objetos se implementan por separado. Por ejemplo, la creación de proyectos y soluciones se producen en subprocesos independientes y el objeto para administrar la compilación vive por separado del objeto que describe la configuración de la compilación.

  Para obtener más información sobre las interfaces de objeto de configuración y las interfaces de objeto de proveedor de configuración en el diagrama anterior, vea Objeto de [configuración de proyecto](../../extensibility/internals/project-configuration-object.md). Además, la configuración de [Project para la creación](../../extensibility/internals/project-configuration-for-building.md) proporciona más información sobre el generador de configuración y las interfaces de objetos de dependencia de compilación, y la configuración del proyecto para administrar la [implementación](../../extensibility/internals/project-configuration-for-managing-deployment.md) describe más detalladamente las interfaces asociadas al implementador de configuración y a los objetos de dependencia de implementación. Por último, Configuración del [proyecto para](../../extensibility/internals/project-configuration-for-output.md) la salida describe el grupo de salida y las interfaces de objeto de salida, y el uso de páginas de propiedades para ver y establecer propiedades dependientes de la configuración.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [Configuración del proyecto para la construcción](../../extensibility/internals/project-configuration-for-building.md)
- [Configuración de la solución](../../extensibility/internals/solution-configuration.md)
