---
title: Enlazar métodos abreviados de teclado a elementos de menú | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: db02cf763ee4bf171d862129c88687accab00cc4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>Métodos abreviados de teclado de enlace a elementos de menú
Para enlazar un método abreviado de teclado a un comando de menú personalizado, simplemente agregue una entrada para el archivo .vsct para el paquete. Este tema explica cómo asignar un método abreviado de teclado a un botón personalizado, un elemento de menú o un comando de barra de herramientas y cómo aplicar la asignación de teclado en el editor predeterminado o limitarlos a un editor personalizado.  
  
 Para asignar métodos abreviados de teclado para los elementos de menú de Visual Studio existentes, consulte [identificar y personalizar métodos abreviados de teclado](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choosing-a-key-combination"></a>Elegir una combinación de teclas  
 Muchos métodos abreviados de teclado ya se usan en Visual Studio. No debe asignar el mismo método abreviado a más de un comando porque los enlaces duplicados son difíciles de detectar y causar resultados imprevisibles. Por lo tanto, es una buena idea comprobar la disponibilidad de un acceso directo antes de asignarlo.  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Para comprobar la disponibilidad de un método abreviado de teclado  
  
1.  En el **herramientas / opciones / entorno** ventana, seleccione **teclado**.  
  
2.  Asegúrese de que **usar nuevo método abreviado en** está establecido en **Global**.  
  
3.  En el **presione las teclas de método abreviado** , escriba el método abreviado de teclado que desea utilizar.  
  
     Si el acceso directo ya se usa en Visual Studio, el **método abreviado utilizado actualmente por** cuadro mostrará el comando que llama el acceso directo a actualmente.  
  
4.  Probar diferentes combinaciones de claves hasta que encuentre uno que no está asignado.  
  
    > [!NOTE]
    >  Métodos abreviados de teclado que use ALT pueden abrir un menú y no directamente ejecutar un comando. Por lo tanto, la **método abreviado utilizado actualmente por** cuadro puede estar en blanco cuando se escribe un método abreviado que incluye ALT. Puede comprobar que el acceso directo no abre un menú cerrando la **opciones** cuadro de diálogo y, a continuación, presione las teclas.  
  
 El siguiente procedimiento se supone que dispone de un VSPackage existente con un comando de menú. Si necesita ayuda sobre cómo hacerlo, eche un vistazo a [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Para asignar un método abreviado de teclado a un comando  
  
1.  Abra el archivo .vsct para el paquete.  
  
2.  Crear vacío `<KeyBindings>` sección después de la `<Commands>` si todavía no está presente.  
  
    > [!WARNING]
    >  Para obtener más información acerca de los enlaces de teclado, consulte [Keybinding](../extensibility/keybinding-element.md).  
  
     En el `<KeyBindings>` , debe crearse un `<KeyBinding>` entrada.  
  
     Establecer el `guid` y `id` atributos a los del comando que desea invocar.  
  
     Establecer el `mod1` atribuir a **Control**, **Alt**, o **MAYÚS**.  
  
     La sección de enlaces de teclado debe tener un aspecto similar al siguiente:  
  
    ```xml  
    <KeyBindings>  
        <KeyBinding guid="<name of command set>" id="<name of command id>"  
            editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
    </KeyBindings>  
  
    ```  
  
 Si el método abreviado de teclado requiere más de dos claves, establezca el `mod2` y `key2` atributos.  
  
 En la mayoría de los casos, **MAYÚS** no debe usarse sin un segundo modificador porque presionarlo ya hace que la mayoría de las teclas alfanumérica escriba una letra mayúscula o un símbolo.  
  
 Códigos de tecla virtual le permiten acceder a las teclas especiales que no tienen un carácter asociado a ellos, por ejemplo, las teclas de función y la **retroceso** clave. Para obtener más información, consulte [códigos de tecla Virtual](http://go.microsoft.com/fwlink/?LinkID=105932).  
  
 Para que el comando esté disponible en Visual Studio editor, establezca el `editor` atribuir a `guidVSStd97`.  
  
 Para que el comando esté disponible solo en un editor personalizado, establezca la `editor` atributo por el nombre del editor personalizado que se generó el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] plantilla de paquete cuando se crea el VSPackage que incluye el editor personalizado. Para encontrar el valor del nombre, busque en el `<Symbols>` sección un `<GuidSymbol>` nodo cuyo `name` atributo termina en "`editorfactory`." Este es el nombre del editor personalizado.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo enlaza el método abreviado de teclado CTRL + ALT + C para un comando llamado `cmdidMyCommand` en un paquete denominado `MyPackage`.  
  
```  
<CommandTable>  
. . .  
<Commands>  
. . .  
</Commands>  
<KeyBindings>  
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"   
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />  
</KeyBindings>  
. . .  
</CommandTable>  
```  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo enlaza el método abreviado de teclado CTL + B con un comando llamado `cmdidBold` en un proyecto denominado `TestEditor`. El comando está disponible únicamente en el editor personalizado y no en otros editores.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>Vea también  
 [Ampliación de menús y comandos](../extensibility/extending-menus-and-commands.md)