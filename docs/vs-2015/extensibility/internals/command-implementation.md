---
title: Implementación de comandos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a208fabd3d205793763698cde0f6fe367c7bb8b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195056"
---
# <a name="command-implementation"></a>Implementación de comandos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Para implementar un comando en un VSPackage, debe realizar las siguientes tareas:  
  
1. En el archivo. Vsct, configure un grupo de comandos y, a continuación, agregue el comando a él. Para obtener más información, vea [tabla de comandos de Visual Studio (. Archivos de Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2. Registre el comando con Visual Studio.  
  
3. Implemente el comando.  
  
   En las secciones siguientes se explica cómo registrar e implementar comandos.  
  
## <a name="registering-commands-with-visual-studio"></a>Registrar comandos con Visual Studio  
 Si el comando va a aparecer en un menú, debe agregar el <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> a su VSPackage y usarlo como valor, ya sea el nombre del menú o su identificador de recurso.  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Además, debe registrar el comando con <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> . Puede obtener este servicio mediante el <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> método si el VSPackage se deriva de <xref:Microsoft.VisualStudio.Shell.Package> .  
  
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
  
## <a name="implementing-commands"></a>Implementar comandos  
 Hay varias maneras de implementar comandos. Si desea un comando de menú estático, que es un comando que siempre aparece de la misma manera y en el mismo menú, cree el comando con <xref:System.ComponentModel.Design.MenuCommand> como se muestra en los ejemplos de la sección anterior. Para crear un comando estático, debe proporcionar un controlador de eventos que sea responsable de ejecutar el comando. Dado que el comando está siempre habilitado y visible, no es necesario proporcionar su estado a Visual Studio. Si desea cambiar el estado de un comando en función de ciertas condiciones, puede crear el comando como una instancia de la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> clase y, en su constructor, proporcionar un controlador de eventos para ejecutar el comando y un controlador de estado de consulta para notificar a Visual Studio cuando cambia el estado del comando. También puede implementar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> como parte de una clase de comando o, puede implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> si proporciona un comando como parte de un proyecto. Las dos interfaces y la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> clase tienen métodos que notifican a Visual Studio de un cambio en el estado de un comando y otros métodos que proporcionan la ejecución del comando.  
  
 Cuando se agrega un comando al servicio de comandos, se convierte en una cadena de comandos. Cuando implemente los métodos de notificación de estado y ejecución para el comando, tenga cuidado de proporcionar solo para ese comando concreto y pasar todos los demás casos a los demás comandos de la cadena. Si no puede pasar el comando (normalmente devolviendo <xref:Microsoft.VisualStudio.OLE.Interop.Constants> ), Visual Studio puede dejar de funcionar correctamente.  
  
## <a name="query-status-methods"></a>Métodos de estado de consulta  
 Si va a implementar el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método o el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> método, compruebe el GUID del conjunto de comandos al que pertenece el comando y el identificador del comando. Siga estas instrucciones:  
  
- Si no se reconoce el GUID, la implementación de ambos métodos debe devolver <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
- Si su implementación de cualquier método reconoce el GUID pero no ha implementado realmente el comando, el método debe devolver <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
- Si la implementación de cualquier método reconoce el GUID y el comando, el método debe establecer el campo de marcas de comandos de cada comando (en el `prgCmds` parámetro) mediante las marcas siguientes:  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> es si se admite el comando.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si el comando no debe estar visible.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si el comando está activado y parece que se ha comprobado.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si el comando está habilitado.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si el comando debe ocultarse si aparece en un menú contextual.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si el comando es un controlador de menú y no está habilitado, pero la lista de menús desplegables no está vacía y sigue estando disponible. (Esta marca se usa con poca frecuencia).  
  
- Si el comando se definió en el archivo. Vsct con la `TextChanges` marca, establezca los parámetros siguientes:  
  
  - Establezca el `rgwz` elemento del `pCmdText` parámetro en el nuevo texto del comando.  
  
  - Establezca el `cwActual` elemento del `pCmdText` parámetro en el tamaño de la cadena de comando.  
  
  Asegúrese también de que el contexto actual no es una función de automatización, a menos que el comando esté diseñado específicamente para controlar las funciones de automatización.  
  
  Para indicar que se admite un comando determinado, devuelva <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Para el resto de comandos, devuelva <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
  En el ejemplo siguiente, el método Query-status se asegura primero de que el contexto no es una función de automatización y, a continuación, busca el GUID del conjunto de comandos y el ID. de comando correctos. El propio comando se establece para habilitarse y admitirse. No se admite ningún otro comando.  
  
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
 La implementación del método Execute es similar a la implementación del método Query-status. En primer lugar, asegúrese de que el contexto no es una función de automatización. A continuación, pruebe el GUID y el identificador de comando. Si no se reconoce el GUID o el identificador de comando, se devuelve <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
 Para controlar el comando, ejecútelo y devuelva <xref:Microsoft.VisualStudio.VSConstants.S_OK> si la ejecución se realiza correctamente. El comando es responsable de la detección de errores y la notificación. por lo tanto, devuelve un código de error si se produce un error en la ejecución. En el ejemplo siguiente se muestra cómo se debe implementar el método de ejecución.  
  
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
  
## <a name="see-also"></a>Consulte también  
 [Cómo VSPackages agrega elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
