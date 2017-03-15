---
title: "Agregar una mayor&#237;a recientemente usados para un submen&#250; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "listas de MRU"
  - "menús, crear la lista de elementos utilizados Recientemente"
  - "usados más recientemente"
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
caps.latest.revision: 46
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 46
---
# Agregar una mayor&#237;a recientemente usados para un submen&#250;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tutorial se basa en las demostraciones de [Agregar un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md), y muestra cómo agregar una lista dinámica a un submenú. La lista dinámica constituye la base para crear una lista de archivos usados recientemente \(MRU\).  
  
 Una lista de menú dinámico se inicia con un marcador de posición de un menú. Cada vez que se muestra el menú, el entorno de desarrollo integrado \(IDE\) de Visual Studio pide el VSPackage todos los comandos que se deben mostrar en el marcador de posición. Una lista dinámica puede ocurrir en cualquier lugar en un menú. Sin embargo, las listas dinámicas normalmente se almacenan y se muestran por sí mismos submenús o en la parte inferior de los menús. Mediante el uso de estos patrones de diseño, habilite la lista dinámica de comandos para expandir y contraer sin que afecte a la posición de otros comandos del menú. En este tutorial, se muestra la lista dinámica de elementos utilizados Recientemente en la parte inferior de un submenú existente, separado del resto del submenú por una línea.  
  
 Técnicamente, una lista dinámica también puede aplicarse a una barra de herramientas. Sin embargo, se desaconseja, ya que el uso de porque una barra de herramientas debe permanecer sin cambios a menos que el usuario realice los pasos específicos para cambiarlo.  
  
 Este tutorial crea una lista de elementos utilizados Recientemente de cuatro elementos que cambiar su orden cada vez que uno de ellos está seleccionado \(el elemento seleccionado se mueve a la parte superior de la lista\).  
  
 Para obtener más información acerca de los menús y los archivos .vsct, vea [Barras de herramientas, menús y comandos](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulta [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Crear una extensión  
  
-   Siga los procedimientos de [Agregar un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md) para crear el submenú en el que se ha modificado en los procedimientos siguientes.  
  
 Los procedimientos de este tutorial se supone que es el nombre de VSPackage `TopLevelMenu`, que es el nombre que se usa en [Agregar un menú a la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).  
  
## Crear un comando de la lista de elementos dinámicos  
  
1.  Abra TestCommandPackage.vsct.  
  
2.  En la `Symbols` sección, en la `GuidSymbol` nodo denominado guidTestCommandPackageCmdSet, agregue el símbolo de la `MRUListGroup` grupo y el `cmdidMRUList` de comandos, como se indica a continuación.  
  
    ```c#  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  En la `Groups` sección, agregue el grupo declarado después de las entradas de grupo existente.  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  En la `Buttons` sección, agregue un nodo para representar el comando declarado recientemente, después de las entradas del botón existente.  
  
    ```c#  
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
  
     El `DynamicItemStart` la marca permite que el comando generar dinámicamente.  
  
5.  Compilar el proyecto e iniciar la depuración para probar la presentación del nuevo comando.  
  
     En el **TestMenu** menú, haga clic en el submenú, **submenú**, para mostrar el nuevo comando **marcador de posición de elementos utilizados Recientemente**. Después de una lista dinámica de MRU de comandos se implementa en el procedimiento siguiente, esta etiqueta de comando se reemplazará por esa lista cada vez que se abre el submenú.  
  
## Rellenar la lista de elementos utilizados Recientemente  
  
1.  En TestCommandPackageGuids.cs, agregue las siguientes líneas después de los identificadores de comando existentes en el `TestCommandPackageGuids` definición de clase.  
  
    ```c#  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  En TestCommand.cs, agregue la siguiente instrucción using.  
  
    ```c#  
    using System.Collections;  
    ```  
  
3.  Agregue el código siguiente en el constructor TestCommand después de la última llamada AddCommand. El `InitMRUMenu` se definirán más adelante  
  
    ```c#  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  Agregue el código siguiente en la clase TestCommand. Este código inicializa la lista de cadenas que representan los elementos que se van a mostrar en la lista de elementos utilizados Recientemente.  
  
    ```c#  
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
  
    ```c#  
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
  
     Debe crear un objeto de comando de menú para todos los elementos posibles en la lista de elementos utilizados Recientemente. Las llamadas IDE la `OnMRUQueryStatus` método para cada elemento de la lista de elementos utilizados Recientemente hasta que no hay más elementos. En código administrado, la única manera de saber que no hay ningún elemento más el IDE es crear primero de todos los elementos posibles. Si lo desea, puede marcar elementos adicionales como no visible en primero mediante `mc.Visible = false;` después de haber creado el comando de menú. Estos elementos pueden, a continuación, se hace visibles más adelante mediante `mc.Visible = true;` en la `OnMRUQueryStatus` \(método\).  
  
6.  Después de la `InitMRUMenu` \(método\), agregue las siguientes `OnMRUQueryStatus` método. Este es el controlador que establece el texto de cada elemento de utilizados más Recientemente.  
  
    ```c#  
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
  
7.  Después de la `OnMRUQueryStatus` \(método\), agregue las siguientes `OnMRUExec` método. Este es el controlador de selección de un elemento de utilizados más Recientemente. Este método mueve el elemento seleccionado en la parte superior de la lista y, a continuación, muestra el elemento seleccionado en un cuadro de mensaje.  
  
    ```c#  
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
  
## Pruebas de la lista de elementos utilizados Recientemente  
  
#### Para probar la lista del menú MRU  
  
1.  Compilar el proyecto e iniciar la depuración  
  
2.  En el **TestMenu** menú, haga clic en **invocar TestCommand**. Esto muestra un cuadro de mensaje que indica que se ha seleccionado el comando.  
  
    > [!NOTE]
    >  Este paso es necesario para forzar el VSPackage para cargar y mostrar correctamente la lista de elementos utilizados Recientemente. Si omite este paso, no se muestra la lista de elementos utilizados Recientemente.  
  
3.  En el **menú prueba** menú, haga clic en **submenú**. Se muestra una lista de los cuatro elementos al final del submenú, debajo de un separador. Al hacer clic en **elemento 3**, debería aparecer un cuadro de mensaje y se muestra el texto "elemento seleccionado 3". \(Si no se muestra la lista de los cuatro elementos, asegúrese de que ha seguido las instrucciones en el paso anterior.\)  
  
4.  Vuelva a abrir el submenú. Observe que **elemento 3** está ahora en la parte superior de la lista y los demás elementos se han insertado una posición hacia abajo. Haga clic en **elemento 3** nuevamente y observe que el cuadro de mensaje muestra "elemento seleccionado 3", que indica que el texto se ha movido correctamente a la nueva posición junto con la etiqueta del comando.  
  
## Vea también  
 [Agregar dinámicamente elementos de menú](../extensibility/dynamically-adding-menu-items.md)