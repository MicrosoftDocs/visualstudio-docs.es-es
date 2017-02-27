---
title: "Integrar modelos utilizando Modelbus de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ff722f3-21d6-44e2-9efd-f6694aee9987
caps.latest.revision: 26
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 26
---
# Integrar modelos utilizando Modelbus de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus proporciona un método para crear vínculos entre modelos y desde otras herramientas en modelos. Por ejemplo, puede vincular modelos de lenguaje específico de dominio \(DSL\) y modelos UML. Puede crear un conjunto integrado de DSL.  
  
 ModelBus permite crear una referencia única a un modelo o a un elemento específico dentro de un modelo. Esta referencia se puede almacenar fuera del modelo, por ejemplo, en un elemento de otro modelo. Cuando en una ocasión, una herramienta quiera obtener acceso al elemento, la infraestructura de ModelBus cargará el modelo apropiado y devolver el elemento. Si lo desea, puede mostrar el modelo para el usuario. Si no se puede tener acceso al archivo en su ubicación anterior, ModelBus pedirá al usuario para encontrarlo. Si el usuario encuentra el archivo, ModelBus corregirá todas las referencias a ese archivo.  
  
> [!NOTE]
>  En el actual [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] implementación de ModelBus, los modelos vinculados debe ser elementos en la misma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solución.  
  
 Para obtener información adicional y código de ejemplo, consulte:  
  
-   [Cómo: Agregar un controlador para arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md)  
  
-   [Modelar el SDK de Visual Studio](http://www.microsoft.com/download/details.aspx?id=40754)  
  
##  <a name="provide"></a> Proporcionar acceso a un DSL  
 Antes de poder crear referencias de ModelBus a un modelo o sus elementos, debe definir un ModelBusAdapter para el DSL. La manera más fácil de hacerlo es utilizar el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensión del Bus de modelo, que agrega comandos al diseñador de DSL.  
  
###  <a name="expose"></a> Para exponer una definición de DSL a Modelbus  
  
1.  Descargue e instale la extensión Modelbus de Visual Studio, a menos que ya se ha instalado. Para obtener más información, consulte [SDK de visualización y modelado](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
2.  Abra el archivo de definición de DSL. Haga clic en la superficie de diseño y, a continuación, haga clic en **Habilitar Modelbus**.  
  
3.  En el cuadro de diálogo, elija **que deseo exponer este DSL a ModelBus de la**. Puede elegir ambas opciones si desea que este DSL exponga sus modelos y usar referencias a otros DSL.  
  
4.  Haga clic en **Aceptar**. Se agrega un nuevo proyecto "ModelBusAdapter" a la solución DSL.  
  
5.  Si desea acceder al DSL desde una plantilla de texto, debe modificar AdapterManager.tt en el nuevo proyecto. Omita este paso si desea acceder al DSL desde otro código, como comandos y controladores de eventos. Para obtener más información, consulta [Usar ModelBus de Visual Studio en plantillas de texto](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
    1.  Cambiar la clase base de adaptermanagerbase por <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  
  
    2.  Casi al final del archivo, inserte este atributo adicional frente a la clase AdapterManager:  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
    3.  En el proyecto de referencias de ModelBusAdapter, agregue **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**.  
  
     Si desea acceder al DSL de plantillas de texto y del resto del código, necesitará dos adaptadores, uno modificado y otro sin modificar.  
  
6.  Haga clic en **Transformar todas las plantillas de**.  
  
7.  Recompilar la solución.  
  
 Ahora es posible ModelBus puede abrir instancias de este DSL.  
  
 La carpeta `ModelBusAdapters\bin\*` contiene los ensamblados compilados por el `Dsl` proyecto y el `ModelBusAdapters` proyecto. Para hacer referencia a este DSL desde otro DSL, debe importar estos ensamblados.  
  
### Asegurarse de que pueden hacer referencia a elementos  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Adaptadores de ModelBus usan el guid de un elemento para identificarlo de forma predeterminada. Estos identificadores deben conservarse en el archivo del modelo.  
  
##### Para asegurarse de que el elemento se conserva los Id.  
  
1.  Abra DslDefinition.dsl.  
  
2.  En el Explorador de DSL, expanda **comportamiento de serialización Xml**, a continuación, **datos de la clase**.  
  
3.  Para cada clase a la que desea crear ModelBus hace referencia:  
  
     Haga clic en el nodo de clase y en la ventana Propiedades, asegúrese de que **serializar Id** está establecido en `true`.  
  
 Como alternativa, si desea utilizar nombres de elemento para identificar los elementos en lugar de GUID, puede reemplazar partes de los adaptadores generados. Invalidar los métodos siguientes en la clase de adaptador:  
  
-   Reemplazar `GetElementId` para devolver el identificador que se va a utilizar. Se llama a este método cuando se crean referencias.  
  
-   Reemplazar `ResolveElementReference` para localizar el elemento correcto en una referencia de ModelBus.  
  
##  <a name="editRef"></a> Acceso a un DSL desde otro DSL  
 Puede almacenar referencias de ModelBus en una propiedad de dominio de DSL y puede escribir código personalizado que utiliza. También puede permitir que el usuario cree una referencia de ModelBus seleccionando un archivo de modelo y un elemento dentro de él.  
  
 Para habilitar un DSL pueda usar referencias a otro DSL, debe convertirlo primero en un *consumidor* de referencias de ModelBus.  
  
#### Para habilitar un DSL pueda consumir referencias a un DSL expuesto  
  
1.  En el diagrama de la definición de DSL, haga clic en la parte principal del diagrama y, a continuación, haga clic en **Habilitar Modelbus**.  
  
2.  En el cuadro de diálogo, seleccione **Habilitar este modelo consumir referencias de ModelBus**.  
  
3.  En el proyecto Dsl de consumo, agregue los siguientes ensamblados a las referencias del proyecto. Encontrará estos ensamblados \(archivos .dll\) en el directorio ModelBusAdapter\\bin\\ \* del DSL expuesto.  
  
    -   El ensamblado del DSL expuesto, por ejemplo **Fabrikam.FamilyTree.Dsl.dll**  
  
    -   El modelo de bus de ensamblado del adaptador, por ejemplo **Fabrikam.FamilyTree.ModelBusAdapter.dll**  
  
4.  Agregue los siguientes ensamblados .NET a las referencias del proyecto DSL de consumo.  
  
    1.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
    2.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**  
  
#### Para almacenar una referencia de ModelBus en una propiedad de dominio  
  
1.  En la definición de DSL de consumo, agregue una propiedad de dominio a una clase de dominio y establezca su nombre.  
  
2.  En la ventana Propiedades, con la propiedad de dominio seleccionada, establezca **tipo** a `ModelBusReference`.  
  
 En esta fase, código de programa puede establecer el valor de propiedad, pero es de solo lectura en la ventana Propiedades.  
  
 Puede permitir a los usuarios establecer la propiedad con un editor de referencia de ModelBus especializado. Hay dos versiones de este editor o *selector:* uno permite a los usuarios elegir un archivo de modelo y la otra permite a los usuarios elegir un archivo de modelo y un elemento dentro del modelo.  
  
#### Para permitir al usuario establecer una referencia de ModelBus en una propiedad de dominio  
  
1.  Haga clic en la propiedad de dominio y, a continuación, haga clic en **propiedades específicas de ModelBusReference editar**. Abre un cuadro de diálogo. Se trata de la *selector de ModelBus*.  
  
2.  Seleccione el valor de **de ModelBusReference**: un modelo o a un elemento dentro de un modelo.  
  
3.  En la cadena de filtro del cuadro de diálogo de archivo, escriba una cadena como `Family Tree files |*.ftree`. Reemplace la extensión de archivo de su DSL expuesto.  
  
4.  Si decide hacer referencia a un elemento en un modelo, puede agregar una lista de tipos que el usuario puede seleccionar, por ejemplo, Company.FamilyTree.Person.  
  
5.  Haga clic en **Aceptar**, y, a continuación, haga clic en **Transformar todas las plantillas** en la barra de herramientas del explorador de soluciones.  
  
    > [!WARNING]
    >  Si no ha seleccionado un modelo o entidad válidos, el botón Aceptar no tendrá ningún efecto, incluso aunque aparezca habilitado.  
  
6.  Si especifica una lista de tipos de destino, como Company.FamilyTree.Person, a continuación, debe agregar una referencia de ensamblado al proyecto DSL, que hacen referencia a la DLL de destino DSL, por ejemplo, Company.FamilyTree.Dsl.dll  
  
#### Para probar una referencia de ModelBus  
  
1.  Compile los DSL expuestos y de consumo.  
  
2.  Ejecute uno de los lenguajes DSL en modo experimental presionando F5 o CTRL\+F5.  
  
3.  En el proyecto de depuración en la instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], agregar archivos que son instancias de cada DSL.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus solo puede resolver las referencias a modelos que son elementos de la misma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solución. Por ejemplo, no se puede crear una referencia a un archivo de modelo en otra parte del sistema de archivos.  
  
4.  Cree algunos elementos y vínculos en la instancia del DSL expuesto y guárdelo.  
  
5.  Abra una instancia de consumo y seleccione un elemento de modelo que tiene una propiedad de referencia de ModelBus.  
  
6.  En la ventana Propiedades, haga doble clic en la propiedad de referencia de ModelBus. Se abre el cuadro de diálogo del selector.  
  
7.  Haga clic en **Examinar** y seleccione la instancia del DSL expuesto.  
  
     El selector también le permitirá elegir un elemento en el modelo, si se especifica el tipo de elemento específico de la referencia de ModelBus.  
  
## Crear referencias en código de programa  
 Cuando desea almacenar una referencia a un modelo o un elemento dentro de un modelo, se crea un `ModelBusReference`. Hay dos tipos de `ModelBusReference`: las referencias y elemento de modelo.  
  
 Para crear una referencia de modelo, necesita el AdapterManager del DSL de que el modelo es una instancia y el nombre de archivo o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] elemento de proyecto del modelo.  
  
 Para crear una referencia de elemento, necesita un adaptador para el archivo del modelo y el elemento que desea consultar.  
  
> [!NOTE]
>  Con el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus, puede crear referencias a los elementos en la misma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solución.  
  
### Importar los ensamblajes DSL expuestos  
 En el proyecto, agregue referencias de proyecto a los ensamblados DSL y ModelBusAdapter del DSL expuesto.  
  
 Por ejemplo, suponga que desea almacenar referencias de ModelBus en elementos de un DSL MusicLibrary. Las referencias de ModelBus harán referencia a elementos del DSL FamilyTree. En el `Dsl` proyecto de la solución MusicLibrary, en el nodo referencias, agregue referencias a los ensamblados siguientes:  
  
-   Fabrikam.FamilyTree.Dsl.dll: el DSL expuesto.  
  
-   Fabrikam.FamilyTree.ModelBusAdapters.dll: el adaptador de ModelBus del DSL expuesto.  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0  
  
 Estos ensamblados se encuentran en el `ModelBusAdapters` proyecto del DSL expuesto, en `bin\*`.  
  
 En el archivo de código donde creará las referencias, normalmente tendrá que importar estos espacios de nombres:  
  
```  
// The namespace of the DSL you want to reference:  
using Fabrikam.FamilyTree;  // Exposed DSL  
using Fabrikam.FamilyTree.ModelBusAdapters;  
using Microsoft.VisualStudio.Modeling.Integration;  
using System.Linq;  
...  
```  
  
### Para crear una referencia a un modelo  
 Para crear una referencia de modelo, acceda al AdapterManager del DSL expuesto y usarlo para crear una referencia al modelo. Puede especificar una ruta de archivo, o un `EnvDTE.ProjectItem`.  
  
 Desde el AdapterManager, puede obtener un adaptador, que proporciona acceso a los elementos individuales en el modelo.  
  
> [!NOTE]
>  Debe eliminar un adaptador cuando haya terminado con él. Es la manera más conveniente para lograr esto con un `using` instrucción. Esto se ilustra en el siguiente ejemplo:  
  
```  
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
  
 Si desea poder usar `modelReference` más adelante, puede almacenarla en una propiedad de dominio que tenga el tipo externo `ModelBusReference`:  
  
```  
using Transaction t = this.Store.TransactionManager  
    .BeginTransaction("keep reference"))  
{  
  artist.FamilyTreeReference = modelReference;  
  t.Commit();  
}  
```  
  
 Para permitir a los usuarios editar esta propiedad de dominio, use `ModelReferenceEditor` como parámetro en el atributo Editor. Para obtener más información, consulte [Permitir que el usuario edite una referencia](#editRef).  
  
### Para crear una referencia a un elemento  
 El adaptador que ha creado para el modelo se puede utilizar para crear y resolver las referencias.  
  
```  
// person is an element in the FamilyTree model:  
ModelBusReference personReference =   
  adapter.GetElementReference(person);  
```  
  
 Si desea poder usar `elementReference` más adelante, puede almacenarla en una propiedad de dominio que tenga el tipo externo `ModelBusReference`. Para permitir que los usuarios puedan editarla, use `ModelElementReferenceEditor` como parámetro en el atributo Editor. Para obtener más información, consulte [Permitir que el usuario edite una referencia](#editRef).  
  
### Resolución de referencias  
 Si tiene un `ModelBusReference` \(MBR\) se puede obtener el modelo o el elemento del modelo al que hace referencia. Si el elemento está presente en un diagrama o en otra vista, puede abrir la vista y seleccione el elemento.  
  
 Puede crear un adaptador desde una MBR. Desde el adaptador, puede obtener la raíz del modelo. También puede resolver MBR que hacen referencia a elementos específicos dentro del modelo.  
  
```  
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
  
##### Para resolver referencias de ModelBus en una plantilla de texto  
  
1.  El DSL que desea tener acceso debe tener un adaptador de ModelBus que se ha configurado para el acceso a las plantillas de texto. Para obtener más información, consulta [Proporcionar acceso a un DSL](#provide).  
  
2.  Normalmente, se accederá a un destino DSL mediante una referencia de Bus de modelo \(MBR\) almacenado en un DSL de origen. Por lo tanto, la plantilla incluye la directiva del DSL de origen más código para resolver la MBR. Para obtener más información acerca de las plantillas de texto, consulte [Generar código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
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
  
 Para obtener más información y un tutorial, consulte [Usar ModelBus de Visual Studio en plantillas de texto](../modeling/using-visual-studio-modelbus-in-a-text-template.md)  
  
## Serializar una ModelBusReference  
 Si desea almacenar una `ModelBusReference` \(MBR\) en forma de cadena, puede serializar:  
  
```  
string serialized = modelBus.SerializeReference(elementReference);  
// Store it anywhere, then get it back again:  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, null);  
```  
  
 Un MBR que se serializa de esta manera es independiente del contexto. Si utiliza el adaptador de Bus de modelo basado en archivos simple, el MBR contiene una ruta de acceso absoluta del archivo. Esto es suficiente si nunca se mueven los archivos de modelo de instancia. Sin embargo, los archivos de modelo normalmente serán elementos en una [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto. Los usuarios esperan poder mover todo el proyecto a diferentes partes del sistema de archivos. También esperarán poder mantener el proyecto bajo control de código fuente y abrirlo en equipos diferentes. Por lo tanto, se deben serializar nombres de ruta de acceso relativa a la ubicación del proyecto que contiene los archivos.  
  
### Serializar con relación a una ruta de acceso de archivo especificado  
 Un `ModelBusReference` contiene un `ReferenceContext`, que es un diccionario en el que puede almacenar información como la ruta de acceso con respecto al cual debe serializarse.  
  
 Para serializar con relación a una ruta de acceso:  
  
```  
elementReference.ReferenceContext.Add(  
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,   
   currentProjectFilePath);  
string serialized = modelBus.SerializeReference(elementReference);  
```  
  
 Para recuperar la referencia de la cadena:  
  
```  
ReferenceContext context = new ReferenceContext();  
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,  
    currentProjectFilePath);  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, context);  
```  
  
### Referencias de ModelBus creadas por otros adaptadores  
 La siguiente información es útil si desea crear su propio adaptador.  
  
 Un `ModelBusReference` \(MBR\) consta de dos partes: el encabezado MBR, que se deserializa con el bus del modelo, y una específica del adaptador que se controla mediante el Administrador de adaptador específico. Esto le permite proporcionar su propio formato de serialización del adaptador. Por ejemplo, podría hacer referencia a una base de datos en lugar de un archivo, o podría almacenar información adicional en la referencia de adaptador. Su propio adaptador puede colocar información adicional en el `ReferenceContext`.  
  
 Cuando se deserializa una MBR, debe proporcionar un ReferenceContext, que se almacena en el objeto MBR. Cuando se serializa una MBR, el ReferenceContext almacenado se usa el adaptador para ayudar a generar la cadena. La cadena deserializada no contiene toda la información del referencecontext. Por ejemplo, en el adaptador simple basado en archivos, el ReferenceContext contiene una ruta de archivo raíz, que no se almacena en la cadena serializada de MBR.  
  
 El MBR se deserializa en dos fases:  
  
-   `ModelBusReferencePropertySerializer` es el serializador estándar que aborda el encabezado MBR. Utiliza el estándar DSL `SerializationContext` bolsa de propiedades, que se almacena en la `ReferenceContext` con la clave `ModelBusReferencePropertySerializer.ModelBusLoadContextKey`. En concreto, el `SerializationContext` debe contener una instancia de `ModelBus`.  
  
-   El adaptador de ModelBus trata la parte específica del adaptador del MBR. Puede utilizar la información adicional almacenada en el ReferenceContext de la MBR. El adaptador simple basado en el archivo mantiene las rutas de acceso de un archivo raíz mediante las teclas `FilePathLoadContextKey` y `FilePathSaveContextKey`.  
  
     Sólo cuando se utiliza, se deserializa una referencia de adaptador en un archivo de modelo.  
  
## Para crear un modelo  
  
### Crear, abrir y modificar un modelo  
 El siguiente fragmento de código se toma el ejemplo de la máquina de Estados en el sitio Web de VMSDK. Muestra el uso de ModelBus para crear y abrir un modelo y obtener el diagrama asociado al modelo.  
  
 En este ejemplo, el nombre del destino DSL es StateMachine. Varios nombres derivados de ella, como el nombre de la clase del modelo y el nombre del ModelBusAdapter.  
  
```  
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
  
## Validar referencias  
 BrokenReferenceDetector prueba todas las propiedades de dominio en un almacén que puede contener referencias de ModelBus. Llama a la acción que se proporcionan cuando se detecta cualquier acción. Esto es especialmente útil para los métodos de validación. El siguiente método de validación comprueba el almacén en un intento de guardar el modelo y notifica las referencias rotas en la ventana de errores:  
  
```  
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
  
## Acciones realizadas por la ModelBus extensión  
 La información siguiente no es esencial, pero puede resultar útil si hace un uso intensivo de ModelBus.  
  
 La ModelBus extensión realiza los cambios siguientes en la solución DSL.  
  
 Cuando hace doble clic en el diagrama de la definición de DSL, haga clic en **Habilitar Modelbus**, y, a continuación, seleccione **Habilitar este DSL consumir el ModelBus**:  
  
-   En el proyecto DSL, se agrega una referencia a **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
-   En la definición de DSL, se agrega una referencia de tipo externo: `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`.  
  
     Puede ver la referencia de **DSL Explorer**, en **tipos de dominio**. Para agregar referencias de tipo externo manualmente, haga clic en el nodo raíz.  
  
-   Se agrega un nuevo archivo de plantilla, **Dsl\\GeneratedCode\\ModelBusReferencesSerialization.tt**.  
  
 Cuando establece el tipo de una propiedad de dominio en ModelBusReference y, a continuación, haga clic en la propiedad y haga clic en **propiedades específicas de ModelBusReference habilitar**:  
  
-   Varios atributos CLR se agregan a la propiedad de dominio. Puede verlos en el campo de atributos personalizados en la ventana Propiedades. En **Dsl\\GeneratedCode\\DomainClasses.cs**, puede ver los atributos de la declaración de propiedad:  
  
    ```  
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
  
 Cuando haga clic en el diagrama de la definición de DSL, haga clic en **Habilitar ModelBus**, y seleccione **exponer este DSL a ModelBus de la**:  
  
-   Un nuevo proyecto `ModelBusAdapter` se agrega a la solución.  
  
-   Una referencia a `ModelBusAdapter` se agrega a la `DslPackage` proyecto.`ModelBusAdapter` tiene una referencia a la `Dsl` proyecto.  
  
-   En **DslPackage\\source.extention.tt**, `|ModelBusAdapter|` se agrega como un componente MEF.  
  
## Vea también  
 [Cómo: Abrir un modelo desde un archivo en el código del programa](../modeling/how-to-open-a-model-from-file-in-program-code.md)   
 [Integrar modelos UML con otros modelos y herramientas](../modeling/integrate-uml-models-with-other-models-and-tools.md)   
 [Cómo: Agregar un controlador para arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Usar ModelBus de Visual Studio en plantillas de texto](../modeling/using-visual-studio-modelbus-in-a-text-template.md)