---
title: Actualizar proyectos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea5c29819d0035e45f97122fd108ea1f51d60806
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057539"
---
# <a name="upgrading-projects"></a>Actualización de proyectos

Los cambios en el modelo de proyecto desde una versión de Visual Studio a la siguiente pueden requerir que los proyectos y soluciones se puede actualizar para que pueda ejecutar en la versión más reciente. El [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] proporciona interfaces que pueden usarse para implementar la compatibilidad con la actualización en sus propios proyectos.

## <a name="upgrade-strategies"></a>Estrategias de actualización

Para admitir una actualización, la implementación de sistema de proyecto debe definir e implementar una estrategia de actualización. Para determinar la estrategia, puede elegir admitir la copia de seguridad paralelo (SxS), copia de seguridad o ambos.

-   Copia de seguridad de SxS significa que un proyecto de sólo copia los archivos que se deben actualizar en su lugar, agrega un sufijo de nombre de archivo adecuado, por ejemplo, ".old".

-   Copia de seguridad significa que un proyecto copia todos los elementos de proyecto en una ubicación de copia de seguridad proporcionada por el usuario. A continuación, se actualizan los archivos correspondientes en la ubicación del proyecto original.

## <a name="how-upgrade-works"></a>Cómo funcionan las actualizaciones

Cuando se abre una solución creada en una versión anterior de Visual Studio en una versión más reciente, el IDE comprueba el archivo de solución para determinar si debe actualizarse. Si la actualización es necesaria, el **Asistente para actualización** se inicia automáticamente para guiar al usuario a través del proceso de actualización.

Cuando una solución necesita actualizarse, consulta cada generador de proyectos para su estrategia de actualización. La estrategia determina si el generador de proyectos admite la copia de seguridad de copia o SxS. La información se envía a la **Asistente para actualización**, que recopila la información necesaria para la copia de seguridad y presenta las opciones aplicables al usuario.

### <a name="multi-project-solutions"></a>Soluciones de varios proyectos

Si una solución contiene varios proyectos y las estrategias de actualización son diferentes, como cuando un proyecto de C++ que solo es compatible con copia de seguridad de SxS y un proyecto Web que solo admiten la copia de seguridad, los generadores de proyecto deben negociar la estrategia de actualización.

Cada generador de proyectos para consultas de la solución <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. A continuación, llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> para ver si es necesario actualizar archivos del proyecto global y para determinar las estrategias de actualización compatibles. El **Asistente para actualización** , a continuación, se invoca.

Después de que el usuario completa el asistente, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> se llama en cada generador de proyectos para realizar la actualización real. Para facilitar la copia de seguridad, proporcionan métodos IVsProjectUpgradeViaFactory el <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> servicio para registrar los detalles del proceso de actualización. Este servicio no se puede almacenar en caché.

Después de actualizar todos los archivos pertinentes de globales, puede elegir cada generador de proyectos crear instancias de un proyecto. La implementación del proyecto debe admitir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> , a continuación, se llama el método para actualizar todos los elementos de proyecto correspondiente.

> [!NOTE]
> El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método no proporciona el servicio SVsUpgradeLogger. Este servicio se puede obtener mediante una llamada a <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.

## <a name="best-practices"></a>Procedimientos recomendados

Use el <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> servicio para comprobar si puede editar un archivo antes de editarlo y guardarlo antes de guardarlo. Esto le ayudará a la copia de seguridad y actualización implementaciones controlan los archivos de proyecto bajo control de código fuente, los archivos con permisos insuficientes y así sucesivamente.

Use el <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> durante todas las fases de copia de seguridad de servicio y actualizar para proporcionar información sobre el éxito o error del proceso de actualización.

Para obtener más información acerca de la copia de seguridad y actualización de proyectos, vea los comentarios de IVsProjectUpgrade en vsshell2.idl.

## <a name="upgrading-custom-projects"></a> Actualizar proyectos personalizados

Si cambia la información guardada en el archivo del proyecto entre diferentes versiones de Visual Studio de su producto, deberá admitir la actualización del archivo del proyecto de la versión anterior a la nueva. Para admitir la actualización que le permite participar en el **Asistente para conversión de Visual Studio**, implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaz. Esta interfaz contiene el único mecanismo disponible para la actualización de la copia. La actualización del proyecto se produce como parte de la apertura de la solución. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaz se implementa mediante el generador de proyectos, o debe ser al menos puede obtenerse desde el generador de proyectos.

El mecanismo anterior que usa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfaz se sigue admitiendo, pero conceptualmente actualiza el sistema del proyecto como parte del proyecto abierto. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfaz, por tanto, se llama mediante la Visual Studio entorno, aunque el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaz se llama o se implementa. Este enfoque permite usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> para implementar la copia y solo proyectar partes de la actualización y delegar el resto del trabajo que se realiza en contexto (posiblemente en la nueva ubicación), el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfaz.

Para una implementación de ejemplo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, consulte [muestras de VSSDK](http://aka.ms/vs2015sdksamples).

Con las actualizaciones del proyecto, se producen los escenarios siguientes:

-   Si el archivo tiene un formato más reciente de los que puede admitir el proyecto, debe devolver un error en que se indique esto. Esto supone que la versión anterior del producto incluye código para comprobar la versión.

-   Si el <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> indicador se especifica en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método, la actualización se va a implementarse como una actualización en contexto antes de la apertura del proyecto.

-   Si el <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> indicador se especifica en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método, la actualización se implementa como una actualización de la copia.

-   Si el <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> indicador se especifica en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> llamar, a continuación, el usuario ha solicitado por el entorno para actualizar el archivo de proyecto como una actualización en contexto, una vez que se abre el proyecto. Por ejemplo, el entorno pide al usuario que realice la actualización cuando este abra una versión anterior de la solución.

-   Si el <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> marca no se especifica en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> llamar, a continuación, debe pedir al usuario que actualice el archivo de proyecto.

     A continuación, se muestra un ejemplo del mensaje de solicitud de actualización:

     "El proyecto '%1' se creó con una versión anterior de Visual Studio. Si lo abre con esta versión de Visual Studio, es posible que no pueda abrirlo con versiones anteriores de Visual Studio. ¿Quiere continuar y abrir este proyecto?"

### <a name="to-implement-ivsprojectupgradeviafactory"></a>Para implementar IVsProjectUpgradeViaFactory

1.  Implemente el método de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaz, específicamente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método en su implementación del generador de proyecto, o realice implementaciones que se puede llamar desde su implementación del generador de proyecto.

2.  Si desea realizar una actualización en contexto como parte de la solución abrir, proporcione la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> como el `VSPUVF_FLAGS` parámetro en su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementación.

3.  Si desea realizar una actualización en contexto como parte de la solución abrir, proporcione la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> como el `VSPUVF_FLAGS` parámetro en su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementación.

4.  Los pasos 2 y 3, con pasos de actualización del archivo real <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, se puede implementar como se describe en la "implementación `IVsProjectUpgade`" sección, o bien puede delegar la actualización del archivo real a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

5.  Utilice los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> para después de la actualización relacionada con los mensajes para el usuario mediante el Asistente para migración de Visual Studio.

6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> interfaz se usa para implementar cualquier tipo de actualización de archivo que se debe ejecutar como parte de la actualización del proyecto. Esta interfaz no se llama desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, sino que se proporciona como un mecanismo para actualizar los archivos que forman parte del sistema del proyecto, pero el sistema del proyecto principal no puede tener en cuenta directamente. Por ejemplo, esta situación podría producirse si el equipo de desarrollo que administra el resto del sistema del proyecto no administra las propiedades y los archivos relacionados con el compilador.

### <a name="ivsprojectupgrade-implementation"></a>Implementación de IVsProjectUpgrade

Si implementa el sistema del proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> únicamente, no puede participar en el **Asistente para conversión de Visual Studio**. Sin embargo, incluso si decide implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaz, aún puede delegar la actualización del archivo a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementación.

#### <a name="to-implement-ivsprojectupgrade"></a>Para implementar IVsProjectUpgrade

1.  Cuando un usuario intenta abrir un proyecto, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> método es llamado por el entorno después de abrir el proyecto y antes de cualquier otro usuario puedan tomar medidas en el proyecto. Si ya ha tenido preguntar al usuario que actualice la solución, el <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> marca se pasa en el `grfUpgradeFlags` parámetro. Si el usuario abre un proyecto directamente, por ejemplo, mediante el **Agregar proyecto existente** comando, el <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> no se pasa la marca y el proyecto debe solicitar al usuario que actualice.

2.  En respuesta a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> llamada, el proyecto debe evaluar si se actualiza el archivo de proyecto. Si el proyecto no necesita actualizar el tipo de proyecto a una versión nueva, simplemente puede devolver el <xref:Microsoft.VisualStudio.VSConstants.S_OK> marca.

3.  Si el proyecto necesita actualizar el tipo de proyecto a una nueva versión, debe determinar si el archivo de proyecto puede modificarse mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> método y pasando un valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para el `rgfQueryEdit` parámetro. A continuación, el proyecto debe hacer lo siguiente:

    -   Si el `VSQueryEditResult` valor devuelto en el `pfEditCanceled` parámetro es <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, a continuación, la actualización puede continuar porque se puede escribir el archivo de proyecto.

    -   Si el `VSQueryEditResult` valor devuelto en el `pfEditCanceled` parámetro es <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> y `VSQueryEditResult` valor tiene el <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> bit establecido, a continuación, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> debe devolver un error, ya que los usuarios deben resolver el problema de permisos. A continuación, el proyecto debe hacer lo siguiente:

         Notificar el error al usuario mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> y devolver el <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> código de error a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

    -   Si el `VSQueryEditResult` valor es <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> y `VSQueryEditResultFlags` valor tiene el <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bit establecido, a continuación, se debe desproteger el archivo de proyecto mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>,...).

4.  Si el <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> llamada en el archivo de proyecto que hace que el archivo que se desprotegerán y la versión más reciente que se va a recuperar y, después, se descarga y se vuelve a cargar el proyecto. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> método se llama de nuevo una vez que se crea otra instancia del proyecto. En esta segunda llamada, el archivo del proyecto puede escribirse en el disco; se recomienda que el proyecto guarde una copia del archivo del proyecto en el formato anterior con una extensión .OLD, realice los cambios de actualización necesarios y guarde el archivo del proyecto en el nuevo formato. Nuevamente, si se produce un error en cualquier parte del proceso de actualización, el método debe indicarlo devolviendo <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>. Esto hace que el proyecto se descargue en el Explorador de soluciones.

     Es importante comprender el proceso completo que se produce en el entorno para el caso en que la llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> método (especificando un valor de ReportOnly) devuelve el <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> y <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> marcas.

5.  El usuario intenta abrir el archivo del proyecto.

6.  El entorno llama a su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementación.

7.  Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> devuelve `true`, a continuación, el entorno llama a su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementación.

8.  El entorno llama a su <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementación para abrir el archivo e inicialice el objeto de proyecto, por ejemplo, Proyecto1.

9. El entorno llama a su implementación `IVsProjectUpgrade::UpgradeProject` para determinar si debe actualizarse el archivo del proyecto.

10. Se llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> y pasar un valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> para el `rgfQueryEdit` parámetro.

11. El entorno devuelve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> para `VSQueryEditResult` y <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bit está establecido en `VSQueryEditResultFlags`.

12. Su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementación llama `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>).

Esta llamada puede hacer que se extraiga del repositorio una nueva copia del archivo del proyecto y que se recupere la versión más reciente, así como que se deba volver a cargar el archivo del proyecto. En este punto, ocurren dos cosas:

-   Si administra su recarga del proyecto, a continuación, el entorno llama a su <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementación (VSITEMID_ROOT). Cuando reciba esta llamada, vuelva a cargar la primera instancia del proyecto (Proyecto1) y continúe con la actualización del archivo del proyecto. El entorno sabe que administra su recarga del proyecto si devuelve `true` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>).

-   Si no administra su recarga del proyecto, a continuación, devuelven `false` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>). En este caso, antes de <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) que devuelve el entorno crea otra nueva instancia de su proyecto, por ejemplo, Proyecto2, como sigue:

    1.  El entorno llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> en el primer objeto de proyecto, Proyecto1, y coloca este objeto en el estado inactivo.

    2.  El entorno llama a su implementación `IVsProjectFactory::CreateProject` para crear una segunda instancia de su proyecto, Proyecto2.

    3.  El entorno llama a su implementación `IPersistFileFormat::Load` para que abra el archivo e inicialice el segundo objeto del proyecto, Proyecto2.

    4.  El entorno llama a `IVsProjectUpgrade::UpgradeProject` por segunda vez para determinar si se debe actualizar el objeto del proyecto. Sin embargo, esta llamada se realiza en una segunda instancia nueva del proyecto, Proyecto2. Este es el proyecto que se abre en la solución.

        > [!NOTE]
        > En la instancia que su primer proyecto, Proyecto1, se coloca en el estado inactivo, a continuación, debe devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK> desde la primera llamada a su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> implementación.

    5.  Se llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> y pasar un valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> para el `rgfQueryEdit` parámetro.

    6.  El entorno devuelve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> y la actualización puede continuar porque se puede escribir el archivo de proyecto.

Si no puede actualizar, devuelva <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> desde `IVsProjectUpgrade::UpgradeProject`. Si no es necesario realizar ninguna actualización o si opta por no realizar ninguna actualización, trate la llamada `IVsProjectUpgrade::UpgradeProject` como una operación inefectiva. Si la devolución <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>, se agrega un nodo de marcador de posición a la solución para el proyecto.

## <a name="upgrading-project-items"></a>Actualización de elementos de proyecto

Si agrega o administrar los elementos incluidos en los sistemas de proyectos que no implementa, deberá participar en el proceso de actualización del proyecto. Crystal Reports es un ejemplo de un elemento que se puede agregar al sistema del proyecto.

Normalmente, los implementadores de elemento de proyecto desean aprovechar un proyecto totalmente ya creado o actualizado porque necesitan saber qué proyecto son referencias y qué otras propiedades del proyecto existen tomar una decisión de actualización.

### <a name="to-get-the-project-upgrade-notification"></a>Para obtener la notificación de actualización de proyecto

1.  Establecer el <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> marca (definido en vsshell80.idl del explorador) en la implementación del elemento de proyecto. Esto hace que el elemento de proyecto VSPackage carga automáticamente cuando el shell de Visual Studio determina que es un sistema de proyectos en el proceso de actualización.

2.  Notificar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaz a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> método.

3.  El <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaz se activa después de la implementación de sistema de proyecto haya completado sus operaciones de actualización y se crea el nuevo proyecto actualizado. Según el escenario, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaz se activa tras la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, o el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> métodos.

### <a name="to-upgrade-the-project-item-files"></a>Para actualizar los archivos de elementos de proyecto

1.  Debe administrar con cuidado el proceso de copia de seguridad de archivos en la implementación del elemento de proyecto. Esto se aplica en especial para una copia de seguridad en paralelo, donde el `fUpgradeFlag` parámetro de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método está establecido en <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>, donde se colocan los archivos que habían sido una copia de seguridad a lo largo de los archivos del que se designan como ".old". Los archivos de copiados de seguridad anteriores a la hora del sistema cuando se actualiza el proyecto pueden designarse como obsoletos. Además, pueden sobrescribir a menos que realice los pasos específicos para evitar esto.

2.  En el momento en el elemento de proyecto recibe una notificación de la actualización del proyecto, el **Asistente para conversión de Visual Studio** se sigue mostrando. Por lo tanto, debe usar los métodos de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interfaz para proporcionar los mensajes de actualización a la interfaz de usuario del asistente.

## <a name="see-also"></a>Vea también

- [Proyectos](../../extensibility/internals/projects.md)