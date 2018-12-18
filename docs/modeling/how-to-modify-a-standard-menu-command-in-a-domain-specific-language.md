---
title: 'Cómo: Modificar comandos de menú estándar en lenguajes específicos de dominio'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6aa827781cb8ea78aa5df79f8cb839a6f3548e11
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967056"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Cómo: Modificar comandos de menú estándar en lenguajes específicos de dominio

Puede modificar el comportamiento de algunos de los comandos estándar que se definen automáticamente en su DSL. Por ejemplo, podría modificar **cortar** para que excluya información confidencial. Para ello, se invalidan los métodos en una clase de conjunto de comandos. Estas clases se definen en el archivo CommandSet.cs, en el proyecto DslPackage, y derivan de <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

> [!NOTE]
> Si desea crear sus propios comandos de menú, vea [Cómo: agregar un comando al menú contextual](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

## <a name="what-commands-can-you-modify"></a>¿Qué comandos puede modificar?

### <a name="to-discover-what-commands-you-can-modify"></a>Para averiguar qué comandos puede modificar

1.  En el `DslPackage` proyecto, abra `GeneratedCode\CommandSet.cs`. Este archivo de C# puede encontrarse en el Explorador de soluciones como subsidiario de `CommandSet.tt`.

2.  Buscar clases en este archivo cuyos nombres terminan con "`CommandSet`", por ejemplo `Language1CommandSet` y `Language1ClipboardCommandSet`.

3.  En cada clase de conjunto de comandos, escriba "`override`" seguido de un espacio. IntelliSense mostrará una lista de los métodos que puede invalidar. Cada comando tiene un par de métodos cuyos nombres comienzan por "`ProcessOnStatus`" y "`ProcessOnMenu`".

4.  Anote qué clases de conjunto de comandos contiene el comando que quiere modificar.

5.  Cierre el archivo sin guardar las ediciones.

    > [!NOTE]
    > Normalmente no debe editar los archivos que se han generado. Las ediciones se perderán la próxima vez que se generen los archivos.

## <a name="extend-the-appropriate-command-set-class"></a>Extienda la clase de conjunto de comandos apropiada.

Cree un nuevo archivo que contiene una declaración parcial de la clase de conjunto de comandos.

### <a name="to-extend-the-command-set-class"></a>Para extender la clase de conjunto de comandos

1.  En el Explorador de soluciones, en el proyecto DslPackage, abra la carpeta GeneratedCode, busque en CommandSet.tt y abra su archivo generado CommandSet.cs. Anote el espacio de nombres y el nombre de la primera clase que se define en él. Por ejemplo, puede que vea:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2.  En **DslPackage**, cree una carpeta denominada **código personalizado**. En esta carpeta, cree un nuevo archivo de clase denominado `CommandSet.cs`.

3.  En el nuevo archivo, escriba una declaración parcial que tenga el mismo espacio de nombres y nombre que la clase parcial generada. Por ejemplo:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Design;
    namespace Company.Language1 /* Make sure this is correct */
    { internal partial class Language1CommandSet { ...
    ```

     **Tenga en cuenta** si usó la plantilla de archivo de clase para crear el nuevo archivo, debe corregir el espacio de nombres y el nombre de clase.

## <a name="override-the-command-methods"></a>Invalidar los métodos de comando

Mayoría de los comandos tiene dos métodos asociados: el método con un nombre como `ProcessOnStatus`... determina si el comando debe estar visible y habilitado. Se llama siempre que el usuario hace clic con el botón secundario en el diagrama, debe ejecutarse rápidamente y no realiza cambios. `ProcessOnMenu`... se llama cuando el usuario hace clic en el comando y debe realizar la función del comando. Quizás quiera invalidar uno o los dos métodos.

### <a name="to-change-when-the-command-appears-on-a-menu"></a>Para cambiar cuándo aparece el comando en un menú

Invalide el método ProcessOnStatus... método. Este método debe establecer las propiedades Visible y Enabled de su parámetro MenuCommand. Normalmente, el comando busca en this.CurrentSelection para determinar si se aplica a los elementos seleccionados, y también podría buscar en sus propiedades para determinar si se puede aplicar en el estado actual de las mismas.

Como regla general, la propiedad Visible se debe determinar en función de qué elementos están seleccionados. La propiedad Enabled, que determina si el comando aparece en negro o en gris en el comando, dependerá del estado actual de la selección.

En el ejemplo siguiente se deshabilita el elemento de menú Delete cuando el usuario selecciona más de una forma.

> [!NOTE]
> Este método no afecta a si el comando está disponible presionando una tecla. Por ejemplo, deshabilitar el elemento de menú Delete no impide que el comando se invoque desde la tecla Suprimir.

```csharp
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

Invalide el método ProcessOnMenu... método. En el ejemplo siguiente se impide que el usuario elimine más de un elemento al mismo tiempo, aunque presione la tecla Suprimir.

```csharp
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

Si el código realiza cambios en el almacén, como crear, eliminar o actualizar elementos o vínculos, debe hacerlo dentro de una transacción. Para obtener más información, consulte [cómo crear y actualizar elementos de modelo](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="write-the-code-of-the-methods"></a>Escribir el código de los métodos

Los siguientes fragmentos suelen resultar útiles dentro de estos métodos:

-   `this.CurrentSelection`. La forma en la que el usuario hizo clic con el botón secundario se incluye en esta lista de formas y conectores. Si el usuario hace clic en una parte en blanco del diagrama, el diagrama es el único miembro de la lista.

-   `this.IsDiagramSelected()` - `true` Si el usuario hace clic en una parte en blanco del diagrama.

-   `this.IsCurrentDiagramEmpty()`

-   `this.IsSingleSelection()`: el usuario no seleccionó varias formas.

-   `this.SingleSelection`: forma o diagrama en los que el usuario hizo clic con el botón secundario.

-   `shape.ModelElement as MyLanguageElement`: elemento de modelo representado por una forma.

Para obtener más información sobre cómo navegar de un elemento a otro y sobre cómo crear objetos y vínculos, consulte [navegar y actualizar un modelo en el código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Vea también

- <xref:System.ComponentModel.Design.MenuCommand>
- [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Cómo: Agregar un comando a un menú contextual](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)
- [Adición de elementos de la interfaz de usuario por VSPackages](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referencia del esquema XML de VSCT](../extensibility/vsct-xml-schema-reference.md)
- [VMSDK: diagramas de circuitos. Personalización extensa DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
