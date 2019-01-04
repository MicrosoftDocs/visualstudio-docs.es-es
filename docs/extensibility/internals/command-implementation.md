---
title: Implementación de comandos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea4240ddf84dc1b475adcf81fe80471c9d1bc2b9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53965426"
---
# <a name="command-implementation"></a>Implementación de comandos
Para implementar un comando en un VSPackage, debe realizar las siguientes tareas:  
  
1.  En el *.vsct* de archivos, configurar un grupo de comandos y, a continuación, agregue el comando a él. Para obtener más información, consulte [archivos de tabla (.vsct) de comandos de Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).
  
2.  Registrar el comando con Visual Studio.  
  
3.  Implementar el comando.  
    
Las siguientes secciones explican cómo registrar e implementar los comandos.  
  
## <a name="register-commands-with-visual-studio"></a>Comandos de registro con Visual Studio  
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
  
## <a name="implement-commands"></a>Implementar comandos  
 Hay varias maneras de implementar los comandos. Si desea que un comando de menú estático, que es un comando que aparece siempre la misma manera y en el mismo menú, crear el comando mediante <xref:System.ComponentModel.Design.MenuCommand> tal como se muestra en los ejemplos en la sección anterior. Para crear un comando estático, debe proporcionar un controlador de eventos que se encarga de ejecutar el comando. Dado que el comando siempre está habilitado y visible, no es necesario que proporcionar su estado a Visual Studio. Si desea cambiar el estado de un comando según ciertas condiciones, puede crear el comando como una instancia de la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> clase y, en su constructor, proporcione un controlador de eventos para ejecutar el comando y un `QueryStatus` controlador para notificar al objeto Visual Studio cuando cambia el estado del comando. También puede implementar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> como parte de una clase de comando o puede implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> si va a proporcionar un comando como parte de un proyecto. Las dos interfaces y <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> todas las clases tienen métodos que notifiquen a Visual Studio de un cambio en el estado de un comando y otros métodos que proporcionan la ejecución del comando.  
  
 Cuando se agrega un comando al servicio de comandos, se convierte en uno de una cadena de comandos. Al implementar los métodos de notificación y la ejecución del estado del comando, tenga cuidado para proporcionar solo para ese comando concreto y para pasar todos los demás casos en los otros comandos de la cadena. Si no puede pasar el comando (normalmente devolviendo <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>), Visual Studio pueden dejar de funcionar correctamente.  
  
## <a name="querystatus-methods"></a>Métodos QueryStatus  
 Si va a implementar ya sea el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método o la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> método, busque el GUID del comando conjunto al que pertenece el comando y el identificador del comando. Siga estas instrucciones:  
  
-   Si no se reconoce el GUID, la implementación de cualquiera de estos métodos debe devolver <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>.  
  
-   Si su implementación de cualquiera de estos métodos reconoce el GUID pero no ha implementado el comando, el método debe devolver <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
-   Si su implementación de cualquiera de estos métodos reconoce el GUID y el comando y, después, el método debe establecer el campo de marcadores de comando de todos los comandos (en el `prgCmds` parámetro) mediante el siguiente <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> indicadores:  
  
    -   `OLECMDF_SUPPORTED`: Se admite el comando.  
  
    -   `OLECMDF_INVISIBLE`: El comando no debe ser visible.  
  
    -   `OLECMDF_LATCHED`: El comando se alterna y parece que se han comprobado.  
  
    -   `OLECMDF_ENABLED`: El comando está habilitado.  
  
    -   `OLECMDF_DEFHIDEONCTXTMENU`: El comando debe ocultarse si ésta aparece en un menú contextual.  
  
    -   `OLECMDF_NINCHED`: El comando es un controlador de menú y no está habilitado, pero su lista del menú desplegable no está vacía y sigue estando disponible. (Rara vez se usa esta marca).  
  
-   Si el comando se ha definido en el *.vsct* archivo con el `TextChanges` marca, establezca los parámetros siguientes:  
  
    -   Establecer el `rgwz` elemento de la `pCmdText` parámetro para el nuevo texto del comando.  
  
    -   Establecer el `cwActual` elemento de la `pCmdText` parámetro para el tamaño de la cadena de comandos.  
  

Además, asegúrese de que el contexto actual no es una función de automatización, a menos que el comando está diseñado específicamente para controlar las funciones de automatización.  
  
Para indicar que admite un comando concreto, devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Para todos los otros comandos, devolver <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
En el ejemplo siguiente, la `QueryStatus` método primero se asegura que el contexto no es una función de automatización, a continuación, busca el GUID de conjunto de comandos correcto y el identificador de comando. El propio comando se establece en habilitados y que se admiten. No se admite ningún otro comando.  
  
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
 Implementación de la `Exec` método es similar a la implementación de la `QueryStatus` método. En primer lugar, asegúrese de que el contexto no es una función de automatización. A continuación, comprobar el GUID y el identificador de comando. Si el GUID o no se reconoce el identificador de comando, devolver <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
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
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)