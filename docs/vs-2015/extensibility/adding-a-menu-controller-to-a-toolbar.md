---
title: Agregar un controlador de menú a una barra de herramientas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: 39
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 28588f04119eea31dfb0f32beb3b78376aa1b6b3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996505"
---
# <a name="adding-a-menu-controller-to-a-toolbar"></a>Adición de un controlador de menú a una barra de herramientas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial se basa en el [agregar una barra de herramientas a una ventana de herramientas](../extensibility/adding-a-toolbar-to-a-tool-window.md) tutorial y muestra cómo agregar un controlador de menú a la ventana de herramientas. Los pasos indicados aquí también se pueden aplicar a la barra de herramientas que se crea en el [agregar una barra de herramientas](../extensibility/adding-a-toolbar.md) tutorial.  
  
 Un controlador de menú es un control de expansión. El lado izquierdo del controlador de menú muestra el comando de último uso, y se puede ejecutar haciendo clic en él. El lado derecho del controlador de menú es una flecha que, al hacer clic, se abre una lista de comandos adicionales. Cuando haga clic en un comando en la lista, se ejecuta el comando, y reemplaza el comando en el lado izquierdo del controlador de menú. De este modo, el controlador de menús funciona como un botón de comando que siempre se muestra el comando de último uso de una lista.  
  
 Controladores de menú pueden aparecer en los menús pero se suelen usar en las barras de herramientas.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-controller"></a>Creación de un controlador de menú  
  
#### <a name="to-create-a-menu-controller"></a>Para crear un controlador de menú  
  
1. Siga los procedimientos descritos en [agregar una barra de herramientas a una ventana de herramientas](../extensibility/adding-a-toolbar-to-a-tool-window.md) para crear una ventana de herramientas que tiene una barra de herramientas.  
  
2. En TWTestCommandPackage.vsct, vaya a la sección Symbols. En el elemento GuidSymbol denominado **guidTWTestCommandPackageCmdSet**, declare el controlador de menú, grupo de controladores de menú y tres elementos de menú.  
  
   ```xml  
   <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
   ```  
  
3. En la sección de menús, después de la última entrada de menú, definir el controlador de menú como menú.  
  
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
  
    El `TextChanges` y `TextIsAnchorCommand` marcas deben incluirse para habilitar el controlador de menús reflejar el último comando seleccionado.  
  
4. En los grupos de sección después de la última entrada de grupo, agregue el grupo de controlador de menú.  
  
   ```xml  
   <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
   </Group>  
   ```  
  
    Estableciendo el controlador de menús como elemento primario, los comandos que se colocan en este grupo aparecerá en el controlador de menús. El `priority` atributo se omite, que establece en el valor predeterminado de 0, ya que será el único grupo en el controlador de menús.  
  
5. En la sección de botones, después de la última entrada de botón, agregue un elemento de botón para cada uno de los elementos de menú.  
  
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
  
6. En este momento, puede mirar el controlador de menús. Compile la solución y comience la depuración. Debería ver la instancia experimental.  
  
   1. En el **vista / Windows otras** menú Abrir **ventana de herramientas de prueba**.  
  
   2. El controlador de menús aparece en la barra de herramientas en la ventana de herramientas.  
  
   3. Haga clic en la flecha situada en el lado derecho del controlador de menú para ver los tres comandos posibles.  
  
      Tenga en cuenta que, al hacer clic en un comando, el título del controlador de menú cambia para mostrar ese comando. En la siguiente sección, agregaremos el código para activar estos comandos.  
  
## <a name="implementing-the-menu-controller-commands"></a>Implementar los comandos del controlador de menú  
  
1.  En TWTestCommandPackageGuids.cs, agregue los identificadores de comando para los tres elementos de menú después del Id. de comando existente.  
  
    ```csharp  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  En TWTestCommand.cs, agregue el código siguiente en la parte superior de la clase TWTestCommand.  
  
    ```csharp  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  En el constructor TWTestCommand, después de la última llamada a la `AddCommand` método, agregue código para enrutar los eventos para cada comando a través de los mismos controladores.  
  
    ```csharp  
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
  
4.  Agregue un controlador de eventos a la clase TWTestCommand para marcar el comando seleccionado como comprobado.  
  
    ```csharp  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  Agregue un controlador de eventos que muestra un cuadro de mensaje cuando el usuario selecciona un comando en el controlador de menú:  
  
    ```csharp  
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
  
## <a name="testing-the-menu-controller"></a>Probar el controlador de menús  
  
1.  Compile la solución y comience la depuración. Debería ver la instancia experimental.  
  
2.  Abra el **ventana de herramientas de prueba** en el **vista / Windows otras** menú.  
  
     El controlador de menús aparece en la barra de herramientas en la ventana de herramientas y muestra **MC elemento 1**.  
  
3.  Haga clic en el botón de controlador de menú a la izquierda de la flecha.  
  
     Debería ver tres elementos, el primero de que está seleccionado y tiene un cuadro resaltado alrededor de su icono. Haga clic en **MC elemento 3**.  
  
     Aparece un cuadro de diálogo con el mensaje **seleccionó el controlador de menú elemento 3**. Tenga en cuenta que el mensaje se corresponde con el texto en el botón de controlador de menú. Ahora muestra el botón de menú controlador **MC elemento 3**.  
  
## <a name="see-also"></a>Vea también  
 [Agregar una barra de herramientas a una ventana de herramientas](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Adición de una barra de herramientas](../extensibility/adding-a-toolbar.md)
