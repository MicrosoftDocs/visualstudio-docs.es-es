---
title: Actualizar proyectos personalizados | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project systems
- projects [Visual Studio SDK], upgrading
- project system upgrades [Visual Studio]
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
manager: jillfra
ms.openlocfilehash: dee3f9f906f217befe3a4b7b80c068de9d6e6136
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60093974"
---
# <a name="upgrading-custom-projects"></a>Actualizar proyectos personalizados
Si cambia la información guardada en el archivo del proyecto entre diferentes versiones de Visual Studio de su producto, deberá admitir la actualización del archivo del proyecto de la versión anterior a la nueva. Para admitir la actualización que le permite participar en el **Asistente para conversión de Visual Studio**, implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfaz. Esta interfaz contiene el único mecanismo disponible para la actualización de la copia. La actualización del proyecto se produce como parte de la apertura de la solución. El generador de proyectos implementa la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> o esta debe poderse obtener como mínimo desde el generador de proyectos.  
  
 El mecanismo anterior que usa la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> sigue siendo compatible, pero conceptualmente actualiza el sistema del proyecto como parte de la apertura de la solución. Por lo tanto, el entorno <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> llama a la interfaz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aunque se llame a la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> o esta se implemente. Este enfoque le permite usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> para implementar la copia y solo proyectar partes de la actualización, y delegar el resto del trabajo para que lo realice la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> localmente (posiblemente en la nueva ubicación).  
  
 Para una implementación de ejemplo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, consulte [muestras de VSSDK](../misc/vssdk-samples.md).  
  
 Con las actualizaciones del proyecto, se producen los escenarios siguientes:  
  
- Si el archivo tiene un formato más reciente de los que puede admitir el proyecto, debe devolver un error en que se indique esto. Se supone que la versión anterior del producto, por ejemplo, Visual Studio .NET 2003, incluye código para comprobar la versión.  
  
- Si se especifica la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> en el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>, la actualización se implementará como una actualización local antes de la apertura del proyecto.  
  
- Si se especifica la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> en el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>, la actualización se implementa como una actualización de copia.  
  
- Si se especifica la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> en la llamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, significa que el entorno ha solicitado al usuario que actualice el archivo del proyecto como una actualización local, una vez abierto el proyecto. Por ejemplo, el entorno pide al usuario que realice la actualización cuando este abra una versión anterior de la solución.  
  
- Si no se especifica la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> en la llamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, significa que debe solicitar al usuario que actualice el archivo del proyecto.  
  
     A continuación, se muestra un ejemplo del mensaje de solicitud de actualización:  
  
     "El proyecto '%1' se creó con una versión anterior de Visual Studio. Si lo abre con esta versión de Visual Studio, es posible que no pueda abrirlo con versiones anteriores de Visual Studio. ¿Quiere continuar y abrir este proyecto?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>Para implementar IVsProjectUpgradeViaFactory  
  
1. Implemente el método de la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, específicamente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> de su implementación del generador de proyectos, o realice implementaciones que puedan llamarse desde su implementación del generador de proyectos.  
  
2. Si quiere realizar una actualización local como parte de la apertura de la solución, proporcione la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> como el parámetro `VSPUVF_FLAGS` de su implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.  
  
3. Si quiere realizar una actualización local como parte de la apertura de la solución, proporcione la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> como el parámetro `VSPUVF_FLAGS` de su implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.  
  
4. En relación con los pasos 2 y 3, los pasos de actualización del archivo real mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> se pueden implementar según se describe en la sección "Implementación de `IVsProjectUpgade`", o bien puede delegar la actualización del archivo real a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
5. Use los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> para publicar mensajes relacionados con la actualización para el usuario que usa el Asistente para migración de Visual Studio.  
  
6. La interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> se utiliza para implementar cualquier tipo de actualización de archivo que se debe ejecutar como parte de la actualización del proyecto. Esta interfaz no se llama desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, sino que se proporciona como un mecanismo para actualizar los archivos que forman parte del sistema del proyecto, pero que puede que el sistema del proyecto principal no tenga en cuenta directamente. Por ejemplo, esta situación podría producirse si el equipo de desarrollo que administra el resto del sistema del proyecto no administra las propiedades y los archivos relacionados con el compilador.  
  
## <a name="ivsprojectupgrade-implementation"></a>Implementación de IVsProjectUpgrade  
 Si implementa el sistema del proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> únicamente, no puede participar en el **Asistente para conversión de Visual Studio**. Sin embargo, aunque implemente la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, puede agregar de todos modos la actualización del archivo a la implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>Para implementar IVsProjectUpgrade  
  
1. Cuando un usuario intenta abrir un proyecto, el entorno llama al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> después de abrir el proyecto y antes de que se pueda realizar ninguna otra acción de usuario en el proyecto. Si ya se había solicitado al usuario que actualizara la solución, la marca <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> se pasa al parámetro `grfUpgradeFlags`. Si el usuario abre un proyecto directamente, por ejemplo, mediante el **Agregar proyecto existente** comando, el <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> no se pasa la marca y el proyecto debe solicitar al usuario que actualice.  
  
2. En respuesta a la llamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, el proyecto debe evaluar si se actualiza el archivo del proyecto. Si el proyecto no necesita actualizar el tipo de proyecto a una nueva versión, simplemente puede devolver la marca <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
3. Si el proyecto necesita actualizar el tipo de proyecto a una nueva versión, debe determinar si el archivo del proyecto se puede modificar mediante una llamada al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> y pasando un valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para el parámetro `rgfQueryEdit`. A continuación, el proyecto debe hacer lo siguiente:  
  
   - Si el valor `VSQueryEditResult` devuelto en el parámetro `pfEditCanceled` es <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>, la actualización puede continuar porque se puede escribir en el archivo del proyecto.  
  
   - Si el valor `VSQueryEditResult` devuelto en el parámetro `pfEditCanceled` es <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> y el valor `VSQueryEditResult` tiene el bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> establecido, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> debe devolver un error, ya que los usuarios deben resolver el problema de permisos. A continuación, el proyecto debe hacer lo siguiente:  
  
        Notificar el error al usuario mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>. y devolver el código de error <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
   - Si el valor `VSQueryEditResult` es <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> y el valor `VSQueryEditResultFlags` tiene el bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> establecido, el archivo del proyecto se debería extraer del repositorio llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...).  
  
4. Si la llamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> del archivo del proyecto hace que el archivo se extraiga del repositorio y se recupere la última versión, el proyecto se descarga y se vuelve a cargar. El método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> se llama de nuevo una vez que se crea otra instancia del proyecto. En esta segunda llamada, el archivo del proyecto puede escribirse en el disco; se recomienda que el proyecto guarde una copia del archivo del proyecto en el formato anterior con una extensión .OLD, realice los cambios de actualización necesarios y guarde el archivo del proyecto en el nuevo formato. Nuevamente, si se produce un error en cualquier parte del proceso de actualización, el método debe indicarlo mediante la devolución de <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>. Esto hace que el proyecto se descargue en el Explorador de soluciones.  
  
    Es importante comprender el proceso completo que tiene lugar en el entorno por si la llamada al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (que especifica un valor de ReportOnly) devuelve las marcas <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> y <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>.  
  
5. El usuario intenta abrir el archivo del proyecto.  
  
6. El entorno llama a su implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.  
  
7. Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> devuelve `true`, entonces el entorno llama a su implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.  
  
8. El entorno llama a su implementación <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> para que abra el archivo e inicialice el objeto del proyecto, por ejemplo, Proyecto1.  
  
9. El entorno llama a su implementación `IVsProjectUpgrade::UpgradeProject` para determinar si debe actualizarse el archivo del proyecto.  
  
10. Debe llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> y pasar un valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para el parámetro `rgfQueryEdit`.  
  
11. El entorno devuelve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> para `VSQueryEditResult` y el bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> es establece en `VSQueryEditResultFlags`.  
  
12. Su implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> llama a `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>).  
  
    Esta llamada puede hacer que se extraiga del repositorio una nueva copia del archivo del proyecto y que se recupere la versión más reciente, así como que se deba volver a cargar el archivo del proyecto. En este punto, ocurren dos cosas:  
  
- Si administra su propia recarga del proyecto, el entorno llama a su implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT). Cuando reciba esta llamada, vuelva a cargar la primera instancia del proyecto (Proyecto1) y continúe con la actualización del archivo del proyecto. El entorno sabe que administra su recarga del proyecto si devuelve `true` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>).  
  
- Si no administra su recarga del proyecto, devuelve `false` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>). En este caso, antes de <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>([QEF_ForceEdit_NoPrompting](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True), [QEF_DisallowInMemoryEdits](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True),) que devuelve el entorno crea otra nueva instancia del proyecto, por ejemplo, Proyecto2, como se indica a continuación:  
  
  1. El entorno llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> en el primer objeto del proyecto, Proyecto1, y coloca este objeto en el estado inactivo.  
  
  2. El entorno llama a su implementación `IVsProjectFactory::CreateProject` para crear una segunda instancia de su proyecto, Proyecto2.  
  
  3. El entorno llama a su implementación `IPersistFileFormat::Load` para que abra el archivo e inicialice el segundo objeto del proyecto, Proyecto2.  
  
  4. El entorno llama a `IVsProjectUpgrade::UpgradeProject` por segunda vez para determinar si se debe actualizar el objeto del proyecto. Sin embargo, esta llamada se realiza en una segunda instancia nueva del proyecto, Proyecto2. Este es el proyecto que se abre en la solución.  
  
      > [!NOTE]
      >  En caso de que su primer proyecto, Proyecto1, se coloque en el estado inactivo, debe devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK> desde la primera llamada a su implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>. Para consultar una implementación de [Basic Project](http://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) , vea `IVsProjectUpgrade::UpgradeProject`.  
  
  5. Debe llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> y pasar un valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para el parámetro `rgfQueryEdit`.  
  
  6. El entorno devuelve <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> y la actualización puede continuar porque se puede escribir en el archivo del proyecto.  
  
  Si no puede actualizar, devuelva <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> desde `IVsProjectUpgrade::UpgradeProject`. Si no es necesario realizar ninguna actualización o si opta por no realizar ninguna actualización, trate la llamada `IVsProjectUpgrade::UpgradeProject` como una operación inefectiva. Si devuelve <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>, se agrega un nodo de marcador de posición a la solución del proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Asistente para conversión de Visual Studio](http://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Actualizar elementos de proyecto](../misc/upgrading-project-items.md)   
 [Proyectos](../extensibility/internals/projects.md)