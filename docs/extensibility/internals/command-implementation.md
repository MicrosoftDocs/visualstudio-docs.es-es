---
title: Implementación de comandos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5ed14a65e2839039a9f5c3075dd68498c948a4fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133328"
---
# <a name="command-implementation"></a>Implementación de comandos
Para implementar un comando en un paquete VSPackage, debe realizar las siguientes tareas:  
  
1.  En el archivo .vsct, configure un grupo de comandos y, a continuación, agregue el comando a él. Para obtener más información, vea [tabla de comandos de Visual Studio (. Archivos Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2.  Registrar el comando con Visual Studio.  
  
3.  Implementar el comando.  
  
 Las siguientes secciones explican cómo registrar e implementar comandos.  
  
## <a name="registering-commands-with-visual-studio"></a>Registrar comandos con Visual Studio  
 Si el comando se va a aparecer en un menú, debe agregar el <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> al VSPackage y utilizarlo como un valor en el nombre del menú o en su identificador de recurso.  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Además, debe registrar el comando con el <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>. Puede obtener este servicio mediante el <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> método si el VSPackage se deriva de <xref:Microsoft.VisualStudio.Shell.Package>.  
  
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
 Hay varias maneras de implementar comandos. Si desea que un comando de menú estático, que es un comando que se muestre siempre la misma forma y en el mismo menú, crear el comando mediante <xref:System.ComponentModel.Design.MenuCommand> tal como se muestra en los ejemplos de la sección anterior. Para crear un comando estático, debe proporcionar un controlador de eventos que se encarga de ejecutar el comando. Dado que el comando siempre está habilitado y visible, no es necesario proporcionar su estado a Visual Studio. Si desea cambiar el estado de un comando según ciertas condiciones, puede crear el comando como una instancia de la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> clase y, en su constructor, proporcione un controlador de eventos para ejecutar el comando y un controlador de estado de la consulta para notificar Visual Studio cuando cambia el estado del comando. También puede implementar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> como parte de una clase de comando o puede implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> si va a proporcionar un comando como parte de un proyecto. Las dos interfaces y <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> todas las clases tienen métodos que notifiquen a Visual Studio de un cambio en el estado de un comando y otros métodos que proporcionan la ejecución del comando.  
  
 Cuando se agrega un comando al servicio de comandos, se convierte en uno de una cadena de comandos. Al implementar los métodos de notificación y la ejecución de estado para el comando, tenga cuidado para proporcionar solo para ese comando concreto y para pasar todos los demás casos en los otros comandos de la cadena. Si no puede pasar el comando (normalmente devolviendo <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>), Visual Studio puede dejar de funcionar correctamente.  
  
## <a name="query-status-methods"></a>Métodos de estado de consulta  
 Si está implementando en el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método o la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> método, busque el GUID del comando conjunto al que pertenece el comando y el identificador del comando. Siga estas instrucciones:  
  
-   Si no se reconoce el GUID, la implementación de cualquier método debe devolver <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>.  
  
-   Si su implementación de cualquiera de los métodos reconoce el GUID, pero no ha implementado el comando, el método debe devolver <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
-   Si su implementación de cualquiera de los métodos que reconoce el GUID y el comando, el método debe establecer el campo de marcadores de comando de todos los comandos (en el `prgCmds` parámetro) mediante la siguiente <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> marcas:  
  
    -   OLECMDF_SUPPORTED - si se admite el comando.  
  
    -   OLECMDF_INVISIBLE - si el comando no debería estar visible.  
  
    -   OLECMDF_LATCHED - si el comando se alterna y parece que se han comprobado.  
  
    -   OLECMDF_ENABLED - si el comando está habilitado.  
  
    -   OLECMDF_DEFHIDEONCTXTMENU - si el comando debe estar oculto si aparece en un menú contextual.  
  
    -   OLECMDF_NINCHED - si el comando es un controlador de menú y no está habilitado, pero su lista de menús de lista desplegable no está vacía y sigue estando disponible. (Rara vez se usa esta marca).  
  
-   Si el comando se ha definido en el archivo .vsct con el `TextChanges` marca, establezca los siguientes parámetros:  
  
    -   Establecer el `rgwz` elemento de la `pCmdText` parámetro para el nuevo texto del comando.  
  
    -   Establecer el `cwActual` elemento de la `pCmdText` parámetro para el tamaño de la cadena de comandos.  
  
 También asegúrese de que el contexto actual no es una función de automatización, a menos que el comando está pensado específicamente para controlar las funciones de automatización.  
  
 Para indicar que admite un comando concreto, devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Para todos los demás comandos, devolver <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
 En el ejemplo siguiente, el método de estado de la consulta primero se asegura que el contexto no es una función de automatización, a continuación, busca el GUID de conjunto de comandos correcto y el identificador del comando. El propio comando se establece en habilitado ni admite. No se admite ningún otro comando.  
  
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
 Implementación del método execute es similar a la implementación del método de estado de la consulta. En primer lugar, asegúrese de que el contexto no es una función de automatización. A continuación, pruebe el GUID y el identificador del comando. Si el GUID o no se reconoce el identificador de comando, devolver <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
 Para controlar el comando, ejecutarlo y devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK> si la ejecución se realiza correctamente. El comando es responsable de la detección de errores y la notificación; por lo tanto, devolver un código de error si se produce un error en la ejecución. En el ejemplo siguiente se muestra cómo se debe implementar el método de ejecución.  
  
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