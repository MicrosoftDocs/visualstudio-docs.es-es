---
title: Introducción al código DSL
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, generated code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1196faa5831ae44a93f21ab1808915357690a0ac
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565947"
---
# <a name="understanding-the-dsl-code"></a>Introducción al código DSL

Una solución de lenguaje específico del dominio (DSL) genera una API que se puede usar para leer y actualizar instancias del DSL en Visual Studio. Esta API se define en el código que se genera a partir de la definición de DSL. Este tema describe la API que se genera.

## <a name="the-example-solution-component-diagrams"></a>La solución de ejemplo: diagramas de componentes

Para crear la solución que es el origen de la mayoría de los ejemplos de este tema, cree un DSL a partir de la plantilla de solución de **modelos de componentes** . Esta es una de las plantillas estándar que aparece al crear una nueva solución de DSL.

> [!NOTE]
> La plantilla de DSL de diagramas de componentes se denomina **Diseñador de lenguaje específico de dominio**.

Presione **F5** y experimente si no está familiarizado con esta plantilla de solución. En concreto, tenga en cuenta que los puertos se crean arrastrando una herramienta de puerto a un componente, y que puede conectar puertos.

![Componentes y puertos interconectados](../modeling/media/componentsample.png)

## <a name="the-structure-of-the-dsl-solution"></a>Estructura de la solución de DSL
 El proyecto **DSL** define la API del DSL. El proyecto **DslPackage** define cómo se integra con Visual Studio. También puede agregar sus propios proyectos, que también pueden contener código generado a partir del modelo.

### <a name="the-code-directories"></a>Directorios de código
 La mayor parte del código de cada uno de estos proyectos se genera a partir de **Dsl\DslDefinition.DSL**. El código generado se encuentra en la carpeta de **código generado** . Para ver un archivo generado, haga clic en **[+]** junto al archivo generando **. TT** .

 Le recomendamos que inspeccione el código generado para ayudarle a comprender el DSL. Para ver los archivos generados, expanda los archivos *.tt en el Explorador de soluciones.

 Los archivos \*. TT contienen muy poco código de generación. En lugar de eso, usan directivas `<#include>` para incluir archivos de plantilla compartidos. Los archivos compartidos se pueden encontrar en **\Archivos de Programa\microsoft Visual Studio 10.0 \ COMMON7\IDE\EXTENSIONS\MICROSOFT\DSL SDK\DSL Designer\11.0\TextTemplates**

 Cuando agregue su propio código de programa a la solución de DSL, hágalo en un archivo diferente, fuera de la carpeta Generated Code. Es posible que desee crear una carpeta de **código personalizada** . (Cuando agregue un nuevo archivo de código a una carpeta personalizada, acuérdese de corregir el espacio de nombres en el esqueleto de código inicial).

 Le recomendamos que no edite el código generado directamente, porque las ediciones se perderán al volver a compilar la solución. En su lugar, para personalizar el DSL:

- Ajuste los numerosos parámetros de la definición de DSL.

- Escriba clases parciales en archivos de código diferentes para invalidar los métodos que se definen en clases generadas o se heredan de ellas. En algunos casos, tiene que establecer la opción **genera Double derived** de una clase en la definición de DSL para poder invalidar un método generado.

- Establezca las opciones de la definición de DSL que hacen que el código generado proporcione "enlaces" para su propio código.

     Por ejemplo, si establece la opción **tiene el constructor personalizado** de una clase de dominio y, a continuación, compila la solución, verá mensajes de error. Al hacer doble clic en uno de estos mensajes de error, verá comentarios en el código generado que explican lo que su código personalizado debe proporcionar.

- Escriba sus propias plantillas de texto para generar código específico para su aplicación. Puede usar archivos de inclusión para compartir partes de las plantillas que son comunes a muchos proyectos, y puede crear plantillas de proyecto de Visual Studio para configurar proyectos que se inicializan con su propia estructura de archivos.

## <a name="generated-files-in-dsl"></a>Archivos generados en DSL
 Los siguientes archivos generados aparecen en el proyecto **DSL** .

 `Schema.xsd` *sudsl*

 Esquema de los archivos que contienen instancias de su DSL. Este archivo se copia en el directorio de compilación (**bin**). Al instalar DSL, puede copiar este archivo en **\Archivos de Programa\microsoft Visual Studio 11.0 \ Xml\Schemas** para que se puedan validar los archivos de modelo. Para obtener más información, vea [Implementación de soluciones de lenguaje específico de dominio](msi-and-vsix-deployment-of-a-dsl.md).

 Si personaliza la serialización estableciendo las opciones en DSL Explorer (Explorador de DSL), el esquema cambiará como corresponda. Sin embargo, si escribe su propio código de serialización, este archivo podría no representar ya el esquema actual. Para obtener más información, vea [personalizar File Storage y serialización XML](../modeling/customizing-file-storage-and-xml-serialization.md).

 `ConnectionBuilders.cs`

 Un generador de conexiones es una clase que crea relaciones. Es el código que hay detrás de una herramienta de conexión. Este archivo contiene un par de clases para cada herramienta de conexión. Sus nombres se derivan de los nombres de la relación de dominio y la herramienta de conexión: compilador de *relaciones*y *herramientadeconector*ConnectAction.

 (En la solución de componentes de ejemplo, uno de los generadores de conexiones se llama ConnectionBuilder. Esto es una coincidencia porque la relación de dominio se llama Connection).

 La relación se crea en el método *relationship*`Builder.Connect()`. La versión predeterminada comprueba que los elementos de modelo de origen y destino son aceptables y, después, crea una instancia de la relación. Por ejemplo:

 `CommentReferencesSubject(sourceAccepted, targetAccepted);`

 Cada clase de generador se genera a partir de un nodo en la sección **generadores de conexiones** del explorador de DSL. Un método `Connect` puede crear relaciones entre uno o varios pares de clases de dominio. Cada par se define mediante una directiva de conexión de vínculo, que encontrará en DSL Explorer (Explorador de DSL), en el nodo del generador.

 Por ejemplo, en un generador de conexiones podría agregar directivas de conexión de vínculo para cada uno de los tres tipos de relación del DSL de muestra. Esto proporcionaría al usuario una única herramienta de conexión. El tipo de relación del cual se crea una instancia dependerá del tipo de los elementos de origen y destino que seleccione el usuario.  Para agregar directivas de conexión de vínculo, haga clic con el botón secundario en DSL Explorer (Explorador de DSL).

 Para escribir código personalizado que se ejecuta cuando se crea un tipo específico de una relación de dominio, seleccione la directiva de conexión de vínculo apropiada en el nodo del generador. En el ventana Propiedades, establezca **usa conexión personalizada**. Vuelva a compilar la solución y suministre el código para corregir los errores resultantes.

 Para escribir código personalizado que se ejecute siempre que el usuario Use esta herramienta de conexión, establezca la propiedad **is Custom** del generador de conexiones. Puede suministrar código que decida si un elemento de origen está permitido, si una combinación específica de origen y destino está permitida y qué actualizaciones se deben realizar al modelo cuando se realiza una conexión. Por ejemplo, podría permitir una conexión solo si no crea un bucle en el diagrama. En lugar de un único vínculo de relación, podría crear una instancia de un patrón más complejo de varios elementos interrelacionados entre el origen y el destino.

 `Connectors.cs`

 Contiene las clases de los conectores, que son elementos de diagrama que normalmente representan relaciones de referencia. Cada clase se genera a partir de un conector de la definición de DSL. Todas las clases de conector derivan de <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>.

 Para que el color y otras características de estilo sean variables en tiempo de ejecución, haga clic con el botón secundario en la clase del diagrama de definición de DSL y seleccione **Agregar exposición**.

 Para que otras características de estilo sean variables en tiempo de ejecución, vea <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> y <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>, por ejemplo.

 `Diagram.cs`

 Contiene la clase que define el diagrama. Deriva de <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>.

 Para que el color y otras características de estilo sean variables en tiempo de ejecución, haga clic con el botón secundario en la clase del diagrama de definición de DSL y seleccione **Agregar exposición**.

 Además, este archivo contiene la regla `FixupDiagram`, que responde cuando se agrega un nuevo elemento al modelo. La regla agrega una nueva forma y la vincula al elemento de modelo.

 `DirectiveProcessor.cs`

 Este procesador de directivas ayuda a los usuarios a escribir plantillas de texto que leen una instancia de su DSL. El procesador de directivas carga los ensamblados (DLL) de su DSL e inserta instrucciones `using` para su espacio de nombres. Esto permite al código de las plantillas de texto usar las clases y relaciones que ha definido en su DSL.

 Para obtener más información, vea [generar código a partir de un lenguaje específico de dominio](../modeling/generating-code-from-a-domain-specific-language.md) y [crear procesadores de directivas de plantilla de texto T4 personalizados](../modeling/creating-custom-t4-text-template-directive-processors.md).

 `DomainClasses.cs`

 Implementaciones de las clases de dominio que ha definido, incluidas las clases abstractas y la clase raíz del modelo. Derivan de <xref:Microsoft.VisualStudio.Modeling.ModelElement>.

 Cada clase de dominio contiene:

- Una definición de propiedad y una clase de controlador anidada para cada propiedad de dominio. Puede invalidar OnValueChanging() y OnValueChanged(). Para obtener más información, vea [controladores de cambios de valor de propiedad de dominio](../modeling/domain-property-value-change-handlers.md).

   En el DSL de ejemplo, la clase `Comment` contiene una propiedad `Text` y una clase de controlador `TextPropertyHandler`.

- Las propiedades de descriptor de acceso de las relaciones en las que esta clase de dominio participa. (No hay ninguna clase anidada para las propiedades del rol).

   En el DSL de ejemplo, la clase `Comment` tiene descriptores de acceso que acceden a su modelo primario a través de la relación de incrustación `ComponentModelHasComments`.

- Constructores. Si desea invalidarlos, establezca **tiene un constructor personalizado** en la clase de dominio.

- Métodos de controlador de Prototipo de grupo de elementos (EGP). Son necesarios si el usuario puede *combinar* (agregar) otro elemento en las instancias de esta clase. Para hacerlo, normalmente el usuario arrastra desde una herramienta de elemento u otra forma, o realiza una operación de pegar.

   En el DSL de ejemplo, se puede combinar un puerto de entrada o de salida con un componente. Además, se pueden combinar componentes y comentarios en el modelo. La .

   Los métodos del controlador de EGP en la clase Component permiten a un componente aceptar puertos pero no comentarios. El controlador de EGP en la clase raíz del modelo acepta comentarios y componentes, pero no puertos.

  `DomainModel.cs`

  La clase que representa el modelo de dominio. Deriva de <xref:Microsoft.VisualStudio.Modeling.DomainModel>.

> [!NOTE]
> No es la misma que la clase raíz del modelo.

 Copy y Delete Closures definen qué otros elementos se deben incluir cuando se copia o se elimina un elemento. Puede controlar este comportamiento estableciendo la opción **Propagate Copy** y **propaga** las propiedades Delete de los roles en cada lado de cada relación. Si quiere que los valores se determinen dinámicamente, puede escribir código para invalidar los métodos de las clases Closure.

 `DomainModelResx.resx`

 Contiene cadenas que se podrían mostrar al usuario, tales como descripciones de las clases y propiedades de dominio, nombres de propiedad, etiquetas de cuadro de herramientas o mensajes de error estándar, entre otras. También contiene imágenes e iconos de herramienta para formas de imagen.

 Este archivo se enlaza en el ensamblado compilado y proporciona los valores predeterminados de estos recursos. Puede localizar su DSL creando un ensamblado satélite que contenga una versión localizada de los recursos. Esta versión se usará cuando se instale el DSL en una referencia cultural que coincida con los recursos localizados. Para obtener más información, vea [Implementación de soluciones de lenguaje específico de dominio](msi-and-vsix-deployment-of-a-dsl.md).

 `DomainRelationships.cs`

 Cada vínculo entre dos elementos de un modelo se representa con una instancia de una clase de relación de dominio. Todas las clases de relación derivan de <xref:Microsoft.VisualStudio.Modeling.ElementLink> que, a su vez, deriva de <xref:Microsoft.VisualStudio.Modeling.ModelElement>. Como es un ModelElement, una instancia de una relación puede tener propiedades y puede ser el origen o el destino de una relación.

 `HelpKeywordHelper.cs`

 Proporciona funciones que se usan cuando el usuario presiona F1.

 `MultiplicityValidation.cs`

 En roles de relación en los que se especifica una multiplicidad de 1..1 o 1..*, se debe advertir al usuario de que se necesita al menos una instancia de la relación. Este archivo proporciona restricciones de validación que implementan esas advertencias. El vínculo 1..1 a un primario de incrustación no se comprueba.

 Para que se ejecuten estas restricciones, debe haber establecido una de las opciones de **use...** en el nodo **Editor\Validation** del explorador de DSL. Para obtener más información, vea [validación en un lenguaje específico de dominio](../modeling/validation-in-a-domain-specific-language.md).

 `PropertiesGrid.cs`

 Este archivo contiene código solo si ha asociado un descriptor de tipo personalizado a una propiedad de dominio. Para obtener más información, vea [personalizar la ventana Propiedades](../modeling/customizing-the-properties-window.md).

 `SerializationHelper.cs`

- Método de validación que garantiza que el mismo moniker no hace referencia a dos elementos. Para obtener más información, vea [personalizar File Storage y serialización XML](../modeling/customizing-file-storage-and-xml-serialization.md).

- Clase SerializationHelper, que proporciona funciones que las clases de serialización usan en común.

  `Serializer.cs`

  Clase de serializador para cada clase de dominio, relación, forma, conector, diagrama y modelo.

  Muchas de las características de estas clases se pueden controlar mediante la configuración del explorador de DSL en **comportamiento de serialización XML**.

  `Shapes.cs`

  Una clase para cada clase de forma en la definición de DSL. Las formas derivan de <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>. Para obtener más información, vea [personalizar File Storage y serialización XML](../modeling/customizing-file-storage-and-xml-serialization.md).

  Para invalidar los métodos generados con sus propios métodos en una clase parcial, establezca **genera Double derived** para el conector en la definición de DSL. Para reemplazar un constructor con su propio código, establezca **tiene un constructor personalizado**.

  Para que el color y otras características de estilo sean variables en tiempo de ejecución, haga clic con el botón secundario en la clase del diagrama de definición de DSL y seleccione **Agregar exposición**.

  Para que otras características de estilo sean variables en tiempo de ejecución, vea <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> y <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>, por ejemplo.

  `ToolboxHelper.cs`

  Configura el cuadro de herramientas instalando prototipos de grupos de elementos en las herramientas de elemento. Las copias de estos prototipos se combinan con los elementos de destino cuando el usuario ejecuta la herramienta.

  Podría invalidar `CreateElementPrototype()` para definir un cuadro de herramientas que cree un grupo de varios objetos. Por ejemplo, podría definir un elemento para representar objetos que tienen subcomponentes. Después de cambiar el código, restablezca la instancia experimental de Visual Studio para borrar la memoria caché del cuadro de herramientas.

## <a name="generated-files-in-the-dslpackage-project"></a>Archivos que se generan en el proyecto DslPackage
 DslPackage acopla el modelo DSL al shell de Visual Studio, administrando los comandos de ventana, cuadro de herramientas y menú. La mayoría de las clases son dobles derivadas, por lo que puede invalidar cualquiera de sus métodos.

 `CommandSet.cs`

 Los comandos de menú contextual que están visibles en el diagrama. Puede adaptar o ampliar este conjunto. Este archivo contiene el código de los comandos. El archivo Commands.vsct determina la ubicación de los comandos en los menús. Para obtener más información, consulte [escribir comandos y acciones de usuario](how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 `Constants.cs`

 GUID.

 `DocData.cs`

 *Sudsl* `DocData` administra la carga y el guardado de un modelo en el archivo, y crea la instancia de almacén.

 Por ejemplo, si quiere guardar su DSL en una base de datos en lugar de un archivo, puede invalidar los métodos `Load` y `Save`.

 `DocView.cs`

 *Sudsl* `DocView` administra la ventana en la que aparece el diagrama. Por ejemplo, podría incrustar el diagrama dentro de un Windows Form:

 Agregue un archivo de control de usuario al proyecto DslPackage. Agregue un panel en el que se pueda mostrar el diagrama. Agregue botones y otros controles. En la vista de código del formulario, agregue el siguiente código y ajuste los nombres a su DSL:

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Drawing;
using System.Data;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Shell;

namespace Company.EmbedInForm
{
  public partial class UserControl1 : UserControl
  {
    public UserControl1()
    {
      InitializeComponent();
    }

    private DiagramDocView docView;

    public UserControl1(DiagramDocView docView, Control content)
      : this()
    {
      this.docView = docView;
      panel1.Controls.Add(content);
    }

    private void button1_Click(object sender, EventArgs e)
    {
      ExampleModel modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      foreach (ExampleElement element in modelRoot.Elements)
      {
       listBox1.Items.Add(element.Name);
      }
    }
  }
  internal partial class EmbedInFormDocView
  {

    private ContainerControl container;

    /// <summary>
    /// Return a User Control instead of the DSL window.
    /// The user control will contain the DSL window.
    /// </summary>

    public override System.Windows.Forms.IWin32Window Window
    {
      get
      {
        if (container == null)
        {
          // Put the normal DSL Window inside our control
          container = new UserControl1(this, (Control)base.Window);
        }
        return container;
      }
    }
  }

}
```

 `EditorFactory.cs`

 Crea instancias de `DocData` y `DocView`. Cumple una interfaz estándar que Visual Studio usa para abrir un editor cuando se inicia el paquete DSL. Se hace referencia a ella en el atributo `ProvideEditorFactory`, en Package.cs.

 `GeneratedVSCT.vsct`

 Busca los comandos de menú estándar en los menús, como el menú de clic con el botón secundario (contexto), el menú **edición** , etc. El código de comandos está en CommandSet.cs. Puede reubicar o modificar los comandos estándar y puede agregar sus propios comandos. Para obtener más información, consulte [escribir comandos y acciones de usuario](how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 `ModelExplorer.cs`

 Define el explorador del modelo para su DSL. Es la vista de árbol del modelo que el usuario ve a lo largo del diagrama.

 Por ejemplo, podría invalidar `InsertTreeView()` para cambiar el orden con el que los elementos aparecen en el explorador del modelo.

 Si quiere que la selección en el explorador del modelo se mantenga sincronizada con la selección en el diagrama, use el código siguiente:

```csharp
protected override void OnSelectionChanged(global::System.EventArgs e)
{
base.OnSelectionChanged(e);
// get the selected element
DslModeling::ModelElement selectedElement =
this.PrimarySelection as DslModeling::ModelElement;
// Select in the model explorer
SelectInModelExplorer<YOURLANGUAGEExplorerToolWindow>(selectedElement);
}
private void SelectInModelExplorer<T>(DslModeling::ModelElement modelElement)
where T : DslShell.ModelExplorerToolWindow
{
DslShell::ModelingPackage package =
this.GetService(typeof(VSShell.Package)) as DslShell::ModelingPackage;

if (package != null)
{
// find the model explorer window
T explorerWindow = package.GetToolWindow(typeof(T), true) as T;
if (explorerWindow != null)
{
// get the tree container
DslShell.ModelExplorerTreeContainer treeContainer =
explorerWindow.TreeContainer;
// find the tree node
DslShell.ExplorerTreeNode treeNode =
treeContainer.FindNodeForElement(modelElement);
// select the node
explorerWindow.TreeContainer.ObjectModelBrowser.SelectedNode = treeNode;
}
}
}
```

 `ModelExplorerToolWindow.cs`

 Define la ventana en la que se muestra el explorador del modelo. Controla la selección de elementos en el explorador.

 `Package.cs`

 Este archivo define cómo se integra el DSL en Visual Studio. Los atributos en la clase de paquete registran el DSL como el controlador de los archivos que tienen su extensión de archivo, definen su cuadro de herramientas y definen cómo abrir una nueva ventana. Se llama al método Initialize () una vez cuando se carga el primer DSL en una instancia de Visual Studio.

 `Source.extension.vsixmanifest`

 Para personalizar este archivo, edite el archivo `.tt`.

> [!WARNING]
> Si edita el archivo .tt para incluir recursos como iconos o imágenes, asegúrese de que el recurso se incluye en la compilación de VSIX. En Explorador de soluciones, seleccione el archivo y asegúrese de que la propiedad **incluir en VSIX** esté `True`.

 Este archivo controla cómo se empaqueta el DSL en una extensión de integración de Visual Studio (VSIX). Para obtener más información, vea [Implementación de soluciones de lenguaje específico de dominio](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Vea también

- [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Introducción a los modelos, las clases y las relaciones](../modeling/understanding-models-classes-and-relationships.md)
- [Personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)
- [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
