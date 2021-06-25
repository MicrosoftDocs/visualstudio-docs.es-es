---
title: Enlazar métodos abreviados de teclado a elementos de menú | Microsoft Docs
description: Obtenga información sobre cómo asignar un método abreviado de Visual Studio a un botón personalizado, un elemento de menú o un comando de barra de herramientas para el editor predeterminado o un editor personalizado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a9591a7412b0bcaf506483a16a6660790df5f40
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900439"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Enlazar métodos abreviados de teclado a elementos de menú
Para enlazar un método abreviado de teclado a un comando de menú personalizado, basta con agregar una entrada al *archivo .vsct* del paquete. En este tema se explica cómo asignar un método abreviado de teclado a un botón personalizado, un elemento de menú o un comando de barra de herramientas, y cómo aplicar la asignación de teclado en el editor predeterminado o limitarla a un editor personalizado.

 Para asignar métodos abreviados de teclado a elementos de Visual Studio existentes, vea [Identificar y personalizar métodos abreviados de teclado.](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)

## <a name="choose-a-key-combination"></a>Elegir una combinación de teclas
 Muchos métodos abreviados de teclado ya se usan en Visual Studio. No debe asignar el mismo acceso directo a más de un comando porque los enlaces duplicados son difíciles de detectar y también pueden provocar resultados impredecibles. Por lo tanto, es una buena idea comprobar la disponibilidad de un acceso directo antes de asignarlo.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Para comprobar la disponibilidad de un método abreviado de teclado

1. En la **ventana Tools**  >  **Options**  >  **Environment (Entorno** de opciones de herramientas), seleccione **Keyboard (Teclado).**

2. Asegúrese de que **Usar nuevo acceso directo en** esté establecido en **Global.**

3. En el **cuadro Presionar teclas de método** abreviado, escriba el método abreviado de teclado que desea usar.

    Si el acceso directo ya se usa en Visual Studio, el cuadro **Acceso** directo usado actualmente por mostrará el comando al que el acceso directo llama actualmente.

4. Pruebe diferentes combinaciones de claves hasta que encuentre una que no esté asignada.

   > [!NOTE]
   > Los métodos abreviados de teclado **que usan Alt** pueden abrir un menú y no ejecutar directamente un comando. Por lo tanto, **el cuadro Acceso** directo usado actualmente por puede estar en blanco al escribir un acceso directo que incluya **Alt**. Para comprobar que el acceso directo no abre un menú, cierre el cuadro **de** diálogo Opciones y presione las teclas.

   En el procedimiento siguiente se da por supuesto que tiene un VSPackage existente con un comando de menú. Si necesita ayuda para ello, consulte Creación [de una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Para asignar un método abreviado de teclado a un comando

1. Abra el *archivo .vsct* del paquete.

2. Cree una sección `<KeyBindings>` vacía después de si aún no está `<Commands>` presente.

   > [!WARNING]
   > Para obtener más información sobre los enlaces de claves, vea [Keybinding](../extensibility/keybinding-element.md).

    En la `<KeyBindings>` sección , cree una `<KeyBinding>` entrada.

    Establezca los `guid`  atributos y en los del comando que desea  `id` invocar.

    Establezca el `mod1` atributo en **Control**, **Alt** o **Mayús.**

    La sección KeyBindings debe tener un aspecto parecido al siguiente:

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   Si el método abreviado de teclado requiere más de dos teclas, establezca los `mod2` atributos `key2` y .

   En la mayoría de las situaciones, No se debe usar **Mayús** sin un segundo modificador porque al presionarlo ya se hace que la mayoría de las teclas alfanuméricas escriban una letra mayúscula o un símbolo.

   Los códigos de clave virtual permiten acceder a claves especiales que no tienen un carácter asociado, por ejemplo, las claves de función y la **tecla Retroceso.** Para obtener más información, vea [Códigos de clave virtual](/windows/desktop/inputdev/virtual-key-codes).

   Para que el comando esté disponible en el editor Visual Studio, establezca el `editor` atributo en `guidVSStd97` .

   Para que el comando esté disponible solo en un editor personalizado, establezca el atributo en el nombre del editor personalizado que generó la plantilla de paquete al crear el VSPackage que incluye el `editor` [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor personalizado. Para buscar el valor de nombre, busque en la sección un nodo `<Symbols>` cuyo atributo termine en `<GuidSymbol>` `name` `editorfactory` "." Este es el nombre del editor personalizado.

## <a name="example-1"></a>Ejemplo 1
 En este ejemplo se enlaza el método abreviado de **teclado Ctrl** + **Alt** + **C** a un comando denominado `cmdidMyCommand` en un paquete denominado `MyPackage` .

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

## <a name="example-2"></a>Ejemplo 2
 En este ejemplo se enlaza el método abreviado de **teclado Ctrl** + **B** a un comando denominado `cmdidBold` en un proyecto denominado `TestEditor` . El comando solo está disponible en el editor personalizado y no en otros editores.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>Consulta también
- [Extensión de menús y comandos](../extensibility/extending-menus-and-commands.md)
