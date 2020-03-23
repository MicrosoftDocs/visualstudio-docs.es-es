---
title: Proyectos de actualización ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9170532746dfc61cdec6636fb669676a94535de1
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301630"
---
# <a name="upgrading-projects"></a>Actualización de proyectos

Los cambios en el modelo de proyecto de una versión de Visual Studio a la siguiente pueden requerir que los proyectos y soluciones se actualicen para que se puedan ejecutar en la versión más reciente. Proporciona [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] interfaces que se pueden usar para implementar la compatibilidad con la actualización en sus propios proyectos.

## <a name="upgrade-strategies"></a>Estrategias de actualización

Para admitir una actualización, la implementación del sistema de proyectos debe definir e implementar una estrategia de actualización. Al determinar su estrategia, puede optar por admitir copias de seguridad en paralelo (SxS), copia de seguridad o ambas.

- Copia de seguridad SxS significa que un proyecto copia sólo los archivos que necesitan actualizar en su lugar, añadiendo un sufijo de nombre de archivo adecuado, por ejemplo, ".old".

- Copiar copia de seguridad significa que un proyecto copia todos los elementos del proyecto en una ubicación de copia de seguridad proporcionada por el usuario. A continuación, se actualizan los archivos relevantes en la ubicación del proyecto original.

## <a name="how-upgrade-works"></a>Cómo funciona la actualización

Cuando se abre una solución creada en una versión anterior de Visual Studio en una versión más reciente, el IDE comprueba el archivo de solución para determinar si debe actualizarse. Si se requiere la actualización, el **Asistente para actualización** se inicia automáticamente para guiar al usuario a través del proceso de actualización.

Cuando una solución necesita actualizarse, consulta a cada generador de proyectos su estrategia de actualización. La estrategia determina si el generador de proyectos admite copia de seguridad de copia o copia de seguridad SxS. La información se envía al **Asistente para actualización,** que recopila la información necesaria para la copia de seguridad y presenta las opciones aplicables al usuario.

### <a name="multi-project-solutions"></a>Soluciones multiproyecto

Si una solución contiene varios proyectos y las estrategias de actualización difieren, como cuando un proyecto de C++ que solo admite la copia de seguridad de SxS y un proyecto web que solo admite copia de seguridad de copia, los generadores de proyectos deben negociar la estrategia de actualización.

La solución consulta cada <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>generador de proyectos para . A continuación, llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> para ver si los archivos de proyecto globales necesitan actualización y para determinar las estrategias de actualización admitidas. A continuación, se invoca **el Asistente para actualización.**

Una vez que el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> usuario completa el asistente, se llama en cada generador de proyectos para realizar la actualización real. Para facilitar la copia de seguridad, <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> IVsProjectUpgradeViaFactory métodos proporcionan el servicio para registrar los detalles del proceso de actualización. Este servicio no se puede almacenar en caché.

Después de actualizar todos los archivos globales relevantes, cada fábrica de proyectos puede elegir crear instancias de un proyecto. La implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>del proyecto debe admitir . A <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> continuación, se llama al método para actualizar todos los elementos de proyecto relevantes.

> [!NOTE]
> El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método no proporciona el servicio SVsUpgradeLogger. Este servicio se puede <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>obtener llamando a .

## <a name="best-practices"></a>Prácticas recomendadas

Utilice <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> el servicio para comprobar si puede editar un archivo antes de editarlo y puede guardarlo antes de guardarlo. Esto ayudará a las implementaciones de copia de seguridad y actualización a controlar los archivos de proyecto bajo control de código fuente, archivos con permisos insuficientes, etc.

Utilice <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> el servicio durante todas las fases de copia de seguridad y actualización para proporcionar información sobre el éxito o el error del proceso de actualización.

Para obtener más información acerca de la copia de seguridad y actualización de proyectos, vea los comentarios de IVsProjectUpgrade en vsshell2.idl.

## <a name="upgrading-custom-projects"></a><a name="upgrading-custom-projects"></a>Actualización de proyectos personalizados

Si cambia la información guardada en el archivo del proyecto entre diferentes versiones de Visual Studio de su producto, deberá admitir la actualización del archivo del proyecto de la versión anterior a la nueva. Para admitir la actualización que le permite participar en <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> el Asistente para conversión de Visual **Studio,** implemente la interfaz. Esta interfaz contiene el único mecanismo disponible para la actualización de la copia. La actualización del proyecto se produce como parte de la apertura de la solución. El generador de proyectos implementa la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> o esta debe poderse obtener como mínimo desde el generador de proyectos.

El mecanismo anterior que usa la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> sigue siendo compatible, pero conceptualmente actualiza el sistema del proyecto como parte de la apertura de la solución. Por <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> lo tanto, el entorno de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Visual Studio llama a la interfaz incluso si se llama o implementa la interfaz. Este enfoque le permite usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> para implementar la copia y solo proyectar partes de la actualización, y delegar el resto del trabajo para que lo realice la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> localmente (posiblemente en la nueva ubicación).

Para obtener una <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>implementación de ejemplo de , vea [Ejemplos de VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Con las actualizaciones del proyecto, se producen los escenarios siguientes:

- Si el archivo tiene un formato más reciente de los que puede admitir el proyecto, debe devolver un error en que se indique esto. Esto supone que la versión anterior del producto incluye código para comprobar la versión.

- Si se especifica la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> en el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>, la actualización se implementará como una actualización local antes de la apertura del proyecto.

- Si se especifica la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> en el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>, la actualización se implementa como una actualización de copia.

- Si se especifica la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> en la llamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, significa que el entorno ha solicitado al usuario que actualice el archivo del proyecto como una actualización local, una vez abierto el proyecto. Por ejemplo, el entorno pide al usuario que realice la actualización cuando este abra una versión anterior de la solución.

- Si no se especifica la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> en la llamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, significa que debe solicitar al usuario que actualice el archivo del proyecto.

     A continuación, se muestra un ejemplo del mensaje de solicitud de actualización:

     "El proyecto '%1' se creó con una versión anterior de Visual Studio. Si lo abre con esta versión de Visual Studio, es posible que no pueda abrirlo con versiones anteriores de Visual Studio. ¿Quiere continuar y abrir este proyecto?"

### <a name="to-implement-ivsprojectupgradeviafactory"></a>Para implementar IVsProjectUpgradeViaFactory

1. Implemente el método de la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, específicamente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> de su implementación del generador de proyectos, o realice implementaciones que puedan llamarse desde su implementación del generador de proyectos.

2. Si quiere realizar una actualización local como parte de la apertura de la solución, proporcione la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> como el parámetro `VSPUVF_FLAGS` de su implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.

3. Si quiere realizar una actualización local como parte de la apertura de la solución, proporcione la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> como el parámetro `VSPUVF_FLAGS` de su implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.

4. En relación con los pasos 2 y 3, los pasos de actualización del archivo real mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> se pueden implementar según se describe en la sección "Implementación de `IVsProjectUpgade`", o bien puede delegar la actualización del archivo real a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

5. Use los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> para publicar mensajes relacionados con la actualización para el usuario que usa el Asistente para migración de Visual Studio.

6. La interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> se utiliza para implementar cualquier tipo de actualización de archivo que se debe ejecutar como parte de la actualización del proyecto. Esta interfaz no se llama desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, sino que se proporciona como un mecanismo para actualizar los archivos que forman parte del sistema del proyecto, pero que puede que el sistema del proyecto principal no tenga en cuenta directamente. Por ejemplo, esta situación podría producirse si el equipo de desarrollo que administra el resto del sistema del proyecto no administra las propiedades y los archivos relacionados con el compilador.

### <a name="ivsprojectupgrade-implementation"></a>Implementación de IVsProjectUpgrade

Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> el sistema del proyecto solo implementa, no puede participar en el **Asistente para conversión**de Visual Studio . Sin embargo, aunque implemente la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, puede agregar de todos modos la actualización del archivo a la implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

#### <a name="to-implement-ivsprojectupgrade"></a>Para implementar IVsProjectUpgrade

1. Cuando un usuario intenta abrir un proyecto, el entorno llama al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> después de abrir el proyecto y antes de que se pueda realizar ninguna otra acción de usuario en el proyecto. Si ya se había solicitado al usuario que actualizara la solución, la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> se pasa al parámetro `grfUpgradeFlags`. Si el usuario abre un proyecto directamente, por ejemplo, <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> mediante el comando Agregar proyecto **existente,** no se pasa la marca y el proyecto debe solicitar al usuario que actualice.

2. En respuesta a la llamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, el proyecto debe evaluar si se actualiza el archivo del proyecto. Si el proyecto no necesita actualizar el tipo de proyecto a una nueva versión, simplemente puede devolver la marca <xref:Microsoft.VisualStudio.VSConstants.S_OK>.

3. Si el proyecto necesita actualizar el tipo de proyecto a una nueva versión, debe determinar si el archivo del proyecto se puede modificar mediante una llamada al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> y pasando un valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para el parámetro `rgfQueryEdit`. A continuación, el proyecto debe hacer lo siguiente:

    - Si el valor `VSQueryEditResult` devuelto en el parámetro `pfEditCanceled` es <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, la actualización puede continuar porque se puede escribir en el archivo del proyecto.

    - Si el valor `VSQueryEditResult` devuelto en el parámetro `pfEditCanceled` es <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> y el valor `VSQueryEditResult` tiene el bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> establecido, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> debe devolver un error, ya que los usuarios deben resolver el problema de permisos. A continuación, el proyecto debe hacer lo siguiente:

         Informe del error al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> usuario llamando <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>devuelva el código de error a .

    - Si el valor `VSQueryEditResult` es <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> y el valor `VSQueryEditResultFlags` tiene el bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> establecido, el archivo del proyecto se debería extraer del repositorio llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>,...).

4. Si la llamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> del archivo del proyecto hace que el archivo se extraiga del repositorio y se recupere la última versión, el proyecto se descarga y se vuelve a cargar. El método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> se llama de nuevo una vez que se crea otra instancia del proyecto. En esta segunda llamada, el archivo del proyecto puede escribirse en el disco; se recomienda que el proyecto guarde una copia del archivo del proyecto en el formato anterior con una extensión .OLD, realice los cambios de actualización necesarios y guarde el archivo del proyecto en el nuevo formato. Nuevamente, si se produce un error en cualquier parte del proceso de actualización, el método debe indicarlo mediante la devolución de <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>. Esto hace que el proyecto se descargue en el Explorador de soluciones.

     Es importante comprender el proceso completo que tiene lugar en el entorno por si la llamada al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (que especifica un valor de ReportOnly) devuelve las marcas <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> y <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc>.

5. El usuario intenta abrir el archivo del proyecto.

6. El entorno llama a su implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.

7. Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> devuelve `true`, entonces el entorno llama a su implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.

8. El entorno llama a su implementación <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> para que abra el archivo e inicialice el objeto del proyecto, por ejemplo, Proyecto1.

9. El entorno llama a su implementación `IVsProjectUpgrade::UpgradeProject` para determinar si debe actualizarse el archivo del proyecto.

10. Debe llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> y pasar un valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> para el parámetro `rgfQueryEdit`.

11. El entorno devuelve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> para `VSQueryEditResult` y el bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> es establece en `VSQueryEditResultFlags`.

12. Su implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> llama a `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>).

Esta llamada puede hacer que se extraiga del repositorio una nueva copia del archivo del proyecto y que se recupere la versión más reciente, así como que se deba volver a cargar el archivo del proyecto. En este punto, ocurren dos cosas:

- Si administra su propia recarga del proyecto, el entorno llama a su implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT). Cuando reciba esta llamada, vuelva a cargar la primera instancia del proyecto (Proyecto1) y continúe con la actualización del archivo del proyecto. El entorno sabe que administra su recarga del proyecto si devuelve `true` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>).

- Si no administra su recarga del proyecto, devuelve `false` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>). En este caso, antes <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>de que (QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) se devuelva, el entorno crea otra nueva instancia del proyecto, por ejemplo, Project2, como se indica a continuación:

    1. El entorno llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> en el primer objeto del proyecto, Proyecto1, y coloca este objeto en el estado inactivo.

    2. El entorno llama a su implementación `IVsProjectFactory::CreateProject` para crear una segunda instancia de su proyecto, Proyecto2.

    3. El entorno llama a su implementación `IPersistFileFormat::Load` para que abra el archivo e inicialice el segundo objeto del proyecto, Proyecto2.

    4. El entorno llama a `IVsProjectUpgrade::UpgradeProject` por segunda vez para determinar si se debe actualizar el objeto del proyecto. Sin embargo, esta llamada se realiza en una segunda instancia nueva del proyecto, Proyecto2. Este es el proyecto que se abre en la solución.

        > [!NOTE]
        > En caso de que su primer proyecto, Proyecto1, se coloque en el estado inactivo, debe devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK> desde la primera llamada a su implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>.

    5. Debe llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> y pasar un valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> para el parámetro `rgfQueryEdit`.

    6. El entorno devuelve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> y la actualización puede continuar porque se puede escribir en el archivo del proyecto.

Si no puede actualizar, devuelva <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> desde `IVsProjectUpgrade::UpgradeProject`. Si no es necesario realizar ninguna actualización o si opta por no realizar ninguna actualización, trate la llamada `IVsProjectUpgrade::UpgradeProject` como una operación inefectiva. Si devuelve <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>, se agrega un nodo de marcador de posición a la solución del proyecto.

## <a name="upgrading-project-items"></a>Actualización de elementos de proyecto

Si agrega o administra elementos dentro de sistemas de proyecto que no implementa, es posible que deba participar en el proceso de actualización del proyecto. Crystal Reports es un ejemplo de un elemento que se puede agregar al sistema de proyectos.

Normalmente, los implementadores de elementos de proyecto desean aprovechar un proyecto ya completamente creado y actualizado porque necesitan saber cuáles son las referencias de proyecto y qué otras propiedades del proyecto están allí para tomar una decisión de actualización.

### <a name="to-get-the-project-upgrade-notification"></a>Para obtener la notificación de actualización del proyecto

1. Establezca <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> el indicador (definido en vsshell80.idl) en la implementación del elemento de proyecto. Esto hace que el elemento de proyecto VSPackage se cargue automáticamente cuando el shell de Visual Studio determina que un sistema de proyecto está en proceso de actualización.

2. Aconseje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> interfaz a través del método.

3. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaz se desencadena después de que la implementación del sistema de proyecto haya completado sus operaciones de actualización y se cree el nuevo proyecto actualizado. Dependiendo del escenario, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>se <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>desencadena <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> después de los métodos , the o los métodos.

### <a name="to-upgrade-the-project-item-files"></a>Para actualizar los archivos de elementos del proyecto

1. Debe administrar cuidadosamente el proceso de copia de seguridad de archivos en la implementación del elemento de proyecto. Esto se aplica en particular para una copia `fUpgradeFlag` de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> seguridad en <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>paralelo, donde el parámetro del método se establece en , donde los archivos que se habían realizado una copia de seguridad se colocan a lo largo de los archivos laterales que se designan como ".old". Los archivos de copia de seguridad anteriores a la hora del sistema cuando se actualizó el proyecto se pueden designar como obsoletos. Además, es posible que se sobrescriban a menos que tome medidas específicas para evitarlo.

2. En el momento en que el elemento de proyecto recibe una notificación de la actualización del proyecto, el **Asistente para conversión** de Visual Studio sigue mostrada. Por lo tanto, debe <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> usar los métodos de la interfaz para proporcionar mensajes de actualización a la interfaz de usuario del asistente.

## <a name="see-also"></a>Consulte también

- [Proyectos](../../extensibility/internals/projects.md)
