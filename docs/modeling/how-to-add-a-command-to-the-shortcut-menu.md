---
title: Procedimiento Agregar un comando al menú contextual
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 365e5cae52eb9b1982900faa68afdd72de9e1337
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028515"
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>Procedimiento Agregar un comando al menú contextual

Puede agregar comandos de menú a su lenguaje específico de dominio (DSL) para que sus usuarios puedan realizar tareas específicas de su DSL. Los comandos aparecen en el menú contextual cuando los usuarios hacen clic con el botón secundario en el diagrama. Puede definir un comando para que solo aparezca en el menú en circunstancias específicas. Por ejemplo, puede hacer que el comando sea visible solo cuando el usuario haga clic en tipos específicos de elementos, o en elementos con unos estados determinados.

En resumen, los pasos se realizan en el proyecto DslPackage como sigue:

1. [Declarar el comando en Commands.vsct](#VSCT)

2. [Actualizar el número de versión del paquete en Package.tt](#version). Tiene que hacerlo siempre que cambie Commands.vsct

3. [Escribir métodos en la clase CommandSet](#CommandSet) para que el comando sea visible y definir lo que desea que el comando para hacer.

   Para obtener ejemplos, vea el [sitio Web de SDK de visualización y modelado](http://go.microsoft.com/fwlink/?LinkID=185579).

> [!NOTE]
> También puede modificar el comportamiento de algunos comandos existentes, como Cortar, Pegar, Seleccionar todo e Imprimir invalidando los métodos en CommandSet.cs. Para obtener más información, vea [Cómo: Modificar un comando de menú estándar](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="define-a-command-using-mef"></a>Definir un comando mediante MEF

Managed Extension Framework (MEF) proporciona un método alternativo para definir comandos de menú en el menú del diagrama. Su principal finalidad es habilitar un DSL para que usted u otras personas puedan ampliarlo. Los usuarios pueden elegir instalar solo el DSL o pueden instalar el DSL y las extensiones. Sin embargo, una vez hecho el trabajo inicial de habilitar MEF en el DSL, MEF reduce el trabajo de definir los comandos del menú contextual.

Use el método de este tema si:

1. Quiere definir comandos de menú en otros menús que no sea el contextual.

2. Quiere definir agrupaciones específicas de comandos en el menú.

3. No quiere permitir que otros amplíen el DSL con sus propios comandos.

4. Solo quiere definir un comando.

   En otros casos, considere usar el método MEF para definir comandos. Para obtener más información, consulte [ampliar DSL mediante MEF](../modeling/extend-your-dsl-by-using-mef.md).

##  <a name="VSCT"></a> Declarar el comando en Commands.Vsct
 Los comandos de menú se declaran en DslPackage\Commands.vsct. Estas definiciones especifican las etiquetas de los elementos de menú y dónde aparecen en los menús.

 El archivo que edite, Commands.vsct, importa definiciones de varios archivos. h, que se encuentran en el directorio *ruta de instalación de Visual Studio SDK*\VisualStudioIntegration\Common\Inc. También incluye GeneratedVsct.vsct, que se genera a partir de la definición de DSL.

 Para obtener más información sobre los archivos .vsct, vea [Visual Studio Command Table (. Archivos Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

### <a name="to-add-the-command"></a>Para agregar el comando

1.  En **el Explorador de soluciones**, en el **DslPackage** del proyecto, abra Commands.vsct.

2.  En el elemento `Commands`, defina uno o varios botones y un grupo. Un *botón* es un elemento en el menú. Un *grupo* es una sección en el menú. Para definir estos elementos, agregue lo siguiente:

    ```xml
    <!-- Define a group - a section in the menu -->
    <Groups>
      <Group guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup" priority="0x0100">
        <!-- These symbols are defined in GeneratedVSCT.vsct -->
        <Parent guid="guidCmdSet" id="menuidContext" />
      </Group>
    </Groups>
    <!-- Define a button - a menu item - inside the Group -->
    <Buttons>
      <Button guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        priority="0x0100" type="Button">
        <Parent guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup"/>
        <!-- If you do not want to place the command in your own Group,
             use Parent guid="guidCmdSet" id="grpidContextMain".
             These symbols are defined in GeneratedVSCT.vsct -->
        <CommandFlag>DynamicVisibility</CommandFlag>
        <Strings>
          <ButtonText>My Context Menu Command</ButtonText>
        </Strings>
      </Button>
    </Buttons>
    ```

    > [!NOTE]
    > Cada botón o grupo se identifica por un GUID y un identificador entero. Puede crear varios grupos y botones con el mismo GUID. Sin embargo, sus identificadores deben ser diferentes. Los nombres GUID y los nombres de identificador se traducen a reales GUID e identificadores numéricos en la `<Symbols>` nodo.

3.  Agregue una restricción de visibilidad para el comando de manera que se cargue solo en el contexto de su lenguaje específico de dominio. Para obtener más información, consulte [VisibilityConstraints (elemento)](../extensibility/visibilityconstraints-element.md).

     Para ello, agregue los siguientes elementos en el elemento `CommandTable`, después del elemento `Commands`.

    ```xml
    <VisibilityConstraints>
      <!-- Ensures the command is only loaded for this DSL -->
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        context="guidEditor"/>
    </VisibilityConstraints>
    ```

4.  Defina los nombres que usó para los GUID y los identificadores. Para ello, agregue un elemento `Symbols` en el elemento `CommandTable`, después del elemento `Commands`.

    ```xml
    <Symbols>
      <!-- Substitute a unique GUID for the placeholder: -->
      <GuidSymbol name="guidCustomMenuCmdSet"
        value="{00000000-0000-0000-0000-000000000000}" >
        <IDSymbol name="grpidMyMenuGroup" value="0x01001"/>
        <IDSymbol name="cmdidMyContextMenuCommand" value="0x00001"/>
      </GuidSymbol>
    </Symbols>
    ```

5.  Reemplace `{000...000}` por un GUID que identifique los grupos y elementos de menú. Para obtener un nuevo GUID, use la **crear GUID** herramienta en el **herramientas** menú.

    > [!NOTE]
    >  Para agregar más grupos o elementos de menú, puede usar el mismo GUID. Sin embargo, debe usar nuevos valores para `IDSymbols`.

6.  En el código que copió de este procedimiento, reemplace cada aparición de las siguientes cadenas por sus propias cadenas:

    -   `grpidMyMenuGroup`

    -   `cmdidMyContextMenuCommand`

    -   `guidCustomMenuCmdSet`

    -   `My Context Menu Command`

##  <a name="version"></a> Actualizar la versión del paquete en Package.tt
 Siempre que se agregue o se cambie un comando, actualice el parámetro `version` del <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> que se aplica a la clase de paquete antes de publicar la nueva versión de su lenguaje específico de dominio.

 Como la clase de paquete se define en un archivo generado, actualice el atributo en el archivo de plantilla de texto que genera el archivo Package.cs.

### <a name="to-update-the-packagett-file"></a>Para actualizar el archivo Package.tt

1.  En **el Explorador de soluciones**, en el **DslPackage** del proyecto, en el **GeneratedCode** carpeta, abra el archivo Package.tt.

2.  Busque el atributo `ProvideMenuResource`.

3.  Incremente el parámetro `version` del atributo, que es el segundo parámetro. Si quiere, puede escribir explícitamente el nombre del parámetro para recordarle su finalidad. Por ejemplo:

     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`

##  <a name="CommandSet"></a> Definir el comportamiento del comando

Su DSL ya tiene algunos comandos que se implementan en una clase parcial que se declara en DslPackage\GeneratedCode\CommandSet.cs. Para agregar nuevos comandos, debe extender esta clase creando un nuevo archivo que contenga una declaración parcial de la misma clase. Suele ser el nombre de la clase  *\<Sunombrededsl >*`CommandSet`. Resulta útil empezar por comprobar el nombre de la clase e inspeccionar su contenido.

La clase de conjunto de comandos deriva de <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

### <a name="extend-the-commandset-class"></a>Extender la clase CommandSet

1.  En el Explorador de soluciones, en el proyecto DslPackage, abra la carpeta GeneratedCode, busque en CommandSet.tt y abra su archivo generado CommandSet.cs. Anote el espacio de nombres y el nombre de la primera clase que se define en él. Por ejemplo, puede que vea:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2.  En **DslPackage**, cree una carpeta denominada **código personalizado**. En esta carpeta, cree un nuevo archivo de clase que se denomina `CommandSet.cs`.

3.  En el nuevo archivo, escriba una declaración parcial que tenga el mismo espacio de nombres y nombre que la clase parcial generada. Por ejemplo:

     `namespace Company.Language1 /* Make sure this is correct */`

     `{ internal partial class Language1CommandSet { ...`

     **Tenga en cuenta** si usó la plantilla de clase para crear el nuevo archivo, debe corregir el espacio de nombres y el nombre de clase.

Normalmente, el código del conjunto de comandos tendrá que exportar los siguientes espacios de nombres:

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel.Design;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
```

Ajuste el espacio de nombres y el nombre de la clase para que coincidan con los del archivo CommandSet.cs generado:

```csharp
namespace Company.Language1 /* Make sure this is correct */
{
  // Same class as the generated class.
  internal partial class Language1CommandSet
  {
```

Debe definir dos métodos, uno para determinar cuándo el comando será visible en el menú contextual (contexto) y el otro para ejecutar el comando. Estos métodos no son invalidaciones; se registran en una lista de comandos.

### <a name="define-when-the-command-will-be-visible"></a>Definir cuándo será visible el comando
 Para cada comando, defina un método `OnStatus...` que determine si el comando aparecerá en el menú, y si estará habilitado o atenuado. Establezca las propiedades `Visible` y `Enabled` de `MenuCommand`, como se muestra en el ejemplo siguiente. Se llama a este método para construir el menú contextual cada vez que el usuario hace clic con el botón secundario en el diagrama, por lo que debe trabajar rápidamente.

 En este ejemplo, el comando solo está visible cuando el usuario ha seleccionado un tipo de forma determinado, y solo se habilita cuando al menos uno de los elementos seleccionados está en un estado determinado. El ejemplo se basa en la plantilla de diagrama de clases de DSL, y ClassShape y ModelClass son tipos que se definen en el DSL:

```csharp
private void OnStatusMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  command.Visible = command.Enabled = false;
  foreach (object selectedObject in this.CurrentSelection)
  {
    ClassShape shape = selectedObject as ClassShape;
    if (shape != null)
    {
      // Visibility depends on what is selected.
      command.Visible = true;
      ModelClass element = shape.ModelElement as ModelClass;
      // Enabled depends on state of selection.
      if (element != null && element.Comments.Count == 0)
      {
        command.Enabled = true;
        return; // seen enough
} } } }
```

Los siguientes fragmentos suelen resultar útiles en los métodos OnStatus:

- `this.CurrentSelection`. La forma en la que el usuario hizo clic con el botón secundario se incluye siempre en esta lista. Si el usuario hace clic en una parte en blanco del diagrama, el diagrama es el único miembro de la lista.

- `this.IsDiagramSelected()` - `true` Si el usuario hace clic en una parte en blanco del diagrama.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()`: el usuario no seleccionó varios objetos.

- `this.SingleSelection`: forma o diagrama en los que el usuario hizo clic con el botón secundario.

- `shape.ModelElement as MyLanguageElement`: elemento de modelo representado por una forma.

Como regla general, haga que la propiedad `Visible` dependa de lo que se ha seleccionado y haga que la propiedad `Enabled` dependa del estado de los elementos seleccionados.

Un método OnStatus no debería cambiar el estado del almacén.

### <a name="define-what-the-command-does"></a>Definir la acción del comando
 Para cada comando, defina un método `OnMenu...` que realice la acción necesaria cuando el usuario haga clic en el comando de menú.

 Si realiza cambios en los elementos de modelo, debe hacerlo dentro de una transacción. Para obtener más información, vea [Cómo: Modificar un comando de menú estándar](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 En este ejemplo, `ClassShape`, `ModelClass` y `Comment` son tipos que se definen en el DSL, y derivan de la plantilla de diagrama de clases de DSL.

```csharp
private void OnMenuMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  Store store = this.CurrentDocData.Store;
  // Changes to elements and shapes must be performed in a Transaction.
  using (Transaction transaction =
       store.TransactionManager.BeginTransaction("My command"))
  {
    foreach (object selectedObject in this.CurrentSelection)
    {
      // ClassShape is defined in my DSL.
      ClassShape shape = selectedObject as ClassShape;
      if (shape != null)
      {
        // ModelClass is defined in my DSL.
        ModelClass element = shape.ModelElement as ModelClass;
        if (element != null)
        {
          // Do required action here - for example:

          // Create a new element. Comment is defined in my DSL.
          Comment newComment = new Comment(element.Partition);
          // Every element must be the target of an embedding link.
          element.ModelRoot.Comments.Add(newComment);
          // Set properties of new element.
          newComment.Text = "This is a comment";
          // Create a reference link to existing object.
          element.Comments.Add(newComment);
        }
      }
    }
    transaction.Commit(); // Don't forget this!
  }
}
```

 Para obtener más información sobre cómo navegar de un objeto a objeto en el modelo y sobre cómo crear objetos y vínculos, vea [Cómo: Modificar un comando de menú estándar](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="register-the-command"></a>Registrar el comando
 Repita en C# las declaraciones de los valores de los GUID e identificadores que realizó en la sección Symbols de CommandSet.vsct:

```csharp
private Guid guidCustomMenuCmdSet =
    new Guid("00000000-0000-0000-0000-000000000000");
private const int grpidMyMenuGroup = 0x01001;
private const int cmdidMyContextMenuCommand = 1;
```

 Use el mismo valor GUID que insertó en **Commands.vsct**.

> [!NOTE]
>  Si cambia la sección Symbols del archivo VSCT, debe cambiar también estas declaraciones para que coincidan. También debe incrementar el número de versión en Package.tt

 Registre los comandos de menú como parte de este conjunto de comandos. Se llama a `GetMenuCommands()` una vez cuando el diagrama se inicializa:

```csharp
protected override IList<MenuCommand> GetMenuCommands()
{
  // Get the list of generated commands.
  IList<MenuCommand> commands = base.GetMenuCommands();
  // Add a custom command:
  DynamicStatusMenuCommand myContextMenuCommand =
    new DynamicStatusMenuCommand(
      new EventHandler(OnStatusMyContextMenuCommand),
      new EventHandler(OnMenuMyContextMenuCommand),
      new CommandID(guidCustomMenuCmdSet, cmdidMyContextMenuCommand));
  commands.Add(myContextMenuCommand);
  // Add more commands here.
  return commands;
}
```

## <a name="test-the-command"></a>Probar el comando
 Compile y ejecute el DSL en una instancia experimental de Visual Studio. El comando debe aparecer en el menú contextual en las situaciones que haya especificado.

### <a name="to-exercise-the-command"></a>Para probar el comando

1.  En el **el Explorador de soluciones** barra de herramientas, haga clic en **Transformar todas las plantillas**.

2.  Presione **F5** para volver a generar la solución e iniciar la depuración del lenguaje específico de dominio en la compilación experimental.

3.  En la compilación experimental, abra un diagrama de muestra.

4.  Haga clic con el botón secundario en varios elementos del diagrama para comprobar que el comando aparece correctamente habilitado o deshabilitado, y que se muestra o se oculta correctamente según el elemento seleccionado.

## <a name="troubleshoot"></a>Solucionar problemas

**Comando no aparece en el menú:**

- El comando solo aparecerá en las instancias de depuración de Visual Studio, hasta que instale el paquete de DSL. Para obtener más información, consulte [implementar soluciones de lenguajes específicos de dominio](../modeling/deploying-domain-specific-language-solutions.md).

- Asegúrese de que la muestra experimental tiene la extensión de nombre de archivo correcta para este DSL. Para comprobar la extensión de nombre de archivo, abra DslDefinition.dsl en la instancia principal de Visual Studio. Después, en DSL Explorer (Explorador de DSL), haga clic en el nodo Editor y en Properties (Propiedades). En la ventana Properties (Propiedades), haga clic en la propiedad FileExtension.

- ¿Ha [incrementar el número de versión del paquete](#version)?

- Establezca un punto de interrupción al principio del método OnStatus. Debería interrumpirse al hacer clic con el botón secundario en cualquier parte del diagrama.

**No se llama el método OnStatus**:

-   Asegúrese de que los GUID e identificadores de su código de CommandSet coinciden con los de la sección Symbols de Commands.vsct.

-   En Commands.vsct, asegúrese de que, en cada nodo primario, el GUID y el identificador identifican correctamente el grupo primario.

-   En un símbolo del sistema de Visual Studio, escriba devenv /rootsuffix exp /setup. Después, reinicie la instancia de depuración de Visual Studio.

- Recorra el método OnStatus para comprobar que el valor de command.Visible y command.Enabled es True.

**Aparece el texto incorrecto o el comando aparece en el lugar incorrecto**:

- Asegúrese de que la combinación de GUID e identificador sea única para este comando.

- Asegúrese de que ha desinstalado las versiones anteriores del paquete.

## <a name="see-also"></a>Vea también

- [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Cómo: Modificar un comando de menú estándar](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)
- [Implementar soluciones de lenguajes específicos de dominio](../modeling/deploying-domain-specific-language-solutions.md)
- [Código de ejemplo: Diagramas de circuitos](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]