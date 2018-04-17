---
title: Agregar una lista a un submenú usados recientemente | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 67eb08feff5d8edd1251c8fcff09d8f148b51b96
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-most-recently-used-list-to-a-submenu"></a>Agregar una mayoría recientemente usados para un submenú
En este tutorial se basa en las demostraciones de [agregar un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md)y se muestra cómo agregar una lista dinámica a un submenú. La lista dinámica constituye la base para crear una lista usados más recientemente (MRU).  
  
 Una lista de menú dinámico comienza con un marcador de posición de un menú. Cada vez que se muestra el menú, el entorno de desarrollo integrado (IDE) de Visual Studio le pide el VSPackage para todos los comandos que se deben mostrar en el marcador de posición. Una lista dinámica puede estar en cualquier lugar en un menú. Sin embargo, listas dinámicas normalmente se almacenan y se muestran por sí solas o en submenús o en la parte inferior de los menús. Mediante el uso de estos patrones de diseño, habilite la lista de comandos para expandir y contraer sin que afecte a la posición de otros comandos del menú dinámica. En este tutorial, se muestra la lista de elementos utilizados Recientemente dinámica en la parte inferior de un submenú existente, separada del resto del submenú por una línea.  
  
 Técnicamente, una lista dinámica también puede aplicarse a una barra de herramientas. Sin embargo, se desaconseja ese uso porque una barra de herramientas debe permanecer sin cambios, a menos que el usuario lleva a cabo pasos específicos para cambiarlo.  
  
 Este tutorial crea una lista de elementos utilizados Recientemente de cuatro elementos que cambian su orden cada vez que una de ellas está seleccionada (el elemento seleccionado se mueve a la parte superior de la lista).  
  
 Para obtener más información sobre los menús y los archivos de vsct, consulte [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-an-extension"></a>Crear una extensión  
  
-   Siga los procedimientos de [agregar un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md) para crear el submenú en el que se ha modificado en los procedimientos siguientes.  
  
 Los procedimientos en este tutorial se supone que es el nombre de VSPackage `TopLevelMenu`, que es el nombre que se usa en [agregar un menú a la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).  
  
## <a name="creating-a-dynamic-item-list-command"></a>Crear un comando de la lista de elementos dinámicos  
  
1.  Abra TestCommandPackage.vsct.  
  
2.  En el `Symbols` sección, en la `GuidSymbol` nodo denominado guidTestCommandPackageCmdSet, agregue el símbolo de la `MRUListGroup` grupo y la `cmdidMRUList` de comandos, como se indica a continuación.  
  
    ```csharp  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  En la `Groups` sección, agregue el grupo declarado después de las entradas de grupo existente.  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  En la `Buttons` sección, agregue un nodo para representar el comando recién declarado, después de las entradas existentes de botón.  
  
    ```csharp  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"  
        type="Button" priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />  
        <CommandFlag>DynamicItemStart</CommandFlag>  
        <Strings>  
            <CommandName>cmdidMRUList</CommandName>  
            <ButtonText>MRU Placeholder</ButtonText>  
                </Strings>  
    </Button>  
    ```  
  
     El `DynamicItemStart` la marca permite que el comando para generarse de forma dinámica.  
  
5.  Compile el proyecto e iniciar la depuración para probar la presentación del nuevo comando.  
  
     En el **TestMenu** menú, haga clic en el submenú nuevo, **submenú**, para mostrar el nuevo comando, **marcador de posición de elementos utilizados Recientemente**. Después de implementa una lista de elementos utilizados Recientemente dinámica de comandos en el procedimiento siguiente, esta etiqueta de comando se reemplazará por esa lista cada vez que se abre el submenú.  
  
## <a name="filling-the-mru-list"></a>Rellenar la lista de elementos utilizados Recientemente  
  
1.  En TestCommandPackageGuids.cs, agregue las siguientes líneas después de los identificadores de comando existente en el `TestCommandPackageGuids` definición de clase.  
  
    ```csharp  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  En TestCommand.cs agregue la siguiente instrucción using.  
  
    ```csharp  
    using System.Collections;  
    ```  
  
3.  Agregue el código siguiente en el constructor TestCommand después de la última llamada AddCommand. El `InitMRUMenu` se definirá más adelante  
  
    ```csharp  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  Agregue el código siguiente en la clase TestCommand. Este código inicializa la lista de cadenas que representan los elementos que se mostrará en la lista de elementos utilizados Recientemente.  
  
    ```csharp  
    private int numMRUItems = 4;  
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;  
    private ArrayList mruList;  
  
    private void InitializeMRUList()  
    {  
        if (null == this.mruList)  
        {  
            this.mruList = new ArrayList();  
            if (null != this.mruList)  
            {  
                for (int i = 0; i < this.numMRUItems; i++)  
                {  
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,  
                        "Item {0}", i + 1));  
                }  
            }  
        }  
    }  
    ```  
  
5.  Después de la `InitializeMRUList` método, agregue el `InitMRUMenu` método. Esto inicializa los comandos de menú de la lista de elementos utilizados Recientemente.  
  
    ```csharp  
    private void InitMRUMenu(OleMenuCommandService mcs)  
    {  
        InitializeMRUList();  
        for (int i = 0; i < this.numMRUItems; i++)  
        {  
            var cmdID = new CommandID(  
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);  
            var mc = new OleMenuCommand(  
                new EventHandler(OnMRUExec), cmdID);  
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);  
            mcs.AddCommand(mc);  
        }  
    }  
    ```  
  
     Debe crear un objeto de comando de menú para todos los elementos posibles en la lista de elementos utilizados Recientemente. Las llamadas IDE el `OnMRUQueryStatus` método para cada elemento de la lista de elementos utilizados Recientemente hasta que no hay más elementos. En código administrado, la única forma de que el IDE para saber que no hay más elementos es crear primero todos los elementos posibles. Si lo desea, puede marcar elementos adicionales como no visibles en primero mediante `mc.Visible = false;` una vez creado el comando de menú. Estos elementos pueden, a continuación, hacerse visibles más adelante mediante el uso de `mc.Visible = true;` en el `OnMRUQueryStatus` método.  
  
6.  Después de la `InitMRUMenu` método, agregue las siguientes `OnMRUQueryStatus` método. Este es el controlador que establece el texto para cada elemento de elementos utilizados Recientemente.  
  
    ```csharp  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7.  Después de la `OnMRUQueryStatus` método, agregue las siguientes `OnMRUExec` método. Este es el controlador para seleccionar un elemento de elementos utilizados Recientemente. Este método mueve el elemento seleccionado a la parte superior de la lista y, a continuación, muestra el elemento seleccionado en un cuadro de mensaje.  
  
    ```csharp  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
                for (int i = MRUItemIndex; i > 0; i--)  
                {  
                    this.mruList[i] = this.mruList[i - 1];  
                }  
                this.mruList[0] = selection;  
                System.Windows.Forms.MessageBox.Show(  
                    string.Format(CultureInfo.CurrentCulture,  
                                  "Selected {0}", selection));  
            }  
        }  
    }  
  
    ```  
  
## <a name="testing-the-mru-list"></a>Pruebas de la lista de elementos utilizados Recientemente  
  
#### <a name="to-test-the-mru-menu-list"></a>Para probar la lista del menú MRU  
  
1.  Compile el proyecto e inicie la depuración  
  
2.  En el **TestMenu** menú, haga clic en **TestCommand invocar**. Esto muestra un cuadro de mensaje que indica que el comando se ha seleccionado.  
  
    > [!NOTE]
    >  Este paso es necesario para forzar el VSPackage para cargar y mostrar correctamente la lista de elementos utilizados Recientemente. Si omite este paso, no se muestra la lista de elementos utilizados Recientemente.  
  
3.  En el **menú prueba** menú, haga clic en **submenú**. Se muestra una lista de los cuatro elementos al final del submenú, por debajo de un separador. Al hacer clic en **elemento 3**, debe aparecer un cuadro de mensaje y se muestra el texto, "Selected Item 3". (Si no se muestra la lista de los cuatro elementos, asegúrese de que ha seguido las instrucciones que aparecen en el paso anterior.)  
  
4.  Vuelva a abrir el submenú. Tenga en cuenta que **elemento 3** está ahora en la parte superior de la lista y los demás elementos se hayan insertado una posición hacia abajo. Haga clic en **elemento 3** nuevo y observe que el cuadro de mensaje muestra "Selected Item 3", lo que indica que el texto se movió correctamente a la nueva posición junto con la etiqueta de comando.  
  
## <a name="see-also"></a>Vea también  
 [Adición dinámica de elementos de menú](../extensibility/dynamically-adding-menu-items.md)