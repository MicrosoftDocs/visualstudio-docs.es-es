---
title: "Agregar un submen&#250; a un men&#250; | Microsoft Docs"
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
  - "menús contextuales"
  - "submenús, en cascada"
  - "submenús en cascada"
  - "menús, crear submenús en cascada"
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: 43
caps.handback.revision: 43
ms.author: "gregvanl"
manager: "ghogen"
---
# Agregar un submen&#250; a un men&#250;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tutorial se basa en la demostración en [Agregar un menú a la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) mostrándole cómo agregar un submenú a la **TestMenu** menú.  
  
 Un submenú es un menú secundario que aparece en otro menú. Un submenú puede identificarse por la flecha que sigue a su nombre. Haga clic en el nombre hace que el submenú y los comandos que se mostrará.  
  
 Este tutorial crea un submenú en un menú de la barra de menús de Visual Studio y coloca un nuevo comando en el submenú. El tutorial también implementa el nuevo comando.  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Agregar un submenú a un menú  
  
1.  Siga los pasos de [Agregar un menú a la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) para crear el elemento de menú y el proyecto. Los pasos de este tutorial se supone que es el nombre del proyecto VSIX `TopLevelMenu`.  
  
2.  Abra TestCommandPackage.vsct. En la `<Symbols>` sección, agregue un `<IDSymbol>` \(elemento\) para el submenú, uno para el grupo de submenú y otro para el comando, todo ello en el `<GuidSymbol>` nodo denominado "guidTopLevelMenuCmdSet." Éste es el mismo nodo que contiene el `<IDSymbol>` elemento de menú de nivel superior.  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  Agregar submenú recién creado para el `<Menus>` sección.  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     El par GUID o Id. del elemento primario especifica el grupo de menús que se generó en [Agregar un menú a la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), y es un elemento secundario del menú de nivel superior.  
  
4.  Agregar el grupo de menús definido en el paso 2 para el `<Groups>` sección y convertirlo en un elemento secundario del submenú.  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  Agregue un nuevo `<Button>` elemento a la `<Buttons>` sección para definir el comando creado en el paso 2 como un elemento en el submenú.  
  
    ```xml  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <Strings>  
           <CommandName>cmdidTestSubCommand</CommandName>  
           <ButtonText>Test Sub Command</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
6.  Compile la solución e iniciar la depuración. Debería ver la instancia experimental.  
  
7.  Haga clic en **TestMenu** para ver un submenú denominado **submenú**. Haga clic en **submenú** para abrir el submenú y ver un nuevo comando, **subcomando prueba**. Tenga en cuenta que al hacer clic **subcomando prueba** no hace nada.  
  
## Agregar un comando  
  
1.  Abra TestCommand.cs y agregue el siguiente identificador de comando después en el identificador de comando existente.  
  
    ```c#  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  Agregue el subcomando. Busque el constructor de comando. Agregue las siguientes líneas justo después de la llamada a la `AddCommand` \(método\).  
  
    ```c#  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     El `SubItemCallback` controlador de comandos se definirán más adelante. El constructor debe tener el siguiente aspecto:  
  
    ```c#  
    private TestCommand(Package package)  
            {  
                if (package == null)  
                {  
                    throw new ArgumentNullException("package");  
                }  
  
                this.package = package;  
  
                OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
                if (commandService != null)  
                {  
                    var menuCommandID = new CommandID(CommandSet, CommandId);  
                    var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);  
                    commandService.AddCommand(menuItem);  
                    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
                    MenuCommand subItem = new MenuCommand(  
                        new EventHandler(SubItemCallback), subCommandID);  
                    commandService.AddCommand(subItem);  
                }  
    ```  
  
3.  Agregar SubItemCallback\(\). Este es el método que se llama cuando se hace clic en el comando nuevo en el submenú.  
  
    ```c#  
    private void SubItemCallback(object sender, EventArgs e)  
    {  
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetService(  
            typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "TestCommand",  
            string.Format(CultureInfo.CurrentCulture,  
            "Inside TestCommand.SubItemCallback()",  
            this.ToString()),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result);  
    }  
    ```  
  
4.  Compile la solución y comience la depuración. Debe aparecer la instancia experimental.  
  
5.  En el **TestMenu** menú, haga clic en **submenú** y, a continuación, haga clic en **subcomando prueba**. Debería aparecer un cuadro de mensaje y se muestra el texto, "Comando de prueba dentro de TestCommand.SubItemCallback\(\)".  
  
## Vea también  
 [Agregar un menú a la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [Barras de herramientas, menús y comandos](../extensibility/internals/commands-menus-and-toolbars.md)