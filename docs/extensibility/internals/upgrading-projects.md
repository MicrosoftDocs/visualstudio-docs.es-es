---
title: Actualizar proyectos | Documentos de Microsoft
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
ms.openlocfilehash: cb64d71a50cb59a3c981dd87695bbb685f793761
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="upgrading-projects"></a>Actualizar proyectos
Cambios en el modelo de proyecto de una versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a la siguiente puede requerir que puede actualizar los proyectos y soluciones para que se puede ejecutar en la versión más reciente. El [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] proporciona interfaces que pueden utilizarse para implementar la compatibilidad con la actualización a sus propios proyectos.  
  
## <a name="upgrade-strategies"></a>Estrategias de actualización  
 Para admitir una actualización, la implementación de sistema de proyecto debe definir e implementar una estrategia de actualización. Para determinar la estrategia de, puede elegir admitir la copia de seguridad paralelo (SxS), copia de seguridad o ambos.  
  
-   Copia de seguridad de SxS significa que un proyecto de sólo copia los archivos que se deben actualizar en su lugar, agrega un sufijo de nombre de archivo adecuado, por ejemplo, ".old".  
  
-   Copia de seguridad significa que un proyecto copia todos los elementos de proyecto en una ubicación de copia de seguridad proporcionado por el usuario. A continuación, se actualizan los archivos pertinentes en la ubicación del proyecto original.  
  
## <a name="how-upgrade-works"></a>Cómo actualizar Works  
 Cuando una solución creada en una versión anterior de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se abre en una versión más reciente, las comprobaciones IDE la solución de archivos para determinar si se debe actualizarse. Si la actualización es necesaria, el **Asistente para actualización** se inicia automáticamente para guiar al usuario a través del proceso de actualización.  
  
 Cuando una solución necesita actualizar, consulta cada generador de proyectos para su estrategia de actualización. La estrategia determina si el generador de proyectos admite la copia de seguridad o de copia de seguridad de SxS. La información se envía a la **Asistente para actualización**, que recopila la información necesaria para la copia de seguridad y presenta las opciones que correspondan al usuario.  
  
### <a name="multi-project-solutions"></a>Soluciones de varios proyectos  
 Si una solución contiene varios proyectos y las estrategias de actualización son distintas, como cuando un proyecto de C++ que solo es compatible con copia de seguridad de SxS y un proyecto Web que solo admiten la copia de seguridad, los generadores de proyecto deben negociar la estrategia de actualización.  
  
 La solución consulta cada generador de proyectos para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. A continuación, llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> para ver si es necesario actualizar archivos del proyecto global y para determinar las estrategias de actualización admitidas. El **Asistente para actualización** , a continuación, se invoca.  
  
 Después de que el usuario completa el asistente, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> se llama en cada generador de proyectos para realizar la actualización real. Para facilitar la copia de seguridad, proporcionan métodos IVsProjectUpgradeViaFactory el <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> servicio para registrar los detalles del proceso de actualización. Este servicio no se almacenarán en caché.  
  
 Después de actualizar todos los archivos globales relevantes, puede elegir cada generador de proyectos crear instancias de un proyecto. La implementación de proyecto debe admitir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> , a continuación, se llama el método para actualizar todos los elementos de proyecto correspondiente.  
  
> [!NOTE]
>  El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método no proporciona el servicio SVsUpgradeLogger. Este servicio se puede obtener mediante una llamada a <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.  
  
## <a name="best-practices"></a>Procedimientos recomendados  
 Use el <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> servicio para comprobar si puede editar un archivo antes de editarlo y guardarlo antes de guardarla. Esto le ayudará a la copia de seguridad y actualización implementaciones controlan los archivos de proyecto bajo control de código fuente, archivos con permisos insuficientes y así sucesivamente.  
  
 Use el <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> durante todas las fases de copia de seguridad de servicio y actualizar para proporcionar información sobre el éxito o error del proceso de actualización.  
  
 Para obtener más información acerca de cómo realizar copias de seguridad y actualizar proyectos, vea los comentarios para IVsProjectUpgrade en vsshell2.idl.  
  
## <a name="upgrading-custom-projects"></a> Actualizar proyectos personalizados
Si cambia la información guardada en el archivo del proyecto entre diferentes versiones de Visual Studio de su producto, deberá admitir la actualización del archivo del proyecto de la versión anterior a la nueva. Para admitir la actualización que le permite participar en la **Asistente para conversión de Visual Studio**, implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaz. Esta interfaz contiene el único mecanismo disponible para la actualización de la copia. La actualización del proyecto se produce como parte de la apertura de la solución. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaz se implementa mediante el generador de proyectos, o al menos debería ser puede obtenerse desde el generador de proyectos.  
  
 El mecanismo anterior que usa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfaz se sigue admitiendo, pero conceptualmente actualiza el sistema del proyecto como parte del proyecto abierto. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfaz, por tanto, se llama la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno, aunque la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaz se llama o se implementa. Este enfoque le permite usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> para implementar la copia y solo proyectar partes de la actualización y delegar el resto del trabajo que se efectúa en contexto (posiblemente en la nueva ubicación); para ello la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfaz.  
  
 Para una implementación de ejemplo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, consulte [muestras de VSSDK](http://aka.ms/vs2015sdksamples).  
  
 Con las actualizaciones del proyecto, se producen los escenarios siguientes:  
  
-   Si el archivo tiene un formato más reciente de los que puede admitir el proyecto, debe devolver un error en que se indique esto. Se supone que la versión anterior del producto incluye código para comprobar la versión.  
  
-   Si el <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> indicador se especifica en la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> (método), la actualización se va a implementarse como una actualización en contexto antes de la apertura del proyecto.  
  
-   Si el <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> indicador se especifica en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método, la actualización se implementa como una actualización de copia.  
  
-   Si el <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> indicador se especifica en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> llamar, a continuación, el usuario ha solicitado al entorno para actualizar el archivo de proyecto como una actualización en contexto, una vez que se abre el proyecto. Por ejemplo, el entorno pide al usuario que realice la actualización cuando este abra una versión anterior de la solución.  
  
-   Si el <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> marca no se especifica en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> llamar, significa que debe solicitar al usuario que actualice el archivo de proyecto.  
  
     A continuación, se muestra un ejemplo del mensaje de solicitud de actualización:  
  
     "El proyecto '%1' se creó con una versión anterior de Visual Studio. Si lo abre con esta versión de Visual Studio, es posible que no pueda abrirlo con versiones anteriores de Visual Studio. ¿Quiere continuar y abrir este proyecto?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>Para implementar IVsProjectUpgradeViaFactory  
  
1.  Implemente el método de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaz, específicamente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método en su implementación del generador de proyecto, o realice implementaciones pueda llamar desde su implementación del generador de proyectos.  
  
2.  Si desea realizar una actualización en contexto como parte de la solución abriendo, proporcione la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> como el `VSPUVF_FLAGS` parámetro en su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementación.  
  
3.  Si desea realizar una actualización en contexto como parte de la solución abriendo, proporcione la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> como el `VSPUVF_FLAGS` parámetro en su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementación.  
  
4.  En ambos los pasos 2 y 3, el archivo real actualizar pasos, con <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, se puede implementar como se describe en la "implementación `IVsProjectUpgade`" sección, o bien puede delegar la actualización del archivo real a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
5.  Use los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> para después de la actualización relacionados con mensajes para el usuario mediante el Asistente para migración de Visual Studio.  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> interfaz se utiliza para implementar cualquier tipo de actualización del archivo que se debe ejecutar como parte de la actualización del proyecto. Esta interfaz no se llama desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, sino que se proporciona como un mecanismo para actualizar los archivos que forman parte del sistema del proyecto, pero el sistema de proyecto principal no puede tener en cuenta directamente. Por ejemplo, esta situación podría producirse si el equipo de desarrollo que administra el resto del sistema del proyecto no administra las propiedades y los archivos relacionados con el compilador.  
  
### <a name="ivsprojectupgrade-implementation"></a>Implementación de IVsProjectUpgrade  
 Si implementa el sistema de proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> únicamente, no puede participar en la **Asistente para conversión de Visual Studio**. Sin embargo, incluso si implementa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaz, todavía puede delegar la actualización del archivo a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementación.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>Para implementar IVsProjectUpgrade  
  
1.  Cuando un usuario intenta abrir un proyecto, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> método es llamado por el entorno después de abre el proyecto y antes de cualquier otro usuario se pueda realizar la acción en el proyecto. Si ya se había solicitado al usuario que actualice la solución, la <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> marca se pasa en el `grfUpgradeFlags` parámetro. Si el usuario abre un proyecto directamente, tal como mediante el uso de la **Agregar proyecto existente** comando, la <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> no se pasa la marca y el proyecto debe solicitar al usuario que actualice.  
  
2.  En respuesta a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> llamada, el proyecto debe evaluar si se actualiza el archivo de proyecto. Si el proyecto no es necesario actualizar el tipo de proyecto a una nueva versión, puede devolver simplemente la <xref:Microsoft.VisualStudio.VSConstants.S_OK> marca.  
  
3.  Si el proyecto debe actualizar el tipo de proyecto a una nueva versión, debe determinar si el archivo de proyecto se puede modificar mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> método y pasar un valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para el `rgfQueryEdit` parámetro. A continuación, el proyecto debe hacer lo siguiente:  
  
    -   Si el `VSQueryEditResult` valor devuelto en el `pfEditCanceled` parámetro es <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>, a continuación, la actualización puede continuar porque se puede escribir el archivo de proyecto.  
  
    -   Si el `VSQueryEditResult` valor devuelto en el `pfEditCanceled` parámetro es <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> y `VSQueryEditResult` valor tiene el <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit establecido, a continuación, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> debe devolver un error, porque los usuarios deben resolver el problema de permisos. A continuación, el proyecto debe hacer lo siguiente:  
  
         Notificar el error al usuario mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> y devolver el <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> código de error a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
    -   Si el `VSQueryEditResult` valor es <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> y `VSQueryEditResultFlags` valor tiene el <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit establecido, a continuación, se debe desproteger el archivo de proyecto mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...).  
  
4.  Si el <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> llamada en el archivo de proyecto hace que el archivo esté desprotegido y la versión más reciente para recuperar, a continuación, se descarga y se vuelve a cargar el proyecto. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> método se llama de nuevo una vez que se crea otra instancia del proyecto. En esta segunda llamada, el archivo del proyecto puede escribirse en el disco; se recomienda que el proyecto guarde una copia del archivo del proyecto en el formato anterior con una extensión .OLD, realice los cambios de actualización necesarios y guarde el archivo del proyecto en el nuevo formato. Una vez más, si se produce un error en cualquier parte del proceso de actualización, el método debe indicar error devolviendo <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>. Esto hace que el proyecto se descargue en el Explorador de soluciones.  
  
     Es importante comprender el proceso completo que se produce en el entorno para el caso en que la llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> método (especificando un valor de ReportOnly) devuelve el <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> y <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> marcas.  
  
5.  El usuario intenta abrir el archivo del proyecto.  
  
6.  El entorno llama su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementación.  
  
7.  Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> devuelve `true`, entonces el entorno llama su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementación.  
  
8.  El entorno llama su <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementación para abrir el archivo e inicialice el objeto de proyecto, por ejemplo, Proyecto1.  
  
9. El entorno llama a su implementación `IVsProjectUpgrade::UpgradeProject` para determinar si debe actualizarse el archivo del proyecto.  
  
10. Se llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> y pasar un valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para el `rgfQueryEdit` parámetro.  
  
11. El entorno vuelve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> para `VSQueryEditResult` y <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit está establecido en `VSQueryEditResultFlags`.  
  
12. Su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementación llama `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>).  
  
 Esta llamada puede hacer que se extraiga del repositorio una nueva copia del archivo del proyecto y que se recupere la versión más reciente, así como que se deba volver a cargar el archivo del proyecto. En este punto, ocurren dos cosas:  
  
-   Si administra su propia recarga del proyecto, el entorno llama su <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementación (VSITEMID_ROOT). Cuando reciba esta llamada, vuelva a cargar la primera instancia del proyecto (Proyecto1) y continúe con la actualización del archivo del proyecto. El entorno sabe que administra su recarga del proyecto si devuelve `true` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>).  
  
-   Si no administra su recarga del proyecto, devuelven `false` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>). En este caso, antes de <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) devuelve, el entorno crea otra nueva instancia del proyecto, por ejemplo, Proyecto2, de la manera siguiente:  
  
    1.  El entorno llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> en el primer objeto del proyecto, Proyecto1, y coloca este objeto en el estado inactivo.  
  
    2.  El entorno llama a su implementación `IVsProjectFactory::CreateProject` para crear una segunda instancia de su proyecto, Proyecto2.  
  
    3.  El entorno llama a su implementación `IPersistFileFormat::Load` para que abra el archivo e inicialice el segundo objeto del proyecto, Proyecto2.  
  
    4.  El entorno llama a `IVsProjectUpgrade::UpgradeProject` por segunda vez para determinar si se debe actualizar el objeto del proyecto. Sin embargo, esta llamada se realiza en una segunda instancia nueva del proyecto, Proyecto2. Este es el proyecto que se abre en la solución.  
  
        > [!NOTE]
        >  En la instancia que el primer proyecto, Proyecto1, se coloca en el estado inactivo, a continuación, debe devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK> desde la primera llamada a su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> implementación.  
  
    5.  Se llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> y pasar un valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para el `rgfQueryEdit` parámetro.  
  
    6.  El entorno vuelve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> y la actualización puede continuar porque se puede escribir el archivo de proyecto.  
  
 Si no puede actualizar, devuelva <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> de `IVsProjectUpgrade::UpgradeProject`. Si no es necesario realizar ninguna actualización o si opta por no realizar ninguna actualización, trate la llamada `IVsProjectUpgrade::UpgradeProject` como una operación inefectiva. Si devuelve <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>, se agrega un nodo de marcador de posición a la solución para el proyecto.  
  
## <a name="upgrading-project-items"></a>Actualización de elementos de proyecto
  
Si agrega o administrar los elementos dentro de sistemas del proyecto no se implementan, debe participar en el proceso de actualización de proyecto. Crystal Reports es un ejemplo de un elemento que se pueden agregar al sistema del proyecto.  
  
 Normalmente, los implementadores de elemento de proyecto desean aprovechar un proyecto totalmente ya ha creado una instancia y actualizado porque necesitan saber qué proyecto son referencias y ¿qué otras propiedades del proyecto existen tomar una decisión de actualización.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Para obtener la notificación de actualización de proyecto  
  
1.  Establecer el <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> marca (definido en vsshell80.idl) en su implementación de elemento de proyecto. Esto hace que el elemento de proyecto VSPackage automáticamente al cargar la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell determina que un sistema de proyectos en el proceso de actualización.  
  
2.  Notificar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaz a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> método.  
  
3.  El <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaz se activa después de la implementación de sistema de proyecto haya completado sus operaciones de actualización y se crea el nuevo proyecto actualizado. Según el escenario, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfaz se activa tras la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> métodos.  
  
### <a name="to-upgrade-the-project-item-files"></a>Para actualizar los archivos de elementos de proyecto  
  
1.  Debe administrar con cuidado el proceso de copia de seguridad de archivos en la implementación de elemento de proyecto. Esto se aplica en particular a una copia de seguridad en paralelo, donde el `fUpgradeFlag` parámetro de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método está establecido en <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>, donde se colocan los archivos que tenían con copias de seguridad a lo largo de los archivos de comandos que están designados como ".old". Los archivos de copia de seguridad anteriores a la hora del sistema cuando se actualiza el proyecto pueden designarse como obsoleta. Además, podrían sobrescribirse a menos que seguir unos pasos específicos para evitar que esto.  
  
2.  En el momento en el elemento de proyecto recibe una notificación de la actualización del proyecto, el **Asistente para conversión de Visual Studio** se sigue mostrando. Por lo tanto, debe utilizar los métodos de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interfaz para proporcionar mensajes de actualización en el Asistente para la interfaz de usuario.  
  
## <a name="see-also"></a>Vea también  
 [Proyectos](../../extensibility/internals/projects.md)   
