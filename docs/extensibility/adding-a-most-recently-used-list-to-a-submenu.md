---
title: Adición de una lista a un submenú usados recientemente | Microsoft Docs
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
ms.openlocfilehash: 6d76cf493c20966a989d559b89da20cf5e24247e
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081340"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Agregar que una lista a un submenú usados recientemente
En este tutorial se basa en las demostraciones en [agregar un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md)y se muestra cómo agregar una lista dinámica a un submenú. La lista dinámica constituye la base para la creación de una lista de usados recientemente (MRU).  
  
 Una lista de menús dinámicos comienza con un marcador de posición en un menú. Cada vez que se muestra el menú, el entorno de desarrollo integrado (IDE) de Visual Studio le preguntará el VSPackage para todos los comandos que deben mostrarse en el marcador de posición. Una lista dinámica puede estar en cualquier lugar en un menú. Sin embargo, las listas dinámicas normalmente se almacenan y se muestran por sí mismos submenús o en la parte inferior de los menús. Mediante el uso de estos patrones de diseño, habilitar la lista de comandos para expandir y contraer sin que afecte a la posición de otros comandos del menú dinámico. En este tutorial, se muestra la lista MRU dinámico en la parte inferior de un submenú existente, separado del resto del submenú por una línea.  
  
 Técnicamente, una lista dinámica también se puede aplicar a una barra de herramientas. Sin embargo, ese uso se desaconseja porque una barra de herramientas debe permanecer sin cambios a menos que el usuario realiza los pasos específicos para cambiarlo.  
  
 En este tutorial se crea una lista MRU de cuatro elementos que cambiar su orden cada vez que uno de ellos está seleccionado (el elemento seleccionado se mueve a la parte superior de la lista).  
  
 Para obtener más información acerca de los menús y *.vsct* archivos, consulte [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="create-an-extension"></a>Crear una extensión  
  
-   Siga los procedimientos de [agregar un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md) para crear el submenú en el que se ha modificado en los procedimientos siguientes.  
  
 Los procedimientos en este tutorial se supone que es el nombre del VSPackage `TopLevelMenu`, que es el nombre que se usa en [agregar un menú en la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).  
  
## <a name="create-a-dynamic-item-list-command"></a>Crear un comando de la lista de elemento dinámico  
  
1.  Abra *TestCommandPackage.vsct*.  
  
2.  En el `Symbols` sección la `GuidSymbol` nodo denominado guidTestCommandPackageCmdSet, agregue el símbolo para el `MRUListGroup` grupo y el `cmdidMRUList` de comandos, como se indica a continuación.  
  
    ```csharp  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  En la `Groups` sección, agregue el grupo declarado después de las entradas existentes del grupo.  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  En la `Buttons` sección, agregue un nodo para representar el comando declarado recientemente, después de las entradas existentes de botón.  
  
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
  
     El `DynamicItemStart` marca habilita el comando que se va a generar dinámicamente.  
  
5.  Compilar el proyecto e iniciar la depuración para probar la presentación del nuevo comando.  
  
     En el **TestMenu** menú, haga clic en el submenú, **submenú**, para mostrar el nuevo comando **marcador de posición de MRU**. Después de implementa una lista dinámica de MRU de comandos en el procedimiento siguiente, la etiqueta de este comando se reemplazará por esa lista cada vez que se abre el submenú.  
  
## <a name="filling-the-mru-list"></a>Rellenar la lista MRU  
  
1.  En *TestCommandPackageGuids.cs*, agregue las líneas siguientes después de los identificadores de comando existente en el `TestCommandPackageGuids` definición de clase.  
  
    ```csharp  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  En *TestCommand.cs* agregue la siguiente instrucción using.  
  
    ```csharp  
    using System.Collections;  
    ```  
  
3.  Agregue el código siguiente en el constructor de comando de prueba después de la última llamada AddCommand. El `InitMRUMenu` se definirán más adelante  
  
    ```csharp  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  Agregue el código siguiente en la clase de comando de prueba. Este código inicializa la lista de cadenas que representan los elementos que se mostrará en la lista MRU.  
  
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
  
     Debe crear un objeto de comando de menú para todos los elementos posibles en la lista MRU. Las llamadas IDE el `OnMRUQueryStatus` método para cada elemento en la lista MRU hasta que no hay ningún elemento más. En código administrado, la única forma para el IDE a fin de saber que no hay ningún elemento más es crear primero todos los elementos posibles. Si lo desea, puede marcar los elementos adicionales como no visible en primero mediante el uso de `mc.Visible = false;` una vez creado el comando de menú. Estos elementos, a continuación, se pueden hacer visibles más adelante mediante el uso de `mc.Visible = true;` en el `OnMRUQueryStatus` método.  
  
6.  Después de la `InitMRUMenu` método, agregue las siguientes `OnMRUQueryStatus` método. Este es el controlador que establece el texto para cada elemento MRU.  
  
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
  
7.  Después de la `OnMRUQueryStatus` método, agregue las siguientes `OnMRUExec` método. Este es el controlador para seleccionar un elemento MRU. Este método mueve el elemento seleccionado en la parte superior de la lista y, a continuación, muestra el elemento seleccionado en un cuadro de mensaje.  
  
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
  
## <a name="testing-the-mru-list"></a>Las pruebas de la lista MRU  
  
1.  Compile la solución y comience la depuración.
  
2.  En el **TestMenu** menú, haga clic en **invocar comando de prueba**. Esto muestra un cuadro de mensaje que indica que el comando se ha seleccionado.  
  
    > [!NOTE]
    >  Este paso es necesario para forzar el VSPackage para cargar y mostrar correctamente la lista MRU. Si omite este paso, no se muestra la lista MRU.  
  
3.  En el **menú prueba** menú, haga clic en **submenú**. Se muestra una lista de los cuatro elementos al final del submenú, a continuación un separador. Al hacer clic en **elemento 3**, debe aparecer un cuadro de mensaje y se muestra el texto, **seleccionado elemento 3**. (Si no se muestra la lista de los cuatro elementos, asegúrese de que ha seguido las instrucciones que aparecen en el paso anterior.)  
  
4.  Vuelva a abrir el submenú. Tenga en cuenta que **elemento 3** está ahora en la parte superior de la lista y los demás elementos se han insertado una posición hacia abajo. Haga clic en **elemento 3** nuevo y tenga en cuenta que el cuadro de mensaje todavía muestra **seleccionado elemento 3**, lo que indica que el texto se ha movido correctamente a la nueva posición junto con la etiqueta del comando.  
  
## <a name="see-also"></a>Vea también  
 [Agregar dinámicamente elementos de menú](../extensibility/dynamically-adding-menu-items.md)