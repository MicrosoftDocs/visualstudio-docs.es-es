---
title: Información general de las opciones de configuración | Microsoft Docs
description: Obtenga información sobre las opciones de las configuraciones de proyecto en Visual Studio. Una configuración es un tipo de compilación que se describe con un conjunto de propiedades y ubicaciones de archivos con nombre.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ad30e3f7b91e8a76715f66d9f6701597f3830bd6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057135"
---
# <a name="configuration-options-overview"></a>Información general de las opciones de configuración
Los proyectos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pueden admitir varias configuraciones que se pueden compilar, depurar, ejecutar o implementar. Una configuración es un tipo de compilación que se describe con un conjunto de propiedades con nombre, normalmente modificadores de compilador y ubicaciones de archivos. De forma predeterminada, las nuevas soluciones contienen dos configuraciones, *Debug* y *Release*. Estas configuraciones se pueden aplicar con su configuración predeterminada o modificarse para satisfacer los requisitos específicos de la solución o el proyecto. Algunos paquetes se pueden crear de dos maneras: como un editor ActiveX o como un componente en contexto. No obstante, no es necesario que los proyectos admitan varias configuraciones. Si solo hay una configuración disponible, esa configuración se asigna a todas las configuraciones de soluciones.

 Las configuraciones suelen constar de dos partes: el nombre de la configuración (por ejemplo, *Debug* o *Release*) y la configuración de la plataforma. El nombre de la plataforma de una configuración identifica el entorno de destino de la configuración, como un conjunto de API o una plataforma de sistema operativo. Los usuarios de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no pueden crear una plataforma; deben elegir entre las selecciones que permite un VSPackage del proyecto. Cuando un usuario instala un VSPackage, la plataforma de entrega que se crea durante el desarrollo del paquete puede mostrar cualquier nombre de plataforma deseado en función de los criterios establecidos por el creador del paquete. Después, el usuario puede seleccionar en la lista de plataformas disponibles a través del VSPackage cuando se crean instancias de las páginas de propiedades.

 Los nombres de plataforma son opcionales, ya que no todos los proyectos admiten el concepto de plataformas. Cuando una configuración no tiene un nombre de plataforma, se muestra la cadena **N/a** en la interfaz de usuario.

 Cada solución tiene su propio conjunto de configuraciones, solo una de las cuales puede estar activa a la vez. Una configuración de soluciones es un conjunto de no más de una configuración de cada proyecto. La estipulación "no más que" se debe a la opción de excluir un proyecto de una configuración de solución. Los usuarios pueden crear sus propias configuraciones de soluciones personalizadas.

 En la tabla siguiente se muestra la configuración de configuraciones típicas para un proyecto de. Las filas se etiquetan con los nombres de configuración y las columnas con nombres de plataforma.

|Nombre de la configuración|Plataforma: Win32|Plataforma: Win64|
|------------------------|----------------------|----------------------|
|*Depurar*|\<Debug Win32 settings>|\<Debug Win64 settings>|
|*Versión*|\<Release Win32 settings>|\<Release Win64 settings>|
|*MyConfig*|N/D|\<MyConfig Win64 settings>|

> [!NOTE]
> No se puede crear una configuración de solución de mi *config* que excluya una plataforma Win32 a menos que el proyecto al que se destina no sea compatible con Win32.

 Al cambiar la configuración activa de una solución, se selecciona el conjunto de configuraciones de proyecto que se compila, se ejecuta, se depura o se implementa en esa solución. Por ejemplo, si cambia la configuración de soluciones activa de *Release* a *Debug*, todos los proyectos de esa solución se compilan automáticamente con la configuración de los proyectos indicada en la configuración de depuración de la solución. Las configuraciones de los proyectos también se denominan *depurar* , a menos que el usuario haya realizado cambios manuales en el Configuration Manager del entorno.

 Las propiedades de configuración de soluciones almacenadas para cada proyecto incluyen el nombre del proyecto, el nombre de la configuración del proyecto, las marcas para indicar si se debe compilar o implementar, y el nombre de plataforma. Para obtener más información, vea [configuración de soluciones](../../extensibility/internals/solution-configuration.md).

 El usuario puede ver y establecer los parámetros de configuración de soluciones seleccionando la solución en la jerarquía (Explorador de soluciones) y abriendo las páginas de propiedades. Del mismo modo, puede ver y establecer los parámetros de configuración del proyecto seleccionando un proyecto en Explorador de soluciones y abriendo las páginas de propiedades de ese proyecto.

 El usuario también puede compilar un proyecto con la configuración de lanzamiento y todo el resto con valores de configuración de depuración si es necesario. Para obtener más información, vea [configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md).

 En el diagrama siguiente se muestra cómo se implementan las interfaces que admiten las configuraciones de soluciones y proyectos:

 ![Gráfico de interfaces de configuración](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces") Interfaces de configuración

 Algunas notas relacionadas con el diagrama anterior:

- `IDispatch` está marcado como opcional en el objeto de configuración. En concreto, es opcional tener las interfaces de configuración en el objeto de exploración.

- `IVsDebuggableProjectCfg` está marcado como opcional en el objeto de configuración, pero es necesario para la compatibilidad con la depuración.

- `IVsProjectCfg2` está marcado como opcional en el objeto de configuración, pero es necesario para la compatibilidad con la agrupación de salida.

- El objeto de proveedor de configuración se marca como un objeto opcional, pero la opción es donde se implementa. Puede implementar el objeto en el objeto de proyecto o en un objeto independiente.

- `IVsCfgProvider2` se necesita para la compatibilidad de la plataforma y la edición de la configuración. `IVsCfgProvider` es suficiente si no implementa esa funcionalidad.

- Algunos de estos objetos mostrados en el diagrama como objetos independientes se pueden combinar en la misma clase, siempre que sea práctico según sus requisitos de diseño específicos. En otros temas de esta sección, sin embargo, los objetos y las interfaces asociadas a esos objetos se tratarán según el escenario presentado en el diagrama.

- Ciertos objetos se implementan por separado. Por ejemplo, la creación de proyectos y soluciones tiene lugar en subprocesos independientes y el objeto para administrar la compilación reside por separado del objeto que describe la configuración de la compilación.

  Para obtener más información sobre las interfaces del objeto de configuración y las interfaces de objeto del proveedor de configuración del diagrama anterior, vea [objeto de configuración del proyecto](../../extensibility/internals/project-configuration-object.md). Además, la [configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md) proporciona más información sobre el generador de configuración y las interfaces del objeto de dependencia de compilación, y la [configuración de proyecto para administrar la implementación](../../extensibility/internals/project-configuration-for-managing-deployment.md) describe aún más las interfaces conectadas al implementador de configuración y los objetos de dependencia de implementación. Por último, la [configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md) describe las interfaces del grupo de salida y del objeto de salida, y el uso de páginas de propiedades para ver y establecer las propiedades dependientes de la configuración.

## <a name="see-also"></a>Consulte también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)
- [Configuración de la solución](../../extensibility/internals/solution-configuration.md)
