---
title: "MenuCommands frente a OleMenuCommands | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comandos, crear en VSPackages"
  - "botones de comando, crear y colocar"
  - "menús, crear comandos"
ms.assetid: 553d5e07-3e19-4aba-b490-6c7dd05fd82e
caps.latest.revision: 46
caps.handback.revision: 46
manager: "douge"
---
# MenuCommands frente a OleMenuCommands
Puede crear comandos de menú mediante la derivación de los objetos <xref:System.ComponentModel.Design.MenuCommand> o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> e implementando los controladores de eventos apropiados. En la mayoría de los casos puede usar <xref:System.ComponentModel.Design.MenuCommand>, como hace la plantilla de proyecto de VSPackage, pero en ocasiones puede que deba usar <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>.  
  
 Los comandos que un VSPackage hace que estén disponibles para el IDE deben ser visibles y estar habilitados para que un usuario pueda usarlos. Cuando los comandos se crean en un archivo .vsct usando la plantilla de proyecto del paquete de Visual Studio, son visibles y están habilitados de forma predeterminada. La definición de algunos marcadores de comandos, como `DynamicItemStart`, puede cambiar el comportamiento predeterminado. La visibilidad, el estado habilitado y otras propiedades de un comando también pueden cambiarse en el código en tiempo de ejecución mediante el acceso al objeto <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> asociado con el comando.  
  
## Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulta [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Ubicaciones de plantillas para la plantilla del paquete de Visual Studio  
 Puede encontrar la plantilla de paquete de Visual Studio en el cuadro de diálogo **Nuevo proyecto** en **Visual Basic\/Extensibilidad**, **C\#\/Extensibilidad** u  **Otros tipos de proyectos\/Extensibilidad**.  
  
## Creación de un comando  
 Todos los comandos, los grupos de comandos, los menús, las barras de herramientas y las ventanas de herramientas se definen en el archivo .vsct. Para obtener más información, consulta [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Si va a crear un VSPackage mediante la plantilla de paquete, seleccione **Comando de menú** para crear un archivo .vsct y definir un comando de menú predeterminado. Para obtener más información, consulta [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### Para agregar un comando al IDE  
  
1.  Abra el archivo .vsct.  
  
2.  En la sección `Symbols`, busque el elemento [GuidSymbol](../extensibility/guidsymbol-element.md) que contiene los grupos y los comandos.  
  
3.  Cree un elemento [IDSymbol](../extensibility/idsymbol-element.md) para cada menú, grupo o comando que quiera agregar, como se muestra en el ejemplo siguiente.  
  
     [!CODE [ButtonGroup#01](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#01)]  
  
     Los atributos `name` de los elementos `GuidSymbol` y `IDSymbol` proporcionan el par GUID:ID para cada nuevo menú, grupo o comando. El valor `guid` representa un conjunto de comandos que se define para el VSPackage. Puede definir varios conjuntos de comandos. Cada par de GUID:ID debe ser único.  
  
4.  En la sección [Botones](../extensibility/buttons-element.md), cree un elemento [Button](../extensibility/button-element.md) para definir el comando, como se muestra en el ejemplo siguiente.  
  
     [!CODE [ButtonGroup#03](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#03)]  
  
    1.  Defina los campos `guid` y `id` de modo que coincidan con el par GUID:ID del nuevo comando.  
  
    2.  Defina el atributo `priority`.  
  
         El archivo .vsct usa el atributo `priority` para determinar la ubicación del botón entre los objetos de su grupo primario.  
  
         Los comandos que tienen valores de prioridad inferiores se muestran por encima o a la izquierda de los comandos que tienen valores de prioridad más altos. Se permiten valores de prioridad duplicados, pero la posición relativa de los comandos que tienen la misma prioridad se determina por el orden en que se procesan los VSPackages en tiempo de ejecución y ese orden no puede ser predeterminado.  
  
         Si se omite el atributo `priority`, se define su valor en 0.  
  
    3.  Defina el atributo `type`. En la mayoría de los casos, su valor será `"Button"`. Para obtener descripciones de otros tipos de botones válidos, consulte [Elemento Button](../extensibility/button-element.md).  
  
5.  En la definición del botón, cree un elemento [Strings](../extensibility/strings-element.md) que contenga un elemento [ButtonText](../extensibility/buttontext-element.md) para que contenga el nombre del menú que aparece en el IDE y un elemento [CommandName](../extensibility/commandname-element.md) para que contenga el nombre del comando que se usa para acceder al menú en la ventana **Comando**.  
  
     Si la cadena de texto del botón incluye el carácter '&', el usuario puede abrir el menú presionando la tecla ALT más el carácter inmediatamente posterior a '&'.  
  
     Agregar un elemento `Tooltip` hará que el texto contenido aparezca cuando un usuario desplace el puntero sobre el botón.  
  
6.  Agregue un elemento [Icon](../extensibility/icon-element.md) para especificar el icono, si existe, que se va a mostrar con el comando. Los iconos son necesarios para los botones de las barras de herramientas, pero no para los elementos de menú. El `guid` y el `id` del elemento `Icon` deben coincidir con los de un elemento [Bitmap](../extensibility/bitmap-element.md) definido en la sección `Bitmaps`.  
  
7.  Agregue marcadores de comando, según convenga, para cambiar la apariencia y el comportamiento del botón. Para ello, agregue un elemento [CommandFlag](../extensibility/command-flag-element.md) en la definición de menú.  
  
8.  Defina el grupo primario del comando. El grupo primario puede ser un grupo que cree, un grupo de otro paquete o un grupo del IDE. Por ejemplo, para agregar el comando a la barra de herramientas de edición de Visual Studio, junto a los botones **Comentario** y **Quitar comentario**, establezca el elemento primario en guidStdEditor:IDG\_VS\_EDITTOOLBAR\_COMMENT. Si el elemento primario es un grupo definido por el usuario, debe ser el elemento secundario de un menú, barra de herramientas o ventana de herramientas que aparece en el IDE.  
  
     Puede hacerlo de dos maneras, en función del diseño:  
  
    -   En el elemento `Button`, cree un elemento [Parent](../extensibility/parent-element.md) y defina sus campos `guid` y `id` en el Guid y el id. del grupo que va a hospedar el comando, también conocido como el *grupo principal primario*.  
  
         En el ejemplo siguiente se define un comando que aparecerá en un menú definido por el usuario.  
  
         [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  
  
    -   Puede omitir el elemento `Parent` si el comando se va colocar mediante la ubicación del comando. Cree un elemento [CommandPlacements](../extensibility/commandplacements-element.md) antes de la sección `Symbols` y agregue un elemento [CommandPlacement](../extensibility/commandplacement-element.md) que tenga el `guid` y `id` del comando, un elemento `priority`, y un elemento primario, tal como se muestra en el ejemplo siguiente.  
  
         [!CODE [ButtonGroup#04](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#04)]  
  
         La creación de varias ubicaciones de comando que tienen los mismos GUID:ID y tienen diferentes objetos primarios hace que un menú aparezca en varias ubicaciones. Para obtener más información, consulte el elemento [CommandPlacements](../extensibility/commandplacements-element.md).  
  
     Para obtener más información acerca de los grupos de comandos y la relación jerárquica, vea [Creación de grupos reutilizables de botones](../extensibility/creating-reusable-groups-of-buttons.md).  
  
 En este punto, el comando será visible en el IDE, pero no tendrá ninguna función. Si la plantilla de paquete ha creado el comando, tendrá de forma predeterminada un controlador de clic que muestre un mensaje.  
  
## Control del nuevo comando  
 La mayoría de los comandos del código administrado puede controlarse mediante Managed Package Framework \(MPF\) asociando el comando con un objeto <xref:System.ComponentModel.Design.MenuCommand> o un objeto <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> e implementando sus controladores de eventos.  
  
 Para el código que usa la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> directamente para el control de comandos, debe implementar la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> y sus métodos. Los dos métodos más importantes son <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> y <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>.  
  
1.  Obtenga la instancia <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>, como se muestra en el ejemplo siguiente.  
  
     [!code-cs[ButtonGroup#21](../misc/codesnippet/CSharp/menucommands-vs-olemenucommands_5.cs)]  
  
2.  Cree un objeto <xref:System.ComponentModel.Design.CommandID> que tenga como parámetros el GUID y el id. del comando que se va a controlar, como se muestra en el ejemplo siguiente.  
  
     [!code-cs[ButtonGroup#22](../misc/codesnippet/CSharp/menucommands-vs-olemenucommands_6.cs)]  
  
     La plantilla de paquete de Visual Studio proporciona dos colecciones, `GuidList` y `PkgCmdIDList`, para retener los GUID y los id. de comandos. Se rellenan automáticamente para los comandos que agrega la plantilla, pero para los comandos que agrega manualmente, también deberá agregar la entrada de id. a la clase `PkgCmdIdList`.  
  
     Como alternativa, puede rellenar el objeto <xref:System.ComponentModel.Design.CommandID> con el valor de cadena sin procesar del GUID y el valor entero del id.  
  
3.  Cree una instancia de un objeto <xref:System.ComponentModel.Design.MenuCommand> o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> que especifique el método que controla el comando junto con el <xref:System.ComponentModel.Design.CommandID>, como se muestra en el ejemplo siguiente.  
  
     [!code-cs[ButtonGroup#23](../misc/codesnippet/CSharp/menucommands-vs-olemenucommands_7.cs)]  
  
     <xref:System.ComponentModel.Design.MenuCommand> es adecuado para los comandos estáticos. Las visualizaciones de elementos de menú dinámicos necesitan controladores de eventos QueryStatus. El <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> agrega el evento <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>, que se produce cuando se abre el menú de host del comando y algunas otras propiedades, como <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     Los comandos creados por la plantilla de paquete se pasan de forma predeterminada a un objeto <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> en el método `Initialize()` de la clase de paquete.  
  
4.  <xref:System.ComponentModel.Design.MenuCommand> es adecuado para los comandos estáticos. Las pantallas de elementos de menú dinámicos necesitan controladores de eventos QueryStatus. El <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> agrega el evento <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>, que se produce cuando se abre el menú de host del comando y algunas otras propiedades, como <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     Los comandos creados por la plantilla de paquete se pasan de forma predeterminada a un objeto <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> en el método `Initialize()` de la clase de paquete. El Asistente para Visual Studio implementa el método `Initialize` usando `MenuCommand`. Para pantallas de elementos de menús dinámicos, debe cambiar este valor a `OleMenuCommand`, como se muestra en el paso siguiente. Además, para cambiar el texto del elemento de menú, debe agregar un marcador de comando TextChanges al botón de comando de menú en el archivo .vsct, como se muestra en el ejemplo siguiente.  
  
     [!CODE [MenuText#02](../CodeSnippet/VS_Snippets_VSSDK/menutext#02)]  
  
5.  Pase el nuevo comando de menú al método <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> en la interfaz <xref:System.ComponentModel.Design.IMenuCommandService>. Esto se consigue de forma predeterminada para los comandos creados por la plantilla de paquete, como se muestra en el ejemplo siguiente.  
  
     [!code-cs[ButtonGroup#24](../misc/codesnippet/CSharp/menucommands-vs-olemenucommands_9.cs)]  
  
6.  Implemente el método que controla el comando.  
  
#### Para implementar el evento QueryStatus  
  
1.  El evento QueryStatus se produce antes de que se muestre un comando. Esto permite definir las propiedades de ese comando en el controlador de eventos antes de que llegue al usuario. Solo los comandos que se agregan como objetos <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> pueden tener acceso a este método.  
  
     Agregue un objeto `EventHandler` al evento <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> en el objeto <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> creado para controlar el comando, como se muestra en el ejemplo siguiente \(`menuItem` es la instancia de <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>\).  
  
     [!code-cs[MenuText#14](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_10.cs)]
     [!code-vb[MenuText#14](../extensibility/codesnippet/VisualBasic/menucommands-vs-olemenucommands_10.vb)]  
  
     El objeto `EventHandler` recibe el nombre de un método que se llama cuando se consulta el estado del comando de menú.  
  
2.  Implemente el método de controlador de estado de consulta para el comando. El parámetro `object` `sender` se puede convertir en un objeto <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>, que se usa para establecer los distintos atributos del comando de menú, incluido el texto. En la tabla siguiente se muestran las propiedades de la clase <xref:System.ComponentModel.Design.MenuCommand> \(de la que se deriva la clase MPF <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>\) que corresponden a las marcas <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>.  
  
    |Propiedad MenuCommand|Marca OLECMDF|  
    |---------------------------|-------------------|  
    |<xref:System.ComponentModel.Design.MenuCommand.Checked%2A> \= `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
    |<xref:System.ComponentModel.Design.MenuCommand.Visible%2A> \= `false`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
    |<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> \= `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
  
     Para cambiar el texto de un comando de menú, use la propiedad <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> en el objeto <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>, como se muestra en el ejemplo siguiente.  
  
     [!code-cs[MenuText#11](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_11.cs)]
     [!code-vb[MenuText#11](../extensibility/codesnippet/VisualBasic/menucommands-vs-olemenucommands_11.vb)]  
  
 MPF controla automáticamente el caso de grupos no compatibles o desconocidos. A menos que se haya agregado un comando a <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> usando el método <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A>, no se admite el comando.  
  
### Control de comandos mediante la interfaz IOleCommandTarget  
 Para el código que usa la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> directamente, el VSPackage debe implementar los métodos <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> y <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> de la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>. Si el VSPackage implementa una jerarquía de proyectos, los métodos <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> de la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> se deben implementar en su lugar.  
  
 Los métodos <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> y <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> están diseñados para recibir un único `GUID` de conjunto de comandos y una matriz de ids. de comando como entrada. Se recomienda que los VSPackages sean totalmente compatibles con este concepto de varios ids. en una llamada. Sin embargo, siempre y cuando no se llame a un VSPackage desde otros VSPackages, se puede suponer que la matriz de comandos contiene un único id. de comando porque los métodos <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> y <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> se ejecutan en un orden bien definido. Para obtener más información sobre el enrutamiento, vea [Enrutamiento de comandos en VSPackages](../extensibility/internals/command-routing-in-vspackages.md).  
  
 Para el código que usa la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> directamente para el control de comandos, debe implementar el método <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> en el VSPackage como se indica a continuación para controlar comandos.  
  
##### Para implementar el método QueryStatus  
  
1.  Devuelva <xref:Microsoft.VisualStudio.VSConstants.S_OK> para comandos válidos.  
  
2.  Defina el elemento `cmdf` del parámetro `prgCmds`.  
  
     El valor del elemento `cmdf` es la unión lógica de valores de la enumeración <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>, combinados con el operador OR lógico \(`|`\).  
  
     Use la enumeración adecuada, según el estado del comando:  
  
    -   Si se admite el comando:  
  
         `prgCmds[0].cmdf = OLECMDF_SUPPORTED;`  
  
    -   Si el comando debe ser invisible por el momento:  
  
         `prgCmds[0].cmdf |= OLECMDF_INVISIBLE;`  
  
    -   Si se alterna el comando y parece como si se hubiera hecho clic en él:  
  
         `prgCmds[0].cmdf |= OLECMDF_LATCHED;`  
  
         En el caso de comandos de procesamiento que se hospedan en un menú de tipo `MenuControllerLatched`, el primer comando que está marcado con el marcador `OLECMDF_LATCHED` es el comando predeterminado que el menú muestra en el inicio. Para obtener más información sobre los tipos de menú `MenuController`, vea [Elemento de menú](../extensibility/menu-element.md).  
  
    -   Si el comando está habilitado actualmente:  
  
         `prgCmds[0].cmdf |= OLECMDF_ENABLED;`  
  
    -   Si el comando forma parte de un menú contextual y está oculto de forma predeterminada:  
  
         `prgCmds[0] cmdf |= OLECMDF_DEFHIDEONCTXMENU`  
  
    -   Si el comando usa la marca `TEXTCHANGES`, establezca el elemento `rgwz` del parámetro `pCmdText` en el nuevo texto del comando y establezca el elemento `cwActual` del parámetro `pCmdText` en el tamaño de la cadena de comandos.  
  
     Para condiciones de error, el método <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> debe controlar los casos de error siguientes:  
  
    -   Si el GUID es desconocido o no compatible, se devuelve `OLECMDERR_E_UNKNOWNGROUP`.  
  
    -   Si se conoce el GUID, pero el id. de comando es desconocido o no compatible, se devuelve `OLECMDERR_E_NOTSUPPORTED`.  
  
 La implementación del VSPackage del método <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> también debe devolver códigos de error específicos, en función de si se admite el comando y de si se controló correctamente.  
  
##### Para implementar el método Exec  
  
-   Si el comando `GUID` es desconocido, se devuelve `OLECMDERR_E_UNKNOWNGROUP`.  
  
-   Si el `GUID` es conocido, pero el id. de comando es desconocido, se devuelve `OLECMDERR_E_NOTSUPPORTED`.  
  
-   Si el `GUID` y el id. de comando coinciden con el par GID:ID que usa el comando en el archivo .vsct, se ejecuta el código que está asociado con el comando y se devuelve <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
## Vea también  
 [Referencia del esquema XML de VSCT](../extensibility/vsct-xml-schema-reference.md)   
 [Comandos y menús de extensión](../extensibility/extending-menus-and-commands.md)