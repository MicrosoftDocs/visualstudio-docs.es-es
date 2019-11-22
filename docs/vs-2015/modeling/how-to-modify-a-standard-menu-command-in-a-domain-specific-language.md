---
title: 'How to: Modify a Standard Menu Command in a Domain-Specific Language | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
ms.assetid: 9b9d8314-d0d8-421a-acb9-d7e91e69825c
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 989367d395abb56e4f57c4aa2694b5f4ef17fb6e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300868"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Cómo: Modificar comandos de menú estándar en lenguajes específicos de dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede modificar el comportamiento de algunos de los comandos estándar que se definen automáticamente en su DSL. For example, you could modify **Cut** so that it excludes sensitive information. Para ello, se invalidan los métodos en una clase de conjunto de comandos. Estas clases se definen en el archivo CommandSet.cs, en el proyecto DslPackage, y derivan de <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

 En resumen, para modificar un comando:

1. [Discover what commands you can modify](#what).

2. [Create a partial declaration of the appropriate command set class](#extend).

3. [Override the ProcessOnStatus and ProcessOnMenu methods](#override) for the command.

   En este tema se explica el procedimiento.

> [!NOTE]
> If you want to create your own menu commands, see [How to: Add a Command to the Shortcut Menu](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

## <a name="what"></a> What commands can you modify?

#### <a name="to-discover-what-commands-you-can-modify"></a>Para averiguar qué comandos puede modificar

1. In the `DslPackage` project, open `GeneratedCode\CommandSet.cs`. This C# file can be found in Solution Explorer as a subsidiary of `CommandSet.tt`.

2. Find classes in this file whose names end with "`CommandSet`", for example `Language1CommandSet` and `Language1ClipboardCommandSet`.

3. En cada clase de conjunto de comandos, escriba "`override`" seguido de un espacio. IntelliSense mostrará una lista de los métodos que puede invalidar. Cada comando tiene un par de métodos cuyos nombres comienzan por "`ProcessOnStatus`" y "`ProcessOnMenu`".

4. Anote qué clases de conjunto de comandos contiene el comando que quiere modificar.

5. Cierre el archivo sin guardar las ediciones.

    > [!NOTE]
    > Normalmente no debe editar los archivos que se han generado. Las ediciones se perderán la próxima vez que se generen los archivos.

## <a name="extend"></a> Extend the appropriate command set class
 Cree un nuevo archivo que contiene una declaración parcial de la clase de conjunto de comandos.

#### <a name="to-extend-the-command-set-class"></a>Para extender la clase de conjunto de comandos

1. En el Explorador de soluciones, en el proyecto DslPackage, abra la carpeta GeneratedCode, busque en CommandSet.tt y abra su archivo generado CommandSet.cs. Anote el espacio de nombres y el nombre de la primera clase que se define en él. Por ejemplo, puede que vea:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. In **DslPackage**, create a folder named **Custom Code**. In this folder, create a new class file named `CommandSet.cs`.

3. En el nuevo archivo, escriba una declaración parcial que tenga el mismo espacio de nombres y nombre que la clase parcial generada. Por ejemplo:

    ```
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Design;
    namespace Company.Language1 /* Make sure this is correct */
    { internal partial class Language1CommandSet { ...
    ```

     **Note** If you used the class file template to create the new file, you must correct both the namespace and the class name.

## <a name="override"></a> Override the command methods
 Most commands have two associated methods: The method with a name like `ProcessOnStatus`... determines whether the command should be visible and enabled. Se llama siempre que el usuario hace clic con el botón secundario en el diagrama, debe ejecutarse rápidamente y no realiza cambios. `ProcessOnMenu`... is called when the user clicks the command, and should perform the function of the command. Quizás quiera invalidar uno o los dos métodos.

### <a name="to-change-when-the-command-appears-on-a-menu"></a>Para cambiar cuándo aparece el comando en un menú
 Override the ProcessOnStatus... method. Este método debe establecer las propiedades Visible y Enabled de su parámetro MenuCommand. Normalmente, el comando busca en this.CurrentSelection para determinar si se aplica a los elementos seleccionados, y también podría buscar en sus propiedades para determinar si se puede aplicar en el estado actual de las mismas.

 Como regla general, la propiedad Visible se debe determinar en función de qué elementos están seleccionados. La propiedad Enabled, que determina si el comando aparece en negro o en gris en el comando, dependerá del estado actual de la selección.

 En el ejemplo siguiente se deshabilita el elemento de menú Delete cuando el usuario selecciona más de una forma.

> [!NOTE]
> Este método no afecta a si el comando está disponible presionando una tecla. Por ejemplo, deshabilitar el elemento de menú Delete no impide que el comando se invoque desde la tecla Suprimir.

```
/// <summary>
/// Called when user right-clicks on the diagram or clicks the Edit menu.
/// </summary>
/// <param name="command">Set Visible and Enabled properties.</param>
protected override void ProcessOnStatusDeleteCommand (MenuCommand command)
{
  // Default settings from the base method.
  base.ProcessOnStatusDeleteCommand(command);
  if (this.CurrentSelection.Count > 1)
  {
    // If user has selected more than one item, Delete is greyed out.
    command.Enabled = false;
  }
}
```

 El procedimiento recomendado es llamar primero al método base para que trate con todos los casos y opciones de configuración que no le conciernen.

 El método ProcessOnStatus no debe crear, eliminar ni actualizar elementos en el almacén.

### <a name="to-change-the-behavior-of-the-command"></a>Para cambiar el comportamiento del comando
 Override the ProcessOnMenu... method. En el ejemplo siguiente se impide que el usuario elimine más de un elemento al mismo tiempo, aunque presione la tecla Suprimir.

```
/// <summary>
/// Called when user presses Delete key
/// or clicks the Delete command on a menu.
/// </summary>
protected override void ProcessOnMenuDeleteCommand()
{
  // Allow users to delete only one thing at a time.
  if (this.CurrentSelection.Count <= 1)
  {
    base.ProcessOnMenuDeleteCommand();
  }
}
```

 Si el código realiza cambios en el almacén, como crear, eliminar o actualizar elementos o vínculos, debe hacerlo dentro de una transacción. For more information, see [How to Create and Update model elements](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="writing-the-code-of-the-methods"></a>Escribir el código de los métodos
 Los siguientes fragmentos suelen resultar útiles dentro de estos métodos:

- `this.CurrentSelection`Operador La forma en la que el usuario hizo clic con el botón secundario se incluye en esta lista de formas y conectores. Si el usuario hace clic en una parte en blanco del diagrama, el diagrama es el único miembro de la lista.

- `this.IsDiagramSelected()` - `true` if the user clicked a blank part of the diagram.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()`: el usuario no seleccionó varias formas.

- `this.SingleSelection`: forma o diagrama en los que el usuario hizo clic con el botón secundario.

- `shape.ModelElement as MyLanguageElement`: elemento de modelo representado por una forma.

  For more information about how to navigate from element to element and about how to create objects and links, see [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Vea también
 <xref:System.ComponentModel.Design.MenuCommand> [Writing Code to Customise a Domain-Specific Language](../modeling/writing-code-to-customise-a-domain-specific-language.md) [How to: Add a Command to the Shortcut Menu](../modeling/how-to-add-a-command-to-the-shortcut-menu.md) [Walkthrough: Getting Information from a Selected Link](../misc/walkthrough-getting-information-from-a-selected-link.md) [How VSPackages Add User Interface Elements](../extensibility/internals/how-vspackages-add-user-interface-elements.md) [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) [VSCT XML Schema Reference](../extensibility/vsct-xml-schema-reference.md)
