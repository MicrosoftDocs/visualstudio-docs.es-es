---
title: Adición de una lista de usos más recientemente a un submenú Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf389c0da7ec0aafb6e47dae8f09ffdc3b1d1e4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740303"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Agregue una lista utilizada más recientemente a un submenú
Este tutorial se basa en las demostraciones de [Agregar un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md)y muestra cómo agregar una lista dinámica a un submenú. La lista dinámica constituye la base para crear una lista de uso más reciente (MRU).

Una lista de menús dinámicos comienza con un marcador de posición en un menú. Cada vez que se muestra el menú, el entorno de desarrollo integrado (IDE) de Visual Studio solicita el VSPackage para todos los comandos que se deben mostrar en el marcador de posición. Una lista dinámica puede aparecer en cualquier parte de un menú. Sin embargo, las listas dinámicas normalmente se almacenan y se muestran por sí mismas en los submenús o en la parte inferior de los menús. Mediante el uso de estos patrones de diseño, se habilita la lista dinámica de comandos para expandir y contraer sin afectar a la posición de otros comandos en el menú. En este tutorial, la lista MRU dinámica se muestra en la parte inferior de un submenú existente, separado del resto del submenú por una línea.

Técnicamente, una lista dinámica también se puede aplicar a una barra de herramientas. Sin embargo, desaconsejamos ese uso porque una barra de herramientas debe permanecer sin cambios a menos que el usuario tome pasos específicos para cambiarlo.

Este tutorial crea una lista MRU de cuatro elementos que cambian su orden cada vez que se selecciona uno de ellos (el elemento seleccionado se mueve a la parte superior de la lista).

Para obtener más información acerca de los menús y archivos *.vsct,* vea [Comandos, menús y barras](../extensibility/internals/commands-menus-and-toolbars.md)de herramientas .

## <a name="prerequisites"></a>Prerrequisitos
Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea SDK de [Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="create-an-extension"></a>Creación de una extensión

- Siga los procedimientos descritos en [Agregar un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md) para crear el submenú que se modifica en los procedimientos siguientes.

  Los procedimientos de este tutorial suponen `TopLevelMenu`que el nombre del VSPackage es , que es el nombre que se usa en Agregar un menú a la barra de [menús](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)de Visual Studio .

## <a name="create-a-dynamic-item-list-command"></a>Crear un comando de lista de elementos dinámicos

1. Abra *TestCommandPackage.vsct*.

2. En `Symbols` la sección, `GuidSymbol` en el nodo denominado guidTestCommandPackageCmdSet, agregue el símbolo para el `MRUListGroup` grupo y el `cmdidMRUList` comando, como se indica a continuación.

    ```csharp
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. En `Groups` la sección, agregue el grupo declarado después de las entradas de grupo existentes.

    ```cpp
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>

    ```

4. En `Buttons` la sección, agregue un nodo para representar el comando recién declarado, después de las entradas de botón existentes.

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

    El `DynamicItemStart` indicador permite que el comando se genere dinámicamente.

5. Compile el proyecto e inicie la depuración para probar la visualización del nuevo comando.

    En el menú **TestMenu** , haga clic en el nuevo submenú, **Submenú**, para mostrar el nuevo comando, **Marcador de posición MRU**. Después de implementar una lista dinámica de comandos MRU en el siguiente procedimiento, esta etiqueta de comando se reemplazará por esa lista cada vez que se abra el submenú.

## <a name="filling-the-mru-list"></a>Llenar la lista mRU

1. En *TestCommandPackageGuids.cs*, agregue las siguientes líneas después `TestCommandPackageGuids` de los ides de comando existentes en la definición de clase.

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. En *TestCommand.cs* agregue la siguiente instrucción using.

    ```csharp
    using System.Collections;
    ```

3. Agregue el código siguiente en el TestCommand constructor después de la última llamada AddCommand. El `InitMRUMenu` se definirá más adelante

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. Agregue el código siguiente en la clase TestCommand. Este código inicializa la lista de cadenas que representan los elementos que se mostrarán en la lista MRU.

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

5. Después `InitializeMRUList` del método, agregue el `InitMRUMenu` método. Esto inicializa los comandos del menú de lista MRU.

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

    Debe crear un objeto de comando de menú para cada elemento posible de la lista MRU. El IDE `OnMRUQueryStatus` llama al método para cada elemento de la lista MRU hasta que no hay más elementos. En el código administrado, la única manera de que el IDE sepa que no hay más elementos es crear primero todos los elementos posibles. Si lo desea, puede marcar elementos adicionales `mc.Visible = false;` como no visibles al principio mediante el uso después de crear el comando de menú. Estos elementos se pueden hacer `mc.Visible = true;` visibles más adelante mediante el `OnMRUQueryStatus` método.

6. Después `InitMRUMenu` del método, `OnMRUQueryStatus` agregue el siguiente método. Este es el controlador que establece el texto para cada elemento MRU.

    ```csharp
    private void OnMRUQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                menuCommand.Text = this.mruList[MRUItemIndex] as string;
            }
        }
    }
    ```

7. Después `OnMRUQueryStatus` del método, `OnMRUExec` agregue el siguiente método. Este es el controlador para seleccionar un elemento MRU. Este método mueve el elemento seleccionado a la parte superior de la lista y, a continuación, muestra el elemento seleccionado en un cuadro de mensaje.

    ```csharp
    private void OnMRUExec(object sender, EventArgs e)
    {
        var menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                string selection = this.mruList[MRUItemIndex] as string;
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

## <a name="testing-the-mru-list"></a>Prueba de la lista MRU

1. Compile la solución y comience la depuración.

2. En el menú **TestMenu** , haga clic en **Invocar TestCommand**. Al hacerlo, se muestra un cuadro de mensaje que indica que se ha seleccionado el comando.

    > [!NOTE]
    > Este paso es necesario para forzar el VSPackage para cargar y mostrar correctamente la lista MRU. Si omite este paso, no se muestra la lista MRU.

3. En el menú **Menú de prueba,** haga clic en **Submenú**. Se muestra una lista de cuatro elementos al final del submenú, debajo de un separador. Al hacer clic en **Elemento 3**, debe aparecer un cuadro de mensaje y mostrar el texto, Elemento **seleccionado 3**. (Si no se muestra la lista de cuatro elementos, asegúrese de haber seguido las instrucciones del paso anterior.)

4. Vuelva a abrir el submenú. Observe que el **elemento 3** está ahora en la parte superior de la lista y los otros elementos se han empujado hacia abajo una posición. Vuelva a hacer clic en **el elemento 3** y observe que el cuadro de mensaje sigue mostrando Elemento seleccionado **3**, lo que indica que el texto se ha movido correctamente a la nueva posición junto con la etiqueta de comando.

## <a name="see-also"></a>Vea también
- [Adición dinámica de elementos de menú](../extensibility/dynamically-adding-menu-items.md)
