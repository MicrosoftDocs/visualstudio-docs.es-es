---
title: Agregar una lista de usados más recientemente a un submenú | Microsoft Docs
description: Obtenga información sobre cómo agregar una lista dinámica que contenga los comandos de menú usados más recientemente a un submenú en el entorno de desarrollo integrado (IDE) de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bdff50655f846ced91e59a93a2d264bb06641ed1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951555"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Agregar una lista de usados más recientemente a un submenú
Este tutorial se basa en las demostraciones de [Agregar un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md)y muestra cómo agregar una lista dinámica a un submenú. La lista dinámica constituye la base para crear una lista de elementos usados más recientemente (MRU).

Una lista de menús dinámicos comienza con un marcador de posición en un menú. Cada vez que se muestra el menú, el entorno de desarrollo integrado (IDE) de Visual Studio solicita al VSPackage todos los comandos que se deben mostrar en el marcador de posición. Una lista dinámica puede aparecer en cualquier parte de un menú. Sin embargo, las listas dinámicas suelen almacenarse y mostrarse por sí mismas en submenús o en las parte inferior de los menús. Mediante el uso de estos patrones de diseño, se habilita la lista dinámica de comandos para expandir y contratar sin afectar a la posición de otros comandos en el menú. En este tutorial, la lista de MRU dinámicas se muestra en la parte inferior de un submenú existente, separada del resto del submenú por una línea.

Técnicamente, una lista dinámica también se puede aplicar a una barra de herramientas. Sin embargo, se desaconseja el uso porque una barra de herramientas debe permanecer sin cambios a menos que el usuario lleve a cabo pasos específicos para cambiarla.

En este tutorial se crea una lista MRU de cuatro elementos que cambian su orden cada vez que se selecciona uno de ellos (el elemento seleccionado se desplaza a la parte superior de la lista).

Para obtener más información sobre los menús y los archivos *. Vsct* , vea [comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Requisitos previos
Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea el [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="create-an-extension"></a>Creación de una extensión

- Siga los procedimientos que se indican en [Agregar un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md) para crear el submenú que se modifica en los procedimientos siguientes.

  En los procedimientos de este tutorial se supone que el nombre del VSPackage es `TestCommand` , que es el nombre que se usa en [Agregar un menú a la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).

## <a name="create-a-dynamic-item-list-command"></a>Crear un comando de lista de elementos dinámicos

1. Abra *TestCommandPackage. Vsct*.

2. En la `Symbols` sección, en el `GuidSymbol` nodo denominado guidTestCommandPackageCmdSet, agregue el símbolo del `MRUListGroup` grupo y el `cmdidMRUList` comando, como se indica a continuación.

    ```xml
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. En la `Groups` sección, agregue el grupo declarado después de las entradas de grupo existentes.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

4. En la `Buttons` sección, agregue un nodo para representar el comando recién declarado, después de las entradas de botón existentes.

    ```xml
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

    La `DynamicItemStart` marca permite que el comando se genere dinámicamente.

5. Compile el proyecto e inicie la depuración para probar la presentación del nuevo comando.

    En el menú **TestMenu** , haga clic en el nuevo submenú, **submenú**, para mostrar el nuevo comando, el **marcador de posición MRU**. Después de implementar una lista de comandos MRU dinámica en el procedimiento siguiente, esta etiqueta de comando se reemplazará por esa lista cada vez que se abra el submenú.

## <a name="filling-the-mru-list"></a>Rellenar la lista MRU

1. En *TestCommandPackageGuids.CS*, agregue las siguientes líneas después de los identificadores de comando existentes en la `TestCommandPackageGuids` definición de clase.

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. En *TestCommand.CS* , agregue la siguiente instrucción using.

    ```csharp
    using System.Collections;
    ```

3. Agregue el código siguiente en el constructor prueba después de la última llamada a AddCommand. Se `InitMRUMenu` definirá más adelante

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. Agregue el código siguiente en la clase prueba. Este código inicializa la lista de cadenas que representan los elementos que se van a mostrar en la lista MRU.

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

5. Después del `InitializeMRUList` método, agregue el `InitMRUMenu` método. Esto inicializa los comandos de menú de lista MRU.

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

    Debe crear un objeto de comando de menú para cada elemento posible de la lista MRU. El IDE llama al `OnMRUQueryStatus` método para cada elemento de la lista MRU hasta que no hay más elementos. En código administrado, la única manera de que el IDE sepa que no hay más elementos es crear todos los elementos posibles en primer lugar. Si lo desea, puede marcar elementos adicionales como no visibles al principio usando `mc.Visible = false;` después de crear el comando de menú. Estos elementos se pueden hacer visibles posteriormente mediante `mc.Visible = true;` en el `OnMRUQueryStatus` método.

6. Después del `InitMRUMenu` método, agregue el `OnMRUQueryStatus` método siguiente. Este es el controlador que establece el texto para cada elemento MRU.

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

7. Después del `OnMRUQueryStatus` método, agregue el `OnMRUExec` método siguiente. Este es el controlador para seleccionar un elemento MRU. Este método mueve el elemento seleccionado a la parte superior de la lista y, a continuación, muestra el elemento seleccionado en un cuadro de mensaje.

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

## <a name="testing-the-mru-list"></a>Prueba de la lista MRU

1. Compile la solución y comience la depuración.

2. En el menú **TestMenu** , haga clic en **invocar prueba**. Esto muestra un cuadro de mensaje que indica que se ha seleccionado el comando.

    > [!NOTE]
    > Este paso es necesario para forzar la carga del VSPackage y mostrar correctamente la lista MRU. Si omite este paso, no se muestra la lista MRU.

3. En el menú de **menú prueba** , haga clic en **submenú**. Se muestra una lista de cuatro elementos al final del submenú, debajo de un separador. Al hacer clic en el **elemento 3**, debe aparecer un cuadro de mensaje y mostrar el texto, el **elemento seleccionado 3**. (Si no se muestra la lista de cuatro elementos, asegúrese de que ha seguido las instrucciones del paso anterior).

4. Vuelva a abrir el submenú. Observe que el **elemento 3** está ahora en la parte superior de la lista y que los demás elementos se han insertado una posición hacia abajo. Vuelva a hacer clic en el **elemento 3** y observe que el cuadro de mensaje todavía muestra el **elemento seleccionado 3**, lo que indica que el texto se ha pasado correctamente a la nueva posición junto con la etiqueta del comando.

## <a name="see-also"></a>Vea también
- [Agregar elementos de menú de forma dinámica](../extensibility/dynamically-adding-menu-items.md)
