---
title: Enlace de atajos de teclado a elementos de menú ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94feafbc614be61aaa4eef9e26669c0fbe901ed5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740022"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Enlazar métodos abreviados de teclado a elementos de menú
Para enlazar un método abreviado de teclado a un comando de menú personalizado, simplemente agregue una entrada al archivo *.vsct* para el paquete. En este tema se explica cómo asignar un método abreviado de teclado a un botón personalizado, elemento de menú o comando de barra de herramientas, y cómo aplicar la asignación de teclado en el editor predeterminado o limitarla a un editor personalizado.

 Para asignar métodos abreviados de teclado a elementos de menú de Visual Studio existentes, vea [Identificar y personalizar métodos abreviados](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)de teclado .

## <a name="choose-a-key-combination"></a>Elija una combinación de teclas
 Muchos métodos abreviados de teclado ya se usan en Visual Studio. No debe asignar el mismo acceso directo a más de un comando porque los enlaces duplicados son difíciles de detectar y también pueden provocar resultados impredecibles. Por lo tanto, es una buena idea comprobar la disponibilidad de un acceso directo antes de asignarlo.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Para verificar la disponibilidad de un método abreviado de teclado

1. En la ventana**Entorno** de**opciones** > de **herramientas,** > seleccione **Teclado**.

2. Asegúrese de que **Usar nuevo acceso directo en** está establecido en **Global**.

3. En el cuadro Teclas de método abreviado de **prensa,** escriba el método abreviado de teclado que desea utilizar.

    Si el acceso directo ya se usa en Visual Studio, el cuadro **Acceso directo que se usa actualmente por** mostrará el comando al que llama actualmente el acceso directo.

4. Pruebe diferentes combinaciones de teclas hasta que encuentre una que no esté asignada.

   > [!NOTE]
   > Los métodos abreviados de teclado que utilizan **Alt** pueden abrir un menú y no ejecutar directamente un comando. Por lo tanto, el **cuadro Acceso directo utilizado actualmente puede** estar en blanco al escribir un acceso directo que incluya **Alt**. Puede comprobar que el acceso directo no abre un menú cerrando el cuadro de diálogo **Opciones** y, a continuación, presionando las teclas.

   En el procedimiento siguiente se supone que tiene un VSPackage existente con un comando de menú. Si necesita ayuda para hacerlo, eche un vistazo a [Crear una extensión con un comando](../extensibility/creating-an-extension-with-a-menu-command.md)de menú .

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Para asignar un método abreviado de teclado a un comando

1. Abra el archivo *.vsct* del paquete.

2. Cree una `<KeyBindings>` sección `<Commands>` vacía después de si aún no está presente.

   > [!WARNING]
   > Para obtener más información acerca de los enlaces de claves, vea [Enlace de claves](../extensibility/keybinding-element.md).

    En `<KeyBindings>` la sección, `<KeyBinding>` cree una entrada.

    Establezca `guid` los `id` atributos y en los del comando que desea invocar.

    Establezca `mod1` el atributo en **Control**, **Alt**o **Mayús**.

    La sección KeyBindings debería tener un aspecto similar al siguiente:

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   Si el método abreviado de teclado requiere `mod2` `key2` más de dos teclas, establezca los atributos y.

   En la mayoría de las situaciones, **Shift** no debe utilizarse sin un segundo modificador porque al presionarlo ya hace que la mayoría de las teclas alfanuméricas escriban una letra mayúscula o un símbolo.

   Los códigos de clave virtual le permiten acceder a claves especiales que no tienen un carácter asociado, por ejemplo, las teclas de función y la tecla **Retroceso.** Para obtener más información, consulte [Códigos de clave virtual](/windows/desktop/inputdev/virtual-key-codes).

   Para que el comando esté disponible en `editor` el `guidVSStd97`editor de Visual Studio, establezca el atributo en .

   Para que el comando solo esté disponible `editor` en un editor personalizado, establezca el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] atributo en el nombre del editor personalizado generado por la plantilla de paquete al crear el VSPackage que incluye el editor personalizado. Para encontrar el valor de `<Symbols>` nombre, `<GuidSymbol>` busque `name` en la`editorfactory`sección un nodo cuyo atributo termine en " ." Este es el nombre del editor personalizado.

## <a name="example"></a>Ejemplo
 En este ejemplo se enlaza el método `cmdidMyCommand` abreviado de `MyPackage`teclado **Ctrl**+**Alt**+**C** a un comando denominado en un paquete denominado .

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
 En este ejemplo se enlaza el método `cmdidBold` abreviado de `TestEditor`teclado **Ctrl**+**B** a un comando denominado en un proyecto denominado . El comando solo está disponible en el editor personalizado y no en otros editores.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>Vea también
- [Ampliación de menús y comandos](../extensibility/extending-menus-and-commands.md)
