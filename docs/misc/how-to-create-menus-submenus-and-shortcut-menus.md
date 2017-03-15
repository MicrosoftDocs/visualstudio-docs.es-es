---
title: "C&#243;mo: crear men&#250;s, submen&#250;s y men&#250;s contextuales | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "barras de comandos, arquitectura"
  - "menús, crear"
  - "menús, arquitectura"
  - "comandos, menús"
  - "menús"
ms.assetid: 62004fd9-7f99-4f00-8d01-1dde53e23dbb
caps.latest.revision: 46
caps.handback.revision: 46
manager: "douge"
---
# C&#243;mo: crear men&#250;s, submen&#250;s y men&#250;s contextuales
Para agregar un menú al entorno de desarrollo integrado \(IDE\) de Visual Studio, un paquete VSPackage debe usar la arquitectura de [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] para los menús de grupos de comandos. Un menú de grupos de comandos permite el uso compartido de los comandos por parte del IDE y los componentes. Para obtener más información sobre los menús de grupos de comandos, vea [Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 En los paquetes VSPackage, los menús se definen en la sección [Menús](../extensibility/menus-element.md) de un archivo .vsct. Un archivo .vsct define los menús, las barras de herramientas, los grupos y los comandos. Un comando hace referencia al elemento en el que un usuario hace clic para ejecutar una función. Un grupo es un contenedor de comandos. Un menú es un contenedor de grupos. Para crear un menú básico, debe crear un menú, un grupo de comandos y al menos un comando.  
  
 Hay tres maneras básicas para mostrar un menú en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   como un menú en la barra de menús principal;  
  
-   como un submenú de otro menú;  
  
-   como un menú contextual \(normalmente se muestra al hacer clic con el botón derecho\).  
  
 En este tema se describe cómo crear cada tipo de menú. Los siguientes tutoriales también muestran cómo hacerlo:  
  
-   [Agregar un menú a la barra de menús de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
  
-   [Agregar un submenú a un menú](../extensibility/adding-a-submenu-to-a-menu.md)  
  
-   [Agregar un menú contextual en una ventana de herramientas](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md)  
  
### Para crear un menú, un submenú o un menú contextual  
  
1.  En el proyecto, haga doble clic en el archivo .vsct para abrirlo en el editor.  
  
     Si el proyecto no tiene un archivo .vsct, agregue uno. Si crea un paquete mediante la plantilla de paquetes de Visual Studio, seleccione **Comando de menú**. Esto generará un archivo .vsct.  
  
2.  En la sección `Symbols`, busque el elemento [GuidSymbol](../extensibility/guidsymbol-element.md) que contiene los grupos y los comandos.  
  
3.  Cree un elemento [IDSymbol](../extensibility/idsymbol-element.md) para cada menú, grupo o comando que quiera agregar, como se muestra en el ejemplo siguiente.  
  
     [!CODE [ButtonGroup#01](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#01)]  
  
     Los atributos `name` de los elementos `IDSymbol` y `GuidSymbol` proporcionan el par GUID:ID para cada menú, grupo o comando nuevo.`GUID` representa un conjunto de comandos que se define para el VSPackage. Puede definir varios conjuntos de comandos. Cada par GUID:ID debe ser único.  
  
4.  Defina el nuevo menú en la sección `Menus`, como se explica a continuación:  
  
    1.  Defina los campos `guid` e `id` para que coincidan con el par GUID:ID del nuevo comando.  
  
    2.  Defina el atributo `priority`.  
  
         El archivo .vsct usa el atributo `priority` para determinar la ubicación del menú entre los objetos del grupo primario.  
  
         Los menús que tienen valores de menor prioridad se muestran antes de los menús que tienen valores de mayor prioridad. Se permiten valores de prioridad duplicados, pero la posición relativa de los menús que tienen la misma prioridad se determina por el orden en que se procesan los paquetes VSPackage en tiempo de ejecución y ese orden no se puede predeterminar. Si se omite el atributo `priority`, se define su valor en 0.  
  
         No establezca una prioridad para un menú contextual, porque su posición la determina el código que lo llama.  
  
    3.  En el caso de los menús y los submenús, establezca el atributo `type` en `Menu`, que describe un menú típico. En el caso de los menús contextuales, establezca el atributo `type` en `Context`.  
  
         Para obtener descripciones de otros tipos de menú válidos como, por ejemplo, controladores de menús y barras de herramientas, vea [Elemento de menú](../extensibility/menu-element.md).  
  
    4.  En la definición del menú, cree una sección [Cadenas](../extensibility/strings-element.md) que tenga un elemento [ButtonText](../extensibility/buttontext-element.md) para que contenga el nombre del menú que aparece en el IDE y un elemento [CommandName](../extensibility/commandname-element.md) para que contenga el nombre del comando que se usa para acceder al menú en la ventana **Comando**.  
  
         Si la cadena de texto del botón incluye el carácter '&', el usuario puede abrir el menú presionando la tecla ALT más el carácter inmediatamente posterior a '&'.  
  
    5.  Agregue marcadores de comando, según corresponda, para cambiar la apariencia y el comportamiento del menú. Para ello, agregue un elemento [CommandFlag](../extensibility/command-flag-element.md) en la definición de menú. Para obtener más información, consulte [Elemento de indicador de comando](../extensibility/command-flag-element.md).  
  
5.  Establezca el elemento primario del menú. Para un menú o un submenú estándar, haga esto en una de las formas siguientes, según el diseño:  
  
    -   En el elemento `Menu`, cree un elemento [Parent](../extensibility/parent-element.md) y defina sus campos `guid` e `id` para el par GUID:ID del grupo que va a hospedar el menú, también conocido como el *grupo principal primario*. El grupo primario puede ser un grupo que cree en la sección `Symbols`, un grupo de otro paquete o un grupo del IDE. Por ejemplo, para agregar el menú a la barra de menús de nivel superior del IDE, cerca del menú **Herramientas**, defina el elemento primario en guidSHLMainMenu:IDG\_VS\_MM\_TOOLSADDINS.  
  
         En el ejemplo siguiente se muestra un menú que aparecerá en la barra de menús de Visual Studio.  
  
         [!CODE [TopLevelMenu#01](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#01)]  
  
    -   Puede omitir el elemento `Parent` si el menú se va colocar mediante la ubicación del comando. Cree una sección [CommandPlacements](../extensibility/commandplacements-element.md) antes de la sección `Symbols` y agregue un elemento [CommandPlacement](../extensibility/commandplacement-element.md) que tenga el par GUID:ID del menú, una prioridad y un elemento primario, tal como se muestra en el ejemplo siguiente.  
  
         [!CODE [ButtonGroup#04](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#04)]  
  
         La creación de varias ubicaciones de comando que tienen los mismos GUID:ID pero diferentes objetos primarios hace que un menú aparezca en varias ubicaciones. Para obtener más información, consulte [Elemento CommandPlacements](../extensibility/commandplacements-element.md).  
  
     Un menú estándar debe tener un grupo en la barra de menús de Visual Studio como su elemento primario. Para un submenú, el elemento primario debe ser un grupo en otro menú \(o en una barra de herramientas u otro tipo de menú\). Para que se muestre un menú o un submenú, debe hospedar un grupo que contenga al menos un comando activo o debe tener establecido el marcador de comando `AlwaysCreate`.  
  
     Los menús contextuales no tienen elementos primarios o ubicaciones de comandos. En cambio, es necesario activarlos en el código. Normalmente, un menú contextual se activa en respuesta a un clic con el botón derecho en una superficie de control. En el ejemplo siguiente, se define un nuevo menú contextual.  
  
     [!CODE [ButtonGroup#06](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#06)]  
  
6.  En la sección [Grupos](../extensibility/groups-element.md) debe crear un elemento [Grupo](../extensibility/group-element.md) para que contenga los comandos que van a mostrarse en el menú. La sección `Symbols` debe incluir una entrada con el mismo GUID:ID que el nuevo elemento `Group`.  
  
    1.  Establezca la prioridad del grupo de modo que aparezca donde desee en el menú.  
  
         Los límites de cada grupo en el menú se mostrarán como líneas horizontales.  
  
    2.  Establezca el elemento primario de este nuevo grupo en el par GUID:ID del menú que ha creado. Esto coloca el grupo de comandos en el menú.  
  
     El grupo del ejemplo siguiente aparece en el menú de nivel superior que se mostró en un ejemplo anterior.  
  
     [!CODE [TopLevelMenu#02](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#02)]  
  
     Los menús pueden contener comandos y submenús. Un submenú \(también conocido como un menú en cascada\) es simplemente un menú, pero uno que se agrega al grupo de otro menú y se expone solo cuando se invoca ese otro menú. Al colocar el menú que se muestra en el siguiente ejemplo en un grupo del menú de nivel superior, se convierte en un submenú.  
  
     [!CODE [TopLevelMenu#06](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#06)]  
  
7.  Agregue comandos al menú mediante la creación de entradas de comandos en la sección [Botones](../extensibility/buttons-element.md) y defina el elemento primario de cada uno en el GUID:ID de su grupo. Cada elemento [Botón](../extensibility/button-element.md) debe tener un GUID:ID que corresponde a una entrada en la sección `Symbols`.  
  
     Use el atributo `priority` de cada entrada de botón para especificar el orden en que aparecen los comandos en el grupo.  
  
     En el ejemplo siguiente se define un comando que aparecerá en un menú de nivel superior.  
  
     [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  
  
     Para obtener más información sobre los botones y los elementos de menú, vea [Elemento Button](../extensibility/button-element.md).  
  
     Para obtener información sobre cómo implementar comandos de menú en el código, vea [MenuCommands frente a OleMenuCommands](../misc/menucommands-vs-olemenucommands.md) o los tutoriales mencionados más arriba en este tema.  
  
### Para activar un menú contextual  
  
1.  Obtenga el GUID:ID del menú contextual. De forma predeterminada, la plantilla de paquetes crea una clase `GuidList` en un archivo PkgCmdID.cs para contener el GUID del conjunto de comandos. La plantilla también crea una clase `PkgCmdIdList` en un archivo PkgCmdId.cs para contener los valores de identificador enteros de los comandos que se declaran en la plantilla. Los menús contextuales y los comandos adicionales se deben declarar una vez finalizada la plantilla. En los ejemplos siguientes se muestran estas declaraciones:  
  
     [!code-cs[TWShortcutMenu#12](../misc/codesnippet/CSharp/how-to-create-menus-submenus-and-shortcut-menus_8.cs)]  
  
     Este paso puede omitirse si se usarán directamente los valores de GUID y de ID. Sin embargo, se recomienda establecer los valores aquí para facilitar la lectura.  
  
2.  Asocie a un controlador de eventos. Por lo general, los menús contextuales se asocian al clic con el botón derecho de una superficie, tal como se muestra en el ejemplo siguiente.  
  
     [!code-cs[TWShortcutMenu#43](../misc/codesnippet/CSharp/how-to-create-menus-submenus-and-shortcut-menus_9.cs)]  
  
     El método <xref:System.Windows.Forms.Control.PointToScreen%2A> convierte la posición de clic, que es relativa al control, en una posición de pantalla. El método <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> muestra el menú contextual.  
  
     El archivo que contiene el controlador de eventos debe incluir el espacio de nombres <xref:System.ComponentModel.Design> para acceder a la clase <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> y el espacio de nombres <xref:Microsoft.VisualStudio.Shell> para acceder a la interfaz <xref:System.ComponentModel.Design.IMenuCommandService>.  
  
     [!code-cs[TWShortcutMenu#41](../misc/codesnippet/CSharp/how-to-create-menus-submenus-and-shortcut-menus_10.cs)]  
  
## Vea también  
 [MenuCommands frente a OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [Referencia del esquema XML de VSCT](../extensibility/vsct-xml-schema-reference.md)   
 [Comandos y menús de extensión](../extensibility/extending-menus-and-commands.md)