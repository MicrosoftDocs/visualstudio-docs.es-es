---
title: Implementación de Comandos (Command Implementation) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c7a536120c81c154cf894717a2af6a4e048d56e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709581"
---
# <a name="command-implementation"></a>Implementación del comando
Para implementar un comando en un VSPackage, debe realizar las siguientes tareas:

1. En el archivo *.vsct,* configure un grupo de comandos y, a continuación, agréguele el comando. Para obtener más información, vea Archivos de tabla de [comandos de Visual Studio (.vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

2. Registre el comando con Visual Studio.

3. Implemente el comando.

En las secciones siguientes se explica cómo registrar e implementar comandos.

## <a name="register-commands-with-visual-studio"></a>Registrar comandos con Visual Studio
 Si el comando va a aparecer en <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> un menú, debe agregar el a su VSPackage y usar como un valor el nombre del menú o su identificador de recurso.

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 Además, debe registrar el <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>comando con el archivo . Puede obtener este servicio <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> mediante el método si el <xref:Microsoft.VisualStudio.Shell.Package>VSPackage se deriva de .

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
 Hay varias maneras de implementar comandos. Si desea un comando de menú estático, que es un comando que siempre aparece <xref:System.ComponentModel.Design.MenuCommand> de la misma manera y en el mismo menú, cree el comando utilizando como se muestra en los ejemplos de la sección anterior. Para crear un comando estático, debe proporcionar un controlador de eventos que sea responsable de ejecutar el comando. Dado que el comando siempre está habilitado y visible, no es necesario proporcionar su estado a Visual Studio. Si desea cambiar el estado de un comando en función de determinadas <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> condiciones, puede crear el comando como una instancia `QueryStatus` de la clase y, en su constructor, proporcionar un controlador de eventos para ejecutar el comando y un controlador para notificar a Visual Studio cuando cambie el estado del comando. También puede <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementar como parte de una clase <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> de comando o, puede implementar si está proporcionando un comando como parte de un proyecto. Las dos interfaces <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> y la clase tienen métodos que notifican a Visual Studio de un cambio en el estado de un comando y otros métodos que proporcionan la ejecución del comando.

 Cuando se agrega un comando al servicio de comandos, se convierte en uno de una cadena de comandos. Cuando implemente los métodos de notificación de estado y ejecución para el comando, tenga cuidado de proporcionar solo para ese comando en particular y pasar todos los demás casos a los demás comandos de la cadena. Si no pasa el comando (normalmente <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>devolviendo ), Visual Studio puede dejar de funcionar correctamente.

## <a name="querystatus-methods"></a>Métodos QueryStatus
 Si está implementando <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> método o el método, busque el GUID del conjunto de comandos al que pertenece el comando y el identificador del comando. Siga estas instrucciones:

- Si no se reconoce el GUID, la <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>implementación de cualquiera de los métodos debe devolver .

- Si la implementación de cualquiera de los métodos reconoce el GUID <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>pero no ha implementado el comando, el método debe devolver .

- Si la implementación de cualquiera de los métodos reconoce el GUID y el comando, `prgCmds` el método debe <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> establecer el campo command-flags de cada comando (en el parámetro) mediante las siguientes marcas:

  - `OLECMDF_SUPPORTED`: Se admite el comando.

  - `OLECMDF_INVISIBLE`: El comando no debe estar visible.

  - `OLECMDF_LATCHED`: El comando está activado y parece haber sido activado.

  - `OLECMDF_ENABLED`: El comando está habilitado.

  - `OLECMDF_DEFHIDEONCTXTMENU`: El comando debe estar oculto si aparece en un menú contextual.

  - `OLECMDF_NINCHED`: El comando es un controlador de menú y no está habilitado, pero su lista de menú desplegable no está vacía y todavía está disponible. (Esta bandera rara vez se utiliza.)

- Si el comando se definió en `TextChanges` el archivo *.vsct* con la marca, establezca los siguientes parámetros:

  - Establezca `rgwz` el elemento `pCmdText` del parámetro en el nuevo texto del comando.

  - Establezca `cwActual` el elemento `pCmdText` del parámetro en el tamaño de la cadena de comandos.

Además, asegúrese de que el contexto actual no es una función de automatización, a menos que el comando esté diseñado específicamente para controlar las funciones de automatización.

Para indicar que admite un <xref:Microsoft.VisualStudio.VSConstants.S_OK>comando determinado, devuelva . Para todos los <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>demás comandos, devuelva .

En el ejemplo `QueryStatus` siguiente, el método primero se asegura de que el contexto no es una función de automatización y, a continuación, busca el GUID del conjunto de comandos y el identificador de comando correctos. El comando en sí se establece para ser habilitado y soportado. No se admiten otros comandos.

```csharp
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
 La implementación del método es similar a la `Exec` implementación del `QueryStatus` método. En primer lugar, asegúrese de que el contexto no es una función de automatización. A continuación, pruebe el GUID y el identificador de comando. Si no se reconoce el GUID <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>o el identificador de comando, devuelva .

 Para controlar el comando, <xref:Microsoft.VisualStudio.VSConstants.S_OK> ejecútelo y devuelva si la ejecución se realiza correctamente. El comando es responsable de la detección y notificación de errores; por lo tanto, devuelva un código de error si se produce un error en la ejecución. En el ejemplo siguiente se muestra cómo se debe implementar el método de ejecución.

```csharp
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

- [Cómo VSPackages agregan elementos de interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
