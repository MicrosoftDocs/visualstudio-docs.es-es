---
title: "Agregar un controlador de men&#250; a una barra de herramientas | Microsoft Docs"
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
  - "barras de herramientas [Visual Studio], agregar controladores de menú"
  - "menús, agregar controladores de menús, barras de herramientas"
  - "controladores de menú, agregar barras de herramientas"
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: 38
caps.handback.revision: 38
ms.author: "gregvanl"
manager: "ghogen"
---
# Agregar un controlador de men&#250; a una barra de herramientas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tutorial se basa en el [Agregar una barra de herramientas a una ventana de herramientas](../extensibility/adding-a-toolbar-to-a-tool-window.md) tutorial y muestra cómo agregar un controlador de menú a la barra de herramientas de la ventana de herramienta. Los pasos que se muestran aquí también se pueden aplicar a la barra de herramientas que se crea en el [Agregar una barra de herramientas](../extensibility/adding-a-toolbar.md) tutorial.  
  
 Un controlador de menú es un control de expansión. El lado izquierdo de la controladora de menú muestra el comando utilizó por última vez y se puede ejecutar haciendo clic en él. El lado derecho del controlador de menú es una flecha que, al hacer clic, se abre una lista de comandos adicionales. Cuando haga clic en un comando en la lista, se ejecuta el comando, y reemplaza el comando en el lado izquierdo del controlador del menú. De este modo, el controlador del menú funciona como un botón de comando que siempre muestra el comando utilizó por última vez en una lista.  
  
 Controladores de menú pueden aparecer en los menús pero se suelen utilizar en barras de herramientas.  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Creación de un controlador de menú  
  
#### Para crear un controlador de menú  
  
1.  Siga los procedimientos descritos en [Agregar una barra de herramientas a una ventana de herramientas](../extensibility/adding-a-toolbar-to-a-tool-window.md) para crear una ventana de herramientas que tiene una barra de herramientas.  
  
2.  En TWTestCommandPackage.vsct, vaya a la sección de símbolos. En el elemento GuidSymbol denominado **guidTWTestCommandPackageCmdSet**, declare el controlador de menú, grupo de controladores de menú y tres elementos de menú.  
  
    ```xml  
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
    ```  
  
3.  En la sección de menús, después de la última entrada de menú, definir el controlador del menú como menú.  
  
    ```xml  
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <CommandFlag>TextChanges</CommandFlag>  
        <CommandFlag>TextIsAnchorCommand</CommandFlag>  
        <Strings>  
            <ButtonText>Test Menu Controller</ButtonText>  
            <CommandName>Test Menu Controller</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     El `TextChanges` y `TextIsAnchorCommand` marcas deben incluirse para habilitar el controlador de menú reflejar el último comando seleccionado.  
  
4.  En los grupos de sección, después de la última entrada de grupo, agregue el grupo controlador del menú.  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     Estableciendo el controlador de menú como elemento primario, los comandos que se colocan en este grupo aparecerá en el controlador del menú. El `priority` atributo se omite, que establece en el valor predeterminado de 0, ya que será el único grupo en el controlador del menú.  
  
5.  En la sección de botones, después de la última entrada de botón, agregue un elemento de botón para cada uno de los elementos de menú.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 1</ButtonText>  
            <CommandName>MC Item 1</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 2</ButtonText>  
            <CommandName>MC Item 2</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPicSearch" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 3</ButtonText>  
            <CommandName>MC Item 3</CommandName>  
        </Strings>  
    </Button>  
    ```  
  
6.  En este punto, puede mirar el controlador del menú. Compile la solución y comience la depuración. Debería ver la instancia experimental.  
  
    1.  En el **vista y otras ventanas** menú Abrir **ventana de herramientas de prueba**.  
  
    2.  El controlador del menú aparece en la barra de herramientas en la ventana de herramientas.  
  
    3.  Haga clic en la flecha situada en el lado derecho del controlador de menú para ver los tres comandos posibles.  
  
     Observe que al hacer clic en un comando, el título del controlador del menú cambia para mostrar ese comando. En la siguiente sección, agregaremos el código para activar estos comandos.  
  
## Implementar los comandos de menú controlador  
  
1.  En TWTestCommandPackageGuids.cs, agregue los identificadores de comando para los tres elementos de menú después los identificadores de comando existente.  
  
    ```c#  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  En TWTestCommand.cs, agregue el código siguiente en la parte superior de la clase TWTestCommand.  
  
    ```c#  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  En el constructor TWTestCommand, después de la última llamada a la `AddCommand` método, agregue código para enrutar los eventos para cada comando a través de los mismos controladores.  
  
    ```c#  
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=  
        TWTestCommandPackageGuids.cmdidMCItem3; i++)  
    {  
        CommandID cmdID = new  
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);  
        OleMenuCommand mc = new OleMenuCommand(new  
          EventHandler(OnMCItemClicked), cmdID);  
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);  
        commandService.AddCommand(mc);  
        // The first item is, by default, checked.   
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)  
        {  
            mc.Checked = true;  
            this.currentMCCommand = i;  
        }  
    }  
    ```  
  
4.  Agregue un controlador de eventos a la clase TWTestCommand para marcar el comando seleccionado como activado.  
  
    ```c#  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  Agregue un controlador de eventos que muestra un cuadro de mensaje cuando el usuario selecciona un comando en el controlador del menú:  
  
    ```c#  
    private void OnMCItemClicked(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            string selection;  
            switch (mc.CommandID.ID)  
            {  
                case c.cmdidMCItem1:  
                    selection = "Menu controller Item 1";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem2:  
                    selection = "Menu controller Item 2";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem3:  
                    selection = "Menu controller Item 3";  
                    break;  
  
                default:  
                    selection = "Unknown command";  
                    break;  
            }  
            this.currentMCCommand = mc.CommandID.ID;  
  
            IVsUIShell uiShell =  
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));  
            Guid clsid = Guid.Empty;  
            int result;  
            uiShell.ShowMessageBox(  
                       0,  
                       ref clsid,  
                       "Test Tool Window Toolbar Package",  
                       string.Format(CultureInfo.CurrentCulture,  
                                     "You selected {0}", selection),  
                       string.Empty,  
                       0,  
                       OLEMSGBUTTON.OLEMSGBUTTON_OK,  
                       OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
                       OLEMSGICON.OLEMSGICON_INFO,  
                       0,  
                       out result);  
        }  
    }  
    ```  
  
## Probar el controlador de menú  
  
1.  Compile la solución y comience la depuración. Debería ver la instancia experimental.  
  
2.  Abra la **ventana de herramientas de prueba** en el **vista y otras ventanas** menú.  
  
     El controlador del menú aparece en la barra de herramientas en la ventana de herramienta y muestra **MC elemento 1**.  
  
3.  Haga clic en el botón del controlador de menú a la izquierda de la flecha.  
  
     Debe ver tres elementos, el primero de que está seleccionado y tiene un cuadro resaltado alrededor de su icono. Haga clic en **MC elemento 3**.  
  
     Aparece un cuadro de diálogo con el mensaje **seleccionó controlador menú elemento 3**. Observe que el mensaje corresponde al texto en el botón controlador. Ahora se muestra el botón controlador **MC elemento 3**.  
  
## Vea también  
 [Agregar una barra de herramientas a una ventana de herramientas](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Agregar una barra de herramientas](../extensibility/adding-a-toolbar.md)