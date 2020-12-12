---
title: Integración de modelos mediante Modelbus
description: Aprenda que Visual Studio ModelBus proporciona un método para crear vínculos entre modelos y otras herramientas en modelos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 46705c7a614cd67d81c9e55c03e937f72c29a2fe
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360733"
---
# <a name="integrate-models-by-using-visual-studio-modelbus"></a>Integrar modelos mediante Modelbus de Visual Studio

Visual Studio ModelBus proporciona un método para crear vínculos entre modelos y otras herramientas en modelos. Por ejemplo, podría vincular modelos de lenguaje específico de dominio (DSL) y modelos UML. Puede crear un conjunto integrado de DSL.

ModelBus permite crear una referencia única a un modelo o a un elemento específico dentro de un modelo. Esta referencia se puede almacenar fuera del modelo, por ejemplo, en un elemento en otro modelo. Más adelante, cuando una herramienta quiera obtener acceso al elemento, la infraestructura de ModelBus cargará el modelo apropiado y devolverá el elemento. Si quiere, puede mostrar el modelo al usuario. Si no se puede acceder al archivo en su ubicación anterior, ModelBus pedirá al usuario que lo busque. Si el usuario encuentra el archivo, ModelBus corregirá todas las referencias a ese archivo.

> [!NOTE]
> En la implementación actual de Visual Studio de ModelBus, los modelos vinculados deben ser elementos de la misma solución de Visual Studio.

Para obtener información y ejemplos de código, vea:

- [Cómo: Agregar un controlador para arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md)

- [SDK de modelado para Visual Studio](https://www.microsoft.com/download/details.aspx?id=48148)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="providing-access-to-a-dsl"></a><a name="provide"></a> Proporcionar acceso a un DSL
 Antes de crear referencias de ModelBus a un modelo o a sus elementos, debe definir un ModelBusAdapter para el DSL. La forma más fácil de hacerlo es usar la extensión de bus de modelo de Visual Studio, que agrega comandos al Diseñador DSL.

### <a name="to-expose-a-dsl-definition-to-model-bus"></a><a name="expose"></a> Para exponer una definición de DSL a Model bus

1. Abra el archivo de definición de DSL. Haga clic con el botón secundario en la superficie de diseño y haga clic en **Habilitar Modelbus**.

2. En el cuadro de diálogo, elija **deseo exponer este DSL a ModelBus**. Puede elegir ambas opciones si quiere que este DSL exponga sus modelos y use referencias a otros DSL.

3. Haga clic en **Aceptar**. Se agrega un nuevo proyecto "ModelBusAdapter" a la solución de DSL.

4. Si quiere acceder al DSL desde una plantilla de texto, debe modificar AdapterManager.tt en el nuevo proyecto. Omita este paso si quiere acceder al DSL desde otro código, como comandos y controladores de eventos. Para obtener más información, vea [usar Visual Studio ModelBus en una plantilla de texto](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

   1. Cambie la clase base de AdapterManagerBase a [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)).

   2. Cerca del final del archivo, inserte este atributo adicional frente a la clase AdapterManager:

       `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

   3. En el proyecto References of ModelBusAdapter, agregue **Microsoft. VisualStudio. TextTemplating. Modeling. 11.0**.

      Si quiere acceder al DSL desde las plantillas de texto y desde otro código, necesita dos adaptadores, uno modificado y otro sin modificar.

5. Haga clic en **transformar todas las plantillas**.

6. Recompilar la solución.

   Ahora, ModelBus puede abrir instancias de este DSL.

   La carpeta `ModelBusAdapters\bin\*` contiene los ensamblados compilados por el proyecto `Dsl` y el proyecto `ModelBusAdapters`. Para hacer referencia a este DSL desde otro DSL, debe importar estos ensamblados.

### <a name="ensure-that-elements-can-be-referenced"></a>Asegurarse de que se puede hacer referencia a los elementos

De forma predeterminada, los adaptadores de Visual Studio ModelBus usan el GUID de un elemento para identificarlo. Estos identificadores deben conservarse en el archivo del modelo.

Para asegurarse de que se conservan los identificadores de elemento:

1. Abra DslDefinition.dsl.

2. En el explorador de DSL, expanda **comportamiento de serialización XML** y, a continuación, **datos de clase**.

3. Para cada clase para la que quiera crear referencias de ModelBus:

    Haga clic en el nodo clase y, en el ventana Propiedades, asegúrese de que **serializar identificador** está establecido en `true` .

   Como alternativa, si desea utilizar nombres de elemento para identificar elementos en lugar de GUID, puede invalidar las partes de los adaptadores generados. Invalide los siguientes métodos en la clase de adaptador:

- Invalide `GetElementId` para devolver el identificador que quiere usar. Se llama a este método cuando se crean referencias.

- Invalide `ResolveElementReference` para buscar el elemento correcto en una referencia de ModelBus.

## <a name="accessing-a-dsl-from-another-dsl"></a><a name="editRef"></a> Acceso a un DSL desde otro DSL

Puede almacenar referencias de ModelBus en una propiedad de dominio de un DSL, y puede escribir código personalizado para usarlas. También puede permitir que el usuario cree una referencia de ModelBus seleccionando un archivo de modelo y un elemento dentro de él.

Para que un DSL pueda usar referencias a otro DSL, primero debe convertirlo en un *consumidor* de referencias de bus de modelo.

### <a name="to-enable-a-dsl-to-consume-references-to-an-exposed-dsl"></a>Para que un DSL pueda consumir referencias a un DSL expuesto

1. En el diagrama de definición de DSL, haga clic con el botón secundario en la parte principal del diagrama y, a continuación, haga clic en **Habilitar Modelbus**.

2. En el cuadro de diálogo, seleccione **deseo habilitar este modelo para consumir las referencias de bus de modelo**.

3. En el proyecto del DSL de consumo, agregue los siguientes ensamblados a las referencias del proyecto. Encontrará estos ensamblados (archivos. dll) en el directorio ModelBusAdapter\bin \\ * del DSL expuesto.

    - El ensamblado DSL expuesto, por ejemplo **Fabrikam.FamilyTree.Dsl.dll**

    - El ensamblado del adaptador de bus de modelo expuesto, por ejemplo **Fabrikam.FamilyTree.ModelBusAdapter.dll**

4. Agregue los siguientes ensamblados .NET a las referencias del proyecto de DSL de consumo.

    1. **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

    2. **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**

### <a name="to-store-a-model-bus-reference-in-a-domain-property"></a>Para almacenar una referencia de ModelBus en una propiedad de dominio

1. En DSL Definition (Definición de DSL) del DSL de consumo, agregue una propiedad de dominio a una clase de dominio y establezca su nombre.

2. En el ventana Propiedades, con la propiedad de dominio seleccionada, establezca **tipo** en `ModelBusReference` .

   En esta etapa, el código de programa puede establecer el valor de la propiedad, pero es de solo lectura en la ventana Properties (Propiedades).

   Puede permitir que los usuarios establezcan la propiedad con un editor de referencias de ModelBus especializado. Hay dos versiones de este editor o *selector:* una permite a los usuarios elegir un archivo de modelo y el otro permite a los usuarios elegir un archivo de modelo y un elemento dentro del modelo.

### <a name="to-allow-the-user-to-set-a-model-bus-reference-in-a-domain-property"></a>Para que el usuario pueda establecer una referencia de ModelBus en una propiedad de dominio

1. Haga clic con el botón secundario en la propiedad de dominio y, a continuación, haga clic en **Editar propiedades específicas de ModelBusReference**. Se abre un cuadro de diálogo. Este es el *selector de bus de modelo*.

2. Seleccione el **tipo adecuado de ModelBusReference**: a un modelo o a un elemento dentro de un modelo.

3. En la cadena de filtro del cuadro de diálogo de archivos, especifique una cadena como `Family Tree files |*.ftree`. Sustituya la extensión de archivo del DSL expuesto.

4. Si eligió hacer referencia a un elemento en un modelo, puede agregar una lista de tipos que el usuario puede seleccionar, por ejemplo, Company.FamilyTree.Person.

5. Haga clic en **Aceptar** y, a continuación, haga clic en **transformar todas las plantillas** en la barra de herramientas **Explorador de soluciones** .

    > [!WARNING]
    > Si no ha seleccionado un modelo o entidad válidos, el botón Aceptar no tendrá efecto aunque aparezca habilitado.

6. Si especificó una lista de tipos de destino, como Company.FamilyTree.Person, debe agregar una referencia de ensamblado a su proyecto de DSL, haciendo referencia al archivo DLL del DSL de destino, por ejemplo, Company.FamilyTree.Dsl.dll

### <a name="to-test-a-model-bus-reference"></a>Para probar una referencia de ModelBus

1. Compile los DSL expuestos y de consumo.

2. Presione F5 o CTRL+F5 para ejecutar uno de los DSL en modo experimental.

3. En el proyecto de depuración en la instancia experimental de Visual Studio, agregue los archivos que son instancias de cada DSL.

    > [!NOTE]
    > Visual Studio ModelBus solo puede resolver referencias a modelos que son elementos de la misma solución de Visual Studio. Por ejemplo, no puede crear una referencia a un archivo de modelo que esté en otra parte del sistema de archivos.

4. Cree algunos elementos y vínculos en la instancia del DSL expuesto, y guárdelo.

5. Abra una instancia del DSL de consumo y seleccione un elemento de modelo que tenga una propiedad de referencia de ModelBus.

6. En la ventana Propiedades, haga doble clic en la propiedad de referencia de ModelBus. Se abre el cuadro de diálogo del selector.

7. Haga clic en **examinar** y seleccione la instancia del DSL expuesto.

     El selector también le permitirá elegir un elemento del modelo, si especificó el tipo de referencia de ModelBus específica del elemento.

## <a name="creating-references-in-program-code"></a>Crear referencias en código de programa

Si quiere almacenar una referencia a un modelo o a un elemento dentro de un modelo, cree una `ModelBusReference`. Hay dos tipos de `ModelBusReference` : referencias de modelo y referencias de elemento.

Para crear una referencia de modelo, se necesita el AdapterManager del DSL del que el modelo es una instancia y el nombre de archivo o el elemento de proyecto de Visual Studio del modelo.

Para crear una referencia de elemento, necesita un adaptador para el archivo de modelo, y el elemento al que quiere hacer referencia.

> [!NOTE]
> Con el Visual Studio ModelBus, solo puede crear referencias a los elementos de la misma solución de Visual Studio.

### <a name="import-the-exposed-dsl-assemblies"></a>Importar los ensamblados de DSL expuestos

En el proyecto de consumo, agregue referencias de proyecto a los ensamblados de DSL y ModelBusAdapter del DSL expuesto.

Por ejemplo, supongamos que quiere almacenar referencias de ModelBus en elementos de un DSL MusicLibrary. Las referencias de ModelBus harán referencia a elementos del DSL FamilyTree. En el proyecto `Dsl` de la solución MusicLibrary, en el nodo Referencias, agregue referencias a los siguientes ensamblados:

- Fabrikam.FamilyTree.Dsl.dll: el DSL expuesto.

- Fabrikam.FamilyTree.ModelBusAdapters.dll: el adaptador de ModelBus del DSL expuesto.

- Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

- Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0

  Estos ensamblados se encuentran en el proyecto `ModelBusAdapters` del DSL expuesto, en `bin\*`.

  En el archivo de código donde creará las referencias, normalmente tendrá que importar estos espacios de nombres:

```csharp
// The namespace of the DSL you want to reference:
using Fabrikam.FamilyTree;  // Exposed DSL
using Fabrikam.FamilyTree.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling.Integration;
using System.Linq;
...
```

### <a name="to-create-a-reference-to-a-model"></a>Para crear una referencia a un modelo

Para crear una referencia de modelo, acceda al AdapterManager del DSL expuesto y úselo para crear una referencia al modelo. Puede especificar una ruta de acceso al archivo o un `EnvDTE.ProjectItem`.

Desde el AdapterManager, puede obtener un Adapter, que proporciona acceso a los elementos individuales del modelo.

> [!NOTE]
> Cuando haya terminado con un Adapter, deséchelo. La manera más conveniente de hacerlo es con una instrucción `using`. Esto se ilustra en el siguiente ejemplo:

```csharp
// The file path of a model instance of the FamilyTree DSL:
string targetModelFile = "TudorFamilyTree.ftree";
// Get the ModelBus service:
IModelBus modelBus =
    this.Store.GetService(typeof(SModelBus)) as IModelBus;
// Get an adapterManager for the target DSL:
FamilyTreeAdapterManager manager =
    (modelbus.GetAdapterManager(FamilyTreeAdapter.AdapterId)
     as FamilyTreeAdapterManager;
// or: (modelBus.FindAdapterManagers(targetModelFile).First())
// or could provide an EnvDTE.ProjectItem

// Create a reference to the target model:
// NOTE: the target model must be a file in this project.
ModelBusReference modelReference =
     manager.CreateReference(targetModelFile);
// or can use an EnvDTE.ProjectItem instead of the filename

// Get the root element of this model:
using (FamilyTreeAdapter adapter =
     modelBus.CreateAdapter(modelReference) as FamilyTreeAdapter)
{
  FamilyTree modelRoot = adapter.ModelRoot;
  // Access elements under the root in the usual way:
  foreach (Person p in modelRoot.Persons) {...}
  // You can create adapters for individual elements:
  ModelBusReference elementReference =
     adapter.GetElementReference(person);
  ...
} // Dispose adapter
```

Si quiere poder usar `modelReference` más adelante, puede almacenarla en una propiedad de dominio que tenga el tipo externo `ModelBusReference`:

```csharp
using Transaction t = this.Store.TransactionManager
    .BeginTransaction("keep reference"))
{
  artist.FamilyTreeReference = modelReference;
  t.Commit();
}
```

Para que los usuarios puedan editar esta propiedad de dominio, use `ModelReferenceEditor` como parámetro en el atributo Editor. Para obtener más información, vea [permitir que el usuario edite una referencia](#editRef).

### <a name="to-create-a-reference-to-an-element"></a>Para crear una referencia a un elemento

El adaptador que creó para el modelo se puede usar para crear y resolver referencias.

```csharp
// person is an element in the FamilyTree model:
ModelBusReference personReference =
  adapter.GetElementReference(person);
```

Si quiere poder usar `elementReference` más adelante, puede almacenarla en una propiedad de dominio que tenga el tipo externo `ModelBusReference`. Para que los usuarios puedan editarla, use `ModelElementReferenceEditor` como parámetro en el atributo Editor. Para obtener más información, vea [permitir que el usuario edite una referencia](#editRef).

### <a name="resolving-references"></a>Resolver referencias

Si tiene una `ModelBusReference` (MBR), puede obtener el modelo o el elemento de modelo al que hace referencia. Si el elemento está presente en un diagrama o en otra vista, puede abrir la vista y seleccionar el elemento.

Puede crear un adaptador desde una MBR. En el adaptador, puede obtener la raíz del modelo. También puede resolver las MBR que hacen referencia a elementos específicos dentro del modelo.

```csharp
using Microsoft.VisualStudio.Modeling.Integration; ...
ModelBusReference elementReference = ...;

// Get the ModelBus service:
IModelBus modelBus =
    this.Store.GetService(typeof(SModelBus)) as IModelBus;
// Use a model reference or an element reference
// to obtain an adapter for the target model:
using (FamilyTreeAdapter adapter =
   modelBus.CreateAdapter(elementReference) as FamilyTreeAdapter)
   // or CreateAdapter(modelReference)
{
  // Get the root of the model:
  FamilyTree tree = adapter.ModelRoot;

  // Get a model element:
  MyDomainClass mel =
    adapter.ResolveElementReference<MyDomainClass>(elementReference);
  if (mel != null) {...}

  // Get the diagram or other view, if there is one:
  ModelBusView view = adapter.GetDefaultView();
  if (view != null)
  {
   view.Open();
   // Display the diagram:
   view.Show();
   // Attempt to select the shape that presents the element:
   view.SetSelection(elementReference);
  }
} // Dispose the adapter.
```

#### <a name="to-resolve-modelbus-references-in-a-text-template"></a>Para resolver las referencias de ModelBus en una plantilla de texto

1. El DSL al que quiere acceder debe tener un adaptador de ModelBus que se haya configurado para que las plantillas de texto puedan acceder. Para obtener más información, consulte [proporcionar acceso a un DSL](#provide).

2. Normalmente, se accederá a un DSL de destino usando una MBR almacenada en un DSL de origen. Por lo tanto, la plantilla incluye la directiva del DSL de origen, además del código para resolver la MBR. Para obtener más información acerca de las plantillas de texto, vea [generar código a partir de un lenguaje Domain-Specific](../modeling/generating-code-from-a-domain-specific-language.md).

   ```
   <#@ template debug="true" hostspecific="true"
   inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
   <#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
   <#@ output extension=".txt" #>
   <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
   <#@ assembly name = "System.Core" #>
   <#@ assembly name = "Company.CompartmentDragDrop.Dsl.dll" #>
   <#@ assembly name = "Company.CompartmentDragDrop.ModelBusAdapter.dll" #>
   <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
   <#@ import namespace="System.Linq" #>
   <#@ import namespace="Company.CompartmentDragDrop" #>
   <#@ import namespace="Company.CompartmentDragDrop.ModelBusAdapters" #>
   <# // Get source root from directive processor:
     ExampleModel source = this.ExampleModel;
     // This DSL has a MBR in its root:
   using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as ModelBusAdapter)
     {
     ModelBusAdapterManager manager = this.ModelBus.FindAdapterManagers(this.Host.ResolvePath("Sample.compDD1")).FirstOrDefault();
     ModelBusReference modelReference =
       manager.CreateReference(this.Host.ResolvePath("Sample.compDD1"));

     // Get the root element of this model:
     using (CompartmentDragDropAdapter adapter =
        this.ModelBus.CreateAdapter(modelReference) as CompartmentDragDropAdapter)
     {
       ModelRoot root = adapter.ModelRoot;
   #>
   [[<#= root.Name #>]]
   <#
     }
   #>
   ```

   Para obtener más información y un tutorial, vea [usar Visual Studio ModelBus en una plantilla de texto](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

## <a name="serializing-a-modelbusreference"></a>Serializar una ModelBusReference

Si quiere almacenar una `ModelBusReference` (MBR) en forma de cadena, puede serializarla:

```csharp
string serialized = modelBus.SerializeReference(elementReference);
// Store it anywhere, then get it back again:
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, null);
```

Una MBR que se serializa de esta manera es independiente del contexto. Si usa el adaptador de ModelBus simple basado en archivos, la MBR contiene una ruta de acceso al archivo absoluta. Esto es suficiente si los archivos de modelo de la instancia nunca se mueven. Sin embargo, los archivos de modelo normalmente serán elementos de un proyecto de Visual Studio. Los usuarios esperarán poder mover todo el proyecto a diferentes partes del sistema de archivos. También esperarán poder mantener el proyecto bajo control del código fuente y abrirlo en diferentes equipos. Los nombres de las rutas de acceso deben serializarse con relación a la ubicación del proyecto que contiene los archivos.

### <a name="serializing-relative-to-a-specified-file-path"></a>Serializar con relación a una ruta de acceso al archivo especificada

Una `ModelBusReference` contiene un `ReferenceContext`, que es un diccionario en el que se puede almacenar información, como la ruta de acceso al archivo respecto a la cual debe serializarse.

Para serializar con relación a una ruta de acceso:

```csharp
elementReference.ReferenceContext.Add(
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,
   currentProjectFilePath);
string serialized = modelBus.SerializeReference(elementReference);
```

Para recuperar la referencia de la cadena:

```csharp
ReferenceContext context = new ReferenceContext();
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,
    currentProjectFilePath);
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, context);
```

### <a name="modelbusreferences-created-by-other-adapters"></a>Referencias de ModelBus creadas por otros adaptadores
 La siguiente información resulta útil si quiere crear su propio adaptador.

 Un `ModelBusReference` (MBR) consta de dos partes: el encabezado MBR, que es deserializado por el bus de modelo y un específico del adaptador controlado por el administrador de adaptadores específico. Esto permite proporcionar su propio formato de serialización de adaptadores. Por ejemplo, podría hacer referencia a una base de datos en lugar de a un archivo, o podría almacenar información adicional en la referencia del adaptador. Su propio adaptador puede colocar información adicional en el `ReferenceContext`.

 Cuando se deserializa una MBR, se debe proporcionar un ReferenceContext, que se almacena en el objeto de MBR. Cuando se serializa una MBR, el adaptador usa el ReferenceContext almacenado para ayudar a generar la cadena. La cadena deserializada no contiene toda la información del ReferenceContext. Por ejemplo, en el adaptador simple basado en archivos, el ReferenceContext contiene una ruta de acceso al archivo raíz, que no se almacena en la cadena de la MBR serializada.

 La MBR se deserializa en dos etapas:

- `ModelBusReferencePropertySerializer` es el serializador estándar que trata el encabezado MBR. Usa el contenedor de propiedades `SerializationContext` estándar de DSL, que se almacena en el `ReferenceContext` usando la clave `ModelBusReferencePropertySerializer.ModelBusLoadContextKey`. En concreto, `SerializationContext` debería contener una instancia de `ModelBus`.

- Su adaptador de ModelBus trata con la parte de la MBR específica del adaptador. Puede usar la información adicional almacenada en el ReferenceContext de la MBR. El adaptador simple basado en archivos conserva las rutas de acceso del archivo raíz mediante las claves `FilePathLoadContextKey` y `FilePathSaveContextKey` .

     En un archivo de modelo, las referencias de adaptador solo se deserializan cuando se usan.

## <a name="to-create-a-model"></a>Para crear un modelo

### <a name="creating-opening-and-editing-a-model"></a>Crear, abrir y editar un modelo
 El siguiente fragmento se toma del ejemplo de equipo de estado en el sitio web de VMSDK. Muestra cómo usar referencias de ModelBus para crear y abrir un modelo, y para obtener el diagrama asociado al modelo.

 En esta muestra, el nombre del DSL de destino es StateMachine. De él derivan varios nombres, como el nombre de la clase de modelo y el nombre del ModelBusAdapter.

```csharp
using Fabrikam.StateMachine.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Integration;
using Microsoft.VisualStudio.Modeling.Integration.Shell;
using Microsoft.VisualStudio.Modeling.Shell;
...
// Create a new model.
ModelBusReference modelReference =
   StateMachineAdapterManager    .CreateStateMachineModel(modelName, fileName);
//Keep reference of new model in this model.
using (Transaction t = ...)
{
  myModelElement.ReferenceProperty = modelReference;
  t.Commit();
}
// Get the ModelBus service from Visual Studio.
IModelBus modelBus = Microsoft.VisualStudio.Shell.Package.
    GetGlobalService(typeof(SModelBus)) as IModelBus;
// Get a modelbus adapter on the new model.
ModelBusAdapter modelBusAdapter;
modelBus.TryCreateAdapter(modelReference,
    this.ServiceProvider, out modelBusAdapter);
using (StateMachineAdapter adapter =
      modelBusAdapter as StateMachineAdapter)
{
    if (adapter != null)
    {
        // Obtain a Diagram from the adapter.
        Diagram targetDiagram =
           ((StandardVsModelingDiagramView)
                 adapter.GetDefaultView()
            ).Diagram;

        using (Transaction t =
             targetDiagram.Store.TransactionManager
                .BeginTransaction("Update diagram"))
        {
            DoUpdates(targetDiagram);
            t.Commit();
        }

        // Display the new diagram.
        adapter.GetDefaultView().Show();
    }
}
```

## <a name="validating-references"></a>Validar referencias
 BrokenReferenceDetector prueba todas las propiedades de dominio en un almacén que pueda almacenar referencias de ModelBus. Solicita que se lleve a cabo la acción cuando se encuentra una. Esto resulta especialmente útil para métodos de validación. El siguiente método de validación prueba el almacén en un intento de guardar el modelo, y notifica las referencias que no funcionan en la ventana de errores:

```csharp
[ValidationMethod(ValidationCategories.Save)]
public void ValidateModelBusReferences(ValidationContext context)
{
  BrokenReferenceDetector.DetectBrokenReferences(this.Store,
    delegate(ModelElement element, // parent of property
             DomainPropertyInfo property, // identifies property
             ModelBusReference reference) // invalid reference
    {
      context.LogError(string.Format(INVALID_REF_FORMAT,
             property.Name,
             referenceState.Name,
             new ModelBusReferenceTypeConverter().
                 ConvertToInvariantString(reference)),
         "Reference",
         element);
      });
}}
private const string INVALID_REF_FORMAT =
    "The '{0}' domain property of ths ReferenceState instance "
  + "named '{1}' contains reference value '{2}' which is invalid";
```

## <a name="actions-performed-by-the-modelbus-extension"></a>Acciones realizadas por la extensión ModelBus

La siguiente información no es esencial, pero podría resultar útil si hace un uso intensivo de ModelBus.

La extensión ModelBus realiza los siguientes cambios en su solución de DSL.

Al hacer clic con el botón derecho en el diagrama de definición de DSL, haga clic en **Habilitar Modelbus** y seleccione **habilitar este DSL para usar Modelbus**:

- En el proyecto DSL, se agrega una referencia a **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

- En la definición de DSL, se agrega una referencia de tipo externo: `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference` .

   Puede ver la referencia en **DSL Explorer**, en **tipos de dominio**. Para agregar referencias de tipo externo manualmente, haga clic con el botón secundario en el nodo raíz.

- Se agrega un nuevo archivo de plantilla, **Dsl\GeneratedCode\ModelBusReferencesSerialization.TT**.

Cuando establezca el tipo de una propiedad de dominio en ModelBusReference y, a continuación, haga clic con el botón secundario en la propiedad y haga clic en **Habilitar propiedades específicas de ModelBusReference**:

- Se agregan varios atributos CLR a la propiedad de dominio. Puede verlos en el campo Custom Attributes (Atributos personalizados), en la ventana Properties (Propiedades). En **Dsl\GeneratedCode\DomainClasses.CS**, puede ver los atributos en la declaración de propiedad:

  ```csharp
  [System.ComponentModel.TypeConverter(typeof(
  Microsoft.VisualStudio.Modeling.Integration.ModelBusReferenceTypeConverter))]
  [System.ComponentModel.Editor(typeof(
    Microsoft.VisualStudio.Modeling.Integration.Picker
    .ModelReferenceEditor // or ModelElementReferenceEditor
    ), typeof(System.Drawing.Design.UITypeEditor))]
  [Microsoft.VisualStudio.Modeling.Integration.Picker
    .SupplyFileBasedBrowserConfiguration
    ("Choose a model file", "Target model|*.target")]
  ```

Al hacer clic con el botón derecho en el diagrama de definición de DSL, haga clic en **Habilitar ModelBus** y seleccione **exponer este DSL a ModelBus**:

- Se agrega un proyecto `ModelBusAdapter` a la solución.

- Se agrega una referencia a `ModelBusAdapter` al proyecto `DslPackage`. `ModelBusAdapter` tiene una referencia al `Dsl` proyecto.

- En **DslPackage\source.extention.TT**, `|ModelBusAdapter|` se agrega como componente MEF.

## <a name="see-also"></a>Consulta también

- [Cómo: Abrir un modelo desde un archivo en el código del programa](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [Cómo: Agregar un controlador para arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Usar ModelBus de Visual Studio en plantillas de texto](../modeling/using-visual-studio-modelbus-in-a-text-template.md)
