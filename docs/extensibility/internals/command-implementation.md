---
title: "Implementaci&#243;n de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comandos, implementación"
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Implementaci&#243;n de comandos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Para implementar un comando en un VSPackage, debe realizar las siguientes tareas:  
  
1.  En el archivo .vsct, configurar un grupo de comandos y, a continuación, agregue el comando a él. Para obtener más información, consulte [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2.  Registrar el comando con Visual Studio.  
  
3.  Implementar el comando.  
  
 Las siguientes secciones explican cómo registrar e implementar comandos.  
  
## Registrar los comandos con Visual Studio  
 Si el comando es aparecen en un menú, debe agregar el <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> a su VSPackage y utilice como valor el nombre del menú o su identificador de recurso.  
  
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
  
## Implementación de comandos  
 Hay varias maneras de implementar comandos. Si desea que un comando de menú estático, que es un comando que aparece siempre la misma forma y en el mismo menú, crear el comando mediante <xref:System.ComponentModel.Design.MenuCommand> tal como se muestra en los ejemplos de la sección anterior. Para crear un comando estático, debe proporcionar un controlador de eventos que se encarga de ejecutar el comando. Porque el comando siempre está visible y habilitado, no es necesario proporcionar su estado a Visual Studio. Si desea cambiar el estado de un comando según ciertas condiciones, puede crear el comando como una instancia de la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> clase y, en su constructor, proporcione un controlador de eventos para ejecutar el comando y un controlador de estado de la consulta para notificar a Visual Studio cuando cambia el estado del comando. También puede implementar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> como parte de una clase de comando o puede implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Si va a proporcionar un comando como parte de un proyecto. Las dos interfaces y <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> todas las clases tienen métodos que notifiquen a Visual Studio de un cambio en el estado de un comando y otros métodos que proporcionan la ejecución del comando.  
  
 Cuando se agrega un comando al servicio de comandos, se convierte en una parte de una cadena de comandos. Al implementar los métodos de notificación y ejecución de estado para el comando, tenga cuidado para proporcionar sólo para ese comando concreto y para pasar todos los demás casos en los comandos de la cadena. Si no puede pasar el comando \(normalmente devolviendo <xref:Microsoft.VisualStudio.OLE.Interop.Constants>\), Visual Studio puede dejar de funcionar correctamente.  
  
## Métodos de estado de consulta  
 Si va a implementar en el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> \(método\) o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> \(método\), compruebe que el GUID del conjunto al que pertenece el comando de comandos y el identificador del comando. Siga estas instrucciones:  
  
-   Si no se reconoce el GUID, la implementación de cualquier método debe devolver <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
-   Si la implementación de cualquier método reconoce el GUID, pero no ha implementado realmente el comando, el método debe devolver <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
-   Si la implementación de cualquier método reconoce el GUID y el comando, el método debe establecer el campo de indicadores de comando de cada comando \(en la `prgCmds` parámetro\) mediante el uso de los siguientes indicadores:  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si se admite el comando.  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si el comando no debe estar visible.  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si el comando se alterna y parece que se han comprobado.  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si el comando está habilitado.  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si el comando debe estar oculto si ésta aparece en un menú contextual.  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Si el comando es un controlador de menú y no está habilitado, pero la lista del menú desplegable no está vacía y sigue estando disponible. \(Esta marca se usa rara vez.\)  
  
-   Si el comando se ha definido en el archivo .vsct con el `TextChanges` marca, establezca los siguientes parámetros:  
  
    -   Establecer el `rgwz` elemento de la `pCmdText` parámetro para el nuevo texto del comando.  
  
    -   Establecer el `cwActual` elemento de la `pCmdText` parámetro para el tamaño de la cadena de comandos.  
  
 También asegúrese de que el contexto actual no es una función de automatización, a menos que el comando está diseñado específicamente para controlar las funciones de automatización.  
  
 Para indicar que se admite un comando concreto, devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Todos los demás comandos, devolver <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
 En el ejemplo siguiente, el método de estado de la consulta primero se asegura que el contexto no es una función de automatización, a continuación, busca el GUID de conjunto de comandos correcto y el identificador del comando. El comando se establece en habilitados y se admiten. No se admite ningún otro comando.  
  
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
  
## Métodos de ejecución  
 Implementación del método execute es similar a la implementación del método de estado de la consulta. En primer lugar, asegúrese de que el contexto no es una función de automatización. A continuación, pruebe el GUID y el identificador del comando. Si el GUID o no se reconoce el identificador de comando, devuelve <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
 Para controlar el comando, ejecutarlo y devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK> Si la ejecución se realiza correctamente. El comando es responsable de la detección de errores y la notificación; por lo tanto, devolver un código de error si se produce un error en la ejecución. En el ejemplo siguiente se muestra cómo se debe implementar el método de ejecución.  
  
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
  
## Vea también  
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)