---
title: Actualizar proyectos personalizados | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading project systems
- projects [Visual Studio SDK], upgrading
- project system upgrades [Visual Studio]
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
manager: douge
ms.openlocfilehash: 5c3fd31cfc7cfbf3f7dd687d38483f5bb62703ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577824"
---
# <a name="upgrading-custom-projects"></a>Actualizar proyectos personalizados
Si cambia la información guardada en el archivo del proyecto entre diferentes versiones de Visual Studio de su producto, deberá admitir la actualización del archivo del proyecto de la versión anterior a la nueva. Para admitir la actualización que le permite participar en el **Asistente para conversión de Visual Studio**, implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaz. Esta interfaz contiene el único mecanismo disponible para la actualización de la copia. La actualización del proyecto se produce como parte de la apertura de la solución. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaz se implementa mediante el generador de proyectos, o debe ser al menos puede obtenerse desde el generador de proyectos.  
  
 El mecanismo anterior que usa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfaz se sigue admitiendo, pero conceptualmente actualiza el sistema del proyecto como parte del proyecto abierto. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfaz, por tanto, se llama el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] entorno, aunque el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaz se llama o se implementa. Este enfoque permite usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> para implementar la copia y solo proyectar partes de la actualización y delegar el resto del trabajo que se realiza en contexto (posiblemente en la nueva ubicación), el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfaz.  
  
 Para una implementación de ejemplo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, consulte [muestras de VSSDK](../misc/vssdk-samples.md).  
  
 Con las actualizaciones del proyecto, se producen los escenarios siguientes:  
  
-   Si el archivo tiene un formato más reciente de los que puede admitir el proyecto, debe devolver un error en que se indique esto. Se supone que la versión anterior del producto, por ejemplo, Visual Studio .NET 2003, incluye código para comprobar la versión.  
  
-   Si el <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> indicador se especifica en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método, la actualización se va a implementarse como una actualización en contexto antes de la apertura del proyecto.  
  
-   Si el <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> indicador se especifica en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método, la actualización se implementa como una actualización de la copia.  
  
-   Si el <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> indicador se especifica en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> llamar, a continuación, el usuario ha solicitado por el entorno para actualizar el archivo de proyecto como una actualización en contexto, una vez que se abre el proyecto. Por ejemplo, el entorno pide al usuario que realice la actualización cuando este abra una versión anterior de la solución.  
  
-   Si el <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> marca no se especifica en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> llamar, a continuación, debe pedir al usuario que actualice el archivo de proyecto.  
  
     A continuación, se muestra un ejemplo del mensaje de solicitud de actualización:  
  
     "El proyecto '%1' se creó con una versión anterior de Visual Studio. Si lo abre con esta versión de Visual Studio, es posible que no pueda abrirlo con versiones anteriores de Visual Studio. ¿Quiere continuar y abrir este proyecto?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>Para implementar IVsProjectUpgradeViaFactory  
  
1.  Implemente el método de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaz, específicamente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método en su implementación del generador de proyecto, o realice implementaciones que se puede llamar desde su implementación del generador de proyecto.  
  
2.  Si desea realizar una actualización en contexto como parte de la solución abrir, proporcione la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> como el `VSPUVF_FLAGS` parámetro en su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementación.  
  
3.  Si desea realizar una actualización en contexto como parte de la solución abrir, proporcione la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> como el `VSPUVF_FLAGS` parámetro en su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementación.  
  
4.  Los pasos 2 y 3, con pasos de actualización del archivo real <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, se puede implementar como se describe en la "implementación `IVsProjectUpgade`" sección, o bien puede delegar la actualización del archivo real a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
5.  Utilice los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> para después de la actualización relacionada con los mensajes para el usuario mediante el Asistente para migración de Visual Studio.  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> interfaz se usa para implementar cualquier tipo de actualización de archivo que se debe ejecutar como parte de la actualización del proyecto. Esta interfaz no se llama desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, sino que se proporciona como un mecanismo para actualizar los archivos que forman parte del sistema del proyecto, pero el sistema del proyecto principal no puede tener en cuenta directamente. Por ejemplo, esta situación podría producirse si el equipo de desarrollo que administra el resto del sistema del proyecto no administra las propiedades y los archivos relacionados con el compilador.  
  
## <a name="ivsprojectupgrade-implementation"></a>Implementación de IVsProjectUpgrade  
 Si implementa el sistema del proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> únicamente, no puede participar en el **Asistente para conversión de Visual Studio**. Sin embargo, incluso si decide implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaz, aún puede delegar la actualización del archivo a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementación.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>Para implementar IVsProjectUpgrade  
  
1.  Cuando un usuario intenta abrir un proyecto, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> método es llamado por el entorno después de abrir el proyecto y antes de cualquier otro usuario puedan tomar medidas en el proyecto. Si ya ha tenido preguntar al usuario que actualice la solución, el <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> marca se pasa en el `grfUpgradeFlags` parámetro. Si el usuario abre un proyecto directamente, por ejemplo, mediante el **Agregar proyecto existente** comando, el <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> no se pasa la marca y el proyecto debe solicitar al usuario que actualice.  
  
2.  En respuesta a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> llamada, el proyecto debe evaluar si se actualiza el archivo de proyecto. Si el proyecto no necesita actualizar el tipo de proyecto a una versión nueva, simplemente puede devolver el <xref:Microsoft.VisualStudio.VSConstants.S_OK> marca.  
  
3.  Si el proyecto necesita actualizar el tipo de proyecto a una nueva versión, debe determinar si el archivo de proyecto puede modificarse mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> método y pasando un valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para el `rgfQueryEdit` parámetro. A continuación, el proyecto debe hacer lo siguiente:  
  
    -   Si el `VSQueryEditResult` valor devuelto en el `pfEditCanceled` parámetro es <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>, a continuación, la actualización puede continuar porque se puede escribir el archivo de proyecto.  
  
    -   Si el `VSQueryEditResult` valor devuelto en el `pfEditCanceled` parámetro es <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> y `VSQueryEditResult` valor tiene el <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit establecido, a continuación, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> debe devolver un error, ya que los usuarios deben resolver el problema de permisos. A continuación, el proyecto debe hacer lo siguiente:  
  
         Notificar el error al usuario mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>. y devolver el <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> código de error a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
    -   Si el `VSQueryEditResult` valor es <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> y `VSQueryEditResultFlags` valor tiene el <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit establecido, a continuación, se debe desproteger el archivo de proyecto mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...).  
  
4.  Si el <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> llamada en el archivo de proyecto que hace que el archivo que se desprotegerán y la versión más reciente que se va a recuperar y, después, se descarga y se vuelve a cargar el proyecto. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> método se llama de nuevo una vez que se crea otra instancia del proyecto. En esta segunda llamada, el archivo del proyecto puede escribirse en el disco; se recomienda que el proyecto guarde una copia del archivo del proyecto en el formato anterior con una extensión .OLD, realice los cambios de actualización necesarios y guarde el archivo del proyecto en el nuevo formato. Nuevamente, si se produce un error en cualquier parte del proceso de actualización, el método debe indicarlo devolviendo <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>. Esto hace que el proyecto se descargue en el Explorador de soluciones.  
  
     Es importante comprender el proceso completo que se produce en el entorno para el caso en que la llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> método (especificando un valor de ReportOnly) devuelve el <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> y <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> marcas.  
  
5.  El usuario intenta abrir el archivo del proyecto.  
  
6.  El entorno llama a su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementación.  
  
7.  Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> devuelve `true`, a continuación, el entorno llama a su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementación.  
  
8.  El entorno llama a su <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementación para abrir el archivo e inicialice el objeto de proyecto, por ejemplo, Proyecto1.  
  
9. El entorno llama a su implementación `IVsProjectUpgrade::UpgradeProject` para determinar si debe actualizarse el archivo del proyecto.  
  
10. Se llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> y pasar un valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para el `rgfQueryEdit` parámetro.  
  
11. El entorno devuelve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> para `VSQueryEditResult` y <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit está establecido en `VSQueryEditResultFlags`.  
  
12. Su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementación llama `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>).  
  
 Esta llamada puede hacer que se extraiga del repositorio una nueva copia del archivo del proyecto y que se recupere la versión más reciente, así como que se deba volver a cargar el archivo del proyecto. En este punto, ocurren dos cosas:  
  
-   Si administra su recarga del proyecto, a continuación, el entorno llama a su <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementación (VSITEMID_ROOT). Cuando reciba esta llamada, vuelva a cargar la primera instancia del proyecto (Proyecto1) y continúe con la actualización del archivo del proyecto. El entorno sabe que administra su recarga del proyecto si devuelve `true` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>).  
  
-   Si no administra su recarga del proyecto, a continuación, devuelven `false` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>). En este caso, antes de <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>([QEF_ForceEdit_NoPrompting](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True), [QEF_DisallowInMemoryEdits](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True),) que devuelve el entorno crea otra nueva instancia del proyecto, por ejemplo, Proyecto2, como se indica a continuación:  
  
    1.  El entorno llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> en el primer objeto de proyecto, Proyecto1, y coloca este objeto en el estado inactivo.  
  
    2.  El entorno llama a su implementación `IVsProjectFactory::CreateProject` para crear una segunda instancia de su proyecto, Proyecto2.  
  
    3.  El entorno llama a su implementación `IPersistFileFormat::Load` para que abra el archivo e inicialice el segundo objeto del proyecto, Proyecto2.  
  
    4.  El entorno llama a `IVsProjectUpgrade::UpgradeProject` por segunda vez para determinar si se debe actualizar el objeto del proyecto. Sin embargo, esta llamada se realiza en una segunda instancia nueva del proyecto, Proyecto2. Este es el proyecto que se abre en la solución.  
  
        > [!NOTE]
        >  En la instancia que su primer proyecto, Proyecto1, se coloca en el estado inactivo, a continuación, debe devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK> desde la primera llamada a su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> implementación. Consulte [proyecto básico](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) para una implementación de `IVsProjectUpgrade::UpgradeProject`.  
  
    5.  Se llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> y pasar un valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para el `rgfQueryEdit` parámetro.  
  
    6.  El entorno devuelve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> y la actualización puede continuar porque se puede escribir el archivo de proyecto.  
  
 Si no puede actualizar, devuelva <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> desde `IVsProjectUpgrade::UpgradeProject`. Si no es necesario realizar ninguna actualización o si opta por no realizar ninguna actualización, trate la llamada `IVsProjectUpgrade::UpgradeProject` como una operación inefectiva. Si la devolución <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>, se agrega un nodo de marcador de posición a la solución para el proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Asistente para conversión de Visual Studio](http://msdn.microsoft.com/en-us/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Actualizar elementos de proyecto](../misc/upgrading-project-items.md)   
 [Proyectos](../extensibility/internals/projects.md)