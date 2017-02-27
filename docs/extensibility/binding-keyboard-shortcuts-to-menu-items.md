---
title: "M&#233;todos abreviados de teclado de enlace a elementos de men&#250; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comando de teclado"
  - "teclados"
  - "tecla de comando"
  - "métodos abreviados de teclado"
  - "elementos de menú"
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# M&#233;todos abreviados de teclado de enlace a elementos de men&#250;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para enlazar un método abreviado de teclado a un comando de menú personalizado, simplemente agregue una entrada para el archivo .vsct para el paquete. Este tema explica cómo asignar un método abreviado de teclado a un botón personalizado, un elemento de menú o un comando de barra de herramientas y cómo aplicar la asignación de teclado en el editor predeterminado o limitar a un editor personalizado.  
  
 Para asignar métodos abreviados de teclado a elementos de menú de Visual Studio existentes, consulte [Identificar y personalizar métodos abreviados de teclado](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## Elegir una combinación de teclas  
 Muchos métodos abreviados de teclado ya se utilizan en Visual Studio. No debe asignar el mismo acceso directo a más de un comando porque los enlaces duplicados son difíciles de detectar y también pueden producir resultados imprevisibles. Por lo tanto, es una buena idea comprobar la disponibilidad de un acceso directo antes de asignarlo.  
  
#### Para comprobar la disponibilidad de un método abreviado de teclado  
  
1.  En el **Herramientas \/ Opciones \/ entorno** ventana, seleccione **teclado**.  
  
2.  Asegúrese de que **Usar nuevo método abreviado en** está establecido en **Global**.  
  
3.  En el **presione las teclas de método abreviado** escriba el método abreviado de teclado que desea utilizar.  
  
     Si el método abreviado ya se utiliza en Visual Studio, el **método abreviado utilizado actualmente por** cuadro mostrará el comando que llama el acceso directo a actualmente.  
  
4.  Pruebe las diferentes combinaciones de claves hasta que encuentre uno que no está asignado.  
  
    > [!NOTE]
    >  Métodos abreviados de teclado que use ALT pueden abrir un menú y no directamente ejecutar un comando. Por lo tanto, el **método abreviado utilizado actualmente por** cuadro puede estar en blanco cuando se escribe un método abreviado que incluye ALT. Puede comprobar que el acceso directo no abre un menú cerrando el **opciones** cuadro de diálogo y, a continuación, presione las teclas.  
  
 El siguiente procedimiento se supone que tiene un VSPackage existente con un comando de menú. Si necesita ayuda sobre cómo hacerlo, eche un vistazo a [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### Para asignar un método abreviado de teclado a un comando  
  
1.  Abra el archivo .vsct para el paquete.  
  
2.  Crear vacío `<KeyBindings>` sección después de la `<Commands>` Si no está ya presente.  
  
    > [!WARNING]
    >  Para obtener más información acerca de los enlaces de teclado, consulte [Keybinding](../extensibility/keybinding-element.md).  
  
     En el `<KeyBindings>` debe crearse un `<KeyBinding>` entrada.  
  
     Establecer el `guid`  y  `id` atributos a los del comando que desea invocar.  
  
     Establecer el `mod1` atributo **Control**, **Alt**, o **MAYÚS**.  
  
     La sección de enlaces de teclado debe tener un aspecto similar al siguiente:  
  
    ```xml  
    <KeyBindings> <KeyBinding guid="<name of command set>" id="<name of command id>" editor="guidVSStd97" key1="1" mod1="CONTROL"/> </KeyBindings>  
  
    ```  
  
 Si el método abreviado de teclado requiere más de dos claves, establecer el `mod2` y `key2` atributos.  
  
 En la mayoría de las situaciones, **MAYÚS** no debe utilizarse sin un segundo modificador porque presionarlo ya hace que la mayoría de las teclas alfanumérica escriba una letra mayúscula o un símbolo.  
  
 Códigos de tecla virtual le permiten acceder a las teclas especiales que no tienen un carácter asociado a ellos, por ejemplo, las teclas de función y el **RETROCESO** clave. Para obtener más información, consulte [Virtual\-Key Codes](http://go.microsoft.com/fwlink/?LinkID=105932).  
  
 Para que el comando esté disponible en Visual Studio editor, establezca el `editor` atributo `guidVSStd97`.  
  
 Para que el comando esté disponible solo en un editor personalizado, establezca la `editor` de atributo en el nombre del editor personalizado que generó el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] plantilla de paquete cuando se crea el paquete VSPackage que incluye el editor personalizado. Para encontrar el valor de nombre, busque en la `<Symbols>` sección un `<GuidSymbol>` nodo cuyo `name` atributo termina en "`editorfactory`." Este es el nombre del editor personalizado.  
  
## Ejemplo  
 Este ejemplo enlaza el método abreviado de teclado CTRL \+ ALT \+ C para un comando denominado `cmdidMyCommand` en un paquete denominado `MyPackage`.  
  
```  
<CommandTable> . . . <Commands> . . . </Commands> <KeyBindings> <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand" key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" /> </KeyBindings> . . . </CommandTable>  
```  
  
## Ejemplo  
 Este ejemplo enlaza el método abreviado de teclado CTL \+ B con un comando denominado `cmdidBold` en un proyecto denominado `TestEditor`. El comando está disponible sólo en el editor personalizado y no en otros editores.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## Vea también  
 [Comandos y menús de extensión](../extensibility/extending-menus-and-commands.md)