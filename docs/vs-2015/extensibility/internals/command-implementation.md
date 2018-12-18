---
title: Implementación de comandos | Microsoft Docs
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
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: be1bcecb740fb0c375d0f461639a8b0d5e40669a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765201"
---
# <a name="command-implementation"></a>Implementación de comandos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Para implementar un comando en un VSPackage, debe realizar las siguientes tareas:  
  
1. En el archivo .vsct, configure un grupo de comandos y, a continuación, agregue el comando a él. Para obtener más información, consulte [Visual Studio Command Table (. Archivos Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2. Registrar el comando con Visual Studio.  
  
3. Implementar el comando.  
  
   Las siguientes secciones explican cómo registrar e implementar los comandos.  
  
## <a name="registering-commands-with-visual-studio"></a>Registrar comandos con Visual Studio  
 Si el comando se va a aparecer en un menú, debe agregar el <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> en su VSPackage y usar como valor el nombre del menú o su identificador de recurso.  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Además, debe registrar el comando con el <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>. Puede obtener este servicio mediante el <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> método si se deriva el VSPackage <xref:Microsoft.VisualStudio.Shell.Package>.  
  
```  
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
if ( null != mcs )  
{  
    // Create the command for the menu item.  
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);  
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );  
    mcs.AddCommand( menuItem );  
}  
  
```  
  
## <a name="implementing-commands"></a>Implementación de comandos  
 Hay varias maneras de implementar los comandos. Si desea que un comando de menú estático, que es un comando que aparece siempre la misma manera y en el mismo menú, crear el comando mediante <xref:System.ComponentModel.Design.MenuCommand> tal como se muestra en los ejemplos en la sección anterior. Para crear un comando estático, debe proporcionar un controlador de eventos que se encarga de ejecutar el comando. Dado que el comando siempre está habilitado y visible, no es necesario que proporcionar su estado a Visual Studio. Si desea cambiar el estado de un comando según ciertas condiciones, puede crear el comando como una instancia de la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> clase y, en su constructor, proporcione un controlador de eventos para ejecutar el comando y un controlador de estado de la consulta para notificar al objeto Visual Studio cuando cambia el estado del comando. También puede implementar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> como parte de una clase de comando o puede implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> si va a proporcionar un comando como parte de un proyecto. Las dos interfaces y <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> todas las clases tienen métodos que notifiquen a Visual Studio de un cambio en el estado de un comando y otros métodos que proporcionan la ejecución del comando.  
  
 Cuando se agrega un comando al servicio de comandos, se convierte en uno de una cadena de comandos. Al implementar los métodos de notificación y la ejecución del estado del comando, tenga cuidado para proporcionar solo para ese comando concreto y para pasar todos los demás casos en los otros comandos de la cadena. Si no puede pasar el comando (normalmente devolviendo <xref:Microsoft.VisualStudio.OLE.Interop.Constants>), Visual Studio pueden dejar de funcionar correctamente.  
  
## <a name="query-status-methods"></a>Métodos de estado de consulta  
 Si va a implementar ya sea el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método o la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> método, busque el GUID del comando conjunto al que pertenece el comando y el identificador del comando. Siga estas instrucciones:  
  
- Si no se reconoce el GUID, la implementación de cualquiera de estos métodos debe devolver <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
- Si su implementación de cualquiera de estos métodos reconoce el GUID pero no ha implementado realmente el comando, el método debe devolver <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
- Si su implementación de cualquiera de estos métodos reconoce el GUID y el comando y, después, el método debe establecer el campo de marcadores de comando de todos los comandos (en el `prgCmds` parámetro) mediante el uso de las marcas siguientes:  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si se admite el comando.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si el comando no debe estar visible.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si el comando se alterna y parece que se han comprobado.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si el comando está habilitado.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si se debe ocultar el comando si ésta aparece en un menú contextual.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si el comando es un controlador de menú y no está habilitado, pero su lista del menú desplegable no está vacía y sigue estando disponible. (Rara vez se usa esta marca).  
  
- Si el comando se definió en el archivo .vsct con el `TextChanges` marca, establezca los parámetros siguientes:  
  
  -   Establecer el `rgwz` elemento de la `pCmdText` parámetro para el nuevo texto del comando.  
  
  -   Establecer el `cwActual` elemento de la `pCmdText` parámetro para el tamaño de la cadena de comandos.  
  
  Además, asegúrese de que el contexto actual no es una función de automatización, a menos que el comando está diseñado específicamente para controlar las funciones de automatización.  
  
  Para indicar que admite un comando concreto, devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Para todos los otros comandos, devolver <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
  En el ejemplo siguiente, el método de estado de la consulta primero se asegura que el contexto no es una función de automatización, a continuación, busca el GUID de conjunto de comandos correcto y el identificador de comando. El propio comando se establece en habilitados y que se admiten. No se admite ningún otro comando.  
  
```  
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)  
        {  
            // make the Right command visible   
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;  
                return VSConstants.S_OK;  
            }  
        }  
        return Constants.OLECMDERR_E_NOTSUPPORTED;  
    }  
}  
  
```  
  
## <a name="execution-methods"></a>Métodos de ejecución  
 Implementación del método execute se asemeja a la implementación del método de estado de la consulta. En primer lugar, asegúrese de que el contexto no es una función de automatización. A continuación, pruebe el GUID y el identificador de comando. Si el GUID o no se reconoce el identificador de comando, devolver <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
 Para controlar el comando, ejecútelo y devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK> si la ejecución se realiza correctamente. El comando es responsable de la detección de errores y la notificación; por lo tanto, devolver un código de error si se produce un error en la ejecución. El ejemplo siguiente muestra cómo se debe implementar el método de ejecución.  
  
```  
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)  
        {  
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                //execute the command  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    return Constants.OLECMDERR_E_NOTSUPPORTED;  
}  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Adición de elementos de la interfaz de usuario por VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

