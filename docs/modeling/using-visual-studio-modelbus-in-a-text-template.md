---
title: Usar ModelBus en una plantilla de texto
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22a6c9cb035637347ffd501b5cf3b1038cd09369
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535946"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Usar ModelBus de Visual Studio en plantillas de texto

Si escribe plantillas de texto que lean un modelo que contenga referencias Visual Studio ModelBus, puede que desee resolver las referencias para tener acceso a los modelos de destino. En ese caso, tendrá que adaptar las plantillas de texto y los lenguajes específicos de dominio (DSL) a los que se hace referencia:

- El DSL que es el destino de las referencias debe tener un adaptador de ModelBus configurado para el acceso desde las plantillas de texto. Si también tiene acceso al DSL desde otro código, el adaptador reconfigurado es necesario además del adaptador de ModelBus estándar.

     El administrador de adaptadores debe heredar de [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)) y debe tener el atributo `[HostSpecific(HostName)]` .

- La plantilla debe heredar de [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140)).

> [!NOTE]
> Si desea leer modelos DSL que no contienen referencias de ModelBus, puede utilizar los procesadores de directivas que se generan en los proyectos de DSL. Para obtener más información, consulte [acceso a los modelos desde plantillas de texto](../modeling/accessing-models-from-text-templates.md).

Para obtener más información sobre las plantillas de texto, vea [generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

## <a name="create-a-model-bus-adapter-for-access-from-text-templates"></a>Creación de un adaptador de bus de modelo para el acceso desde plantillas de texto

Para resolver una referencia de ModelBus en una plantilla de texto, el DSL de destino debe tener un adaptador compatible. Las plantillas de texto se ejecutan en un AppDomain independiente de los editores de documentos de Visual Studio y, por tanto, el adaptador tiene que cargar el modelo en lugar de tener acceso a él a través de DTE.

1. Si la solución DSL de destino no tiene un proyecto de **ModelBusAdapter** , cree uno mediante el Asistente para extensiones de Modelbus:

    1. Descargue e instale la extensión de Visual Studio ModelBus, si aún no lo ha hecho. Para obtener más información, vea [SDK de visualización y modelado](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

    2. Abra el archivo de definición de DSL. Haga clic con el botón secundario en la superficie de diseño y haga clic en **Habilitar Modelbus**.

    3. En el cuadro de diálogo, seleccione **deseo exponer este DSL a ModelBus**. Puede seleccionar ambas opciones si quiere que este DSL exponga sus modelos y consuma referencias a otros DSL.

    4. Haga clic en **OK**. Se agrega un nuevo proyecto "ModelBusAdapter" a la solución de DSL.

    5. Haga clic en **transformar todas las plantillas**.

    6. Recompilar la solución.

2. Si desea tener acceso a la DSL desde una plantilla de texto y desde otro código, como comando, duplique el proyecto **ModelBusAdapter** :

    1. En el explorador de Windows, copie y pegue la carpeta que contiene **ModelBusAdapter. csproj**.

    2. Cambie el nombre del archivo de proyecto (por ejemplo, a **T4ModelBusAdapter. csproj**).

    3. En **Explorador de soluciones**, haga clic con el botón secundario en el nodo de la solución, seleccione **Agregar**y, a continuación, haga clic en **proyecto existente**. Busque el nuevo proyecto de adaptador, **T4ModelBusAdapter. csproj**.

    4. En cada `*.tt` archivo del nuevo proyecto, cambie el espacio de nombres.

    5. Haga clic con el botón secundario en el nuevo proyecto en **Explorador de soluciones** y, a continuación, haga clic en **propiedades**. En el editor de propiedades, cambie los nombres del ensamblado generado y del espacio de nombres predeterminado.

    6. En el proyecto DslPackage, agregue una referencia al nuevo proyecto Adapter para que tenga referencias a ambos adaptadores.

    7. En DslPackage\source.extension.tt, agregue una línea que haga referencia al nuevo proyecto de adaptador.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **Transformar todas las plantillas** y recompilar la solución. No se producirán errores de compilación.

3. En el nuevo proyecto de adaptador, agregue referencias a los siguientes ensamblados:

    - Microsoft.VisualStudio.TextTemplating.11.0
    - Microsoft. VisualStudio. TextTemplating. Modeling. 11.0

4. En AdapterManager.tt:

    - Cambie la declaración de AdapterManagerBase para que herede de [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)).

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - Cerca del final del archivo, reemplace el atributo HostSpecific antes de la clase AdapterManager. Quite la siguiente línea:

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Inserte la siguiente línea:

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Este atributo filtra el conjunto de adaptadores que está disponible cuando un consumidor de Modelbus busca un adaptador.

5. **Transformar todas las plantillas** y recompilar la solución. No se producirán errores de compilación.

## <a name="write-a-text-template-that-can-resolve-modelbus-references"></a>Escribir una plantilla de texto que pueda resolver referencias de ModelBus

Normalmente, comienza con una plantilla que lee y genera archivos a partir de un DSL de "origen". Esta plantilla usa la Directiva que se genera en el proyecto DSL de origen para leer los archivos de modelo de origen de la manera que se describe en [acceder a los modelos desde plantillas de texto](../modeling/accessing-models-from-text-templates.md). Sin embargo, el DSL de origen contiene referencias de ModelBus a un DSL de "destino". Por lo tanto, desea habilitar el código de plantilla para resolver las referencias y obtener acceso a la DSL de destino. Por lo tanto, debe adaptar la plantilla siguiendo estos pasos:

- Cambie la clase base de la plantilla a [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140)).

- Incluya `hostspecific="true"` en la Directiva de plantilla.

- Agregue referencias de ensamblado al DSL de destino y a su adaptador, y para habilitar ModelBus.

- No necesita la Directiva que se genera como parte del DSL de destino.

```
<#@ template debug="true" hostspecific="true" language="C#"
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
<#@ output extension=".txt" #>
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>
<#@ assembly name = "System.Core" #>
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
<#@ import namespace="Company.TargetDsl" #>
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>
<#@ import namespace="System.Linq" #>
<#
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.
  // In the source DSL Definition, the root element has a model reference:
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)
  {if (adapter != null)
   {
      // Get the root of the target model:
      TargetRoot target = adapter.ModelRoot;
    // The source DSL Definition has a class "SourceElement" embedded under the root.
    // (Let's assume they're all in the same model file):
    foreach (SourceElement sourceElement in source.Elements)
    {
      // In the source DSL Definition, each SourceElement has a MBR property:
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;
      // Resolve the target model element:
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);
#>
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.
<#
    }
  }}
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename
  // from a path that is relative to the text template.
#>
```

 Cuando se ejecuta esta plantilla de texto, la `SourceDsl` Directiva carga el archivo `Sample.source` . La plantilla puede tener acceso a los elementos de ese modelo, a partir de `this.ModelRoot` . El código puede utilizar las clases de dominio y las propiedades de ese DSL.

 Además, la plantilla puede resolver referencias de ModelBus. Cuando las referencias señalan al modelo de destino, las directivas de ensamblado permiten que el código use las clases de dominio y las propiedades de DSL del modelo.

- Si no usa una directiva generada por un proyecto DSL, también debe incluir lo siguiente.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- Use `this.ModelBus` para obtener acceso a ModelBus.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Tutorial: probar una plantilla de texto que usa ModelBus
 En este tutorial, se siguen estos pasos:

1. Construya dos DSL. Un DSL, el *consumidor*, tiene una `ModelBusReference` propiedad que puede hacer referencia al otro DSL, el *proveedor*.

2. Cree dos adaptadores de ModelBus en el proveedor: uno para el acceso por plantillas de texto, el otro para el código normal.

3. Cree modelos de instancia de los DSL en un solo proyecto experimental.

4. Establezca una propiedad de dominio en un modelo para que apunte al otro modelo.

5. Escriba un controlador de doble clic que abra el modelo al que se apunta.

6. Escriba una plantilla de texto que pueda cargar el primer modelo, siga la referencia al otro modelo y lea el otro modelo.

### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Construya un DSL que sea accesible para ModelBus

1. Cree una nueva solución de DSL. En este ejemplo, seleccione la plantilla de la solución flujo de tareas. Establezca el nombre de idioma en `MBProvider` y la extensión de nombre de archivo en ". proporcionar".

2. En el diagrama de definición de DSL, haga clic con el botón secundario en una parte en blanco del diagrama que no está cerca de la parte superior y, a continuación, haga clic en **Habilitar Modelbus**.

   Si no ve **Habilitar Modelbus**, descargue e instale la extensión de VMSDK Modelbus.

3. En el cuadro de diálogo **Habilitar Modelbus** , seleccione **exponer este DSL a Modelbus**y, a continuación, haga clic en **Aceptar**.

    Un nuevo proyecto, `ModelBusAdapter` , se agrega a la solución.

Ahora tiene un DSL al que se puede tener acceso a través de plantillas de texto a través de ModelBus. Las referencias a él se pueden resolver en el código de comandos, controladores de eventos o reglas, y todos ellos funcionan en el AppDomain del editor del archivo de modelo. Sin embargo, las plantillas de texto se ejecutan en un AppDomain independiente y no pueden tener acceso a un modelo cuando se está editando. Si desea tener acceso a las referencias de ModelBus a este DSL desde una plantilla de texto, debe tener un ModelBusAdapter independiente.

### <a name="create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Crear un adaptador de ModelBus que esté configurado para plantillas de texto

1. En el explorador de archivos, copie y pegue la carpeta que contiene *ModelBusAdapter. csproj*.

    Asigne a la carpeta el nombre **T4ModelBusAdapter**.

    Cambie el nombre del archivo de proyecto *T4ModelBusAdapter. csproj*.

2. En Explorador de soluciones, agregue T4ModelBusAdapter a la solución MBProvider. Haga clic con el botón secundario en el nodo de la solución, seleccione **Agregar**y, a continuación, haga clic en **proyecto existente**.

3. Haga clic con el botón secundario en el nodo del proyecto T4ModelBusAdapter y, a continuación, haga clic en propiedades. En la ventana Propiedades del proyecto, cambie el **nombre de ensamblado** y el **espacio de nombres predeterminado** a `Company.MBProvider.T4ModelBusAdapters` .

4. En cada archivo *. TT de T4ModelBusAdapter, inserte "T4" en la última parte del espacio de nombres, de modo que la línea sea similar a la siguiente.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. En el `DslPackage` proyecto, agregue una referencia de proyecto a `T4ModelBusAdapter` .

6. En DslPackage\source.extension.tt, agregue la siguiente línea en `<Content>` .

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. En el `T4ModelBusAdapter` proyecto, agregue una referencia a: **Microsoft. VisualStudio. TextTemplating. Modeling. 11.0**

8. Abra T4ModelBusAdapter\AdapterManager.tt:

   1. Cambie la clase base de AdapterManagerBase a [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)). Esta parte del archivo ahora es similar a la siguiente.

       ```
       namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters
       {
           /// <summary>
           /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer
           /// </summary>
           public partial class <#= dslName #>AdapterManagerBase
           : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager
           {
       ```

   2. Cerca del final del archivo, inserte el siguiente atributo adicional delante de la clase AdapterManager.

        `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

        El resultado es similar al siguiente.

       ```
       /// <summary>
       /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter
       /// </summary>
       [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]
       [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]
       [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]
       [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]
       public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase
       {
       }
       ```

9. Haga clic en **transformar todas las plantillas** en la barra de título de explorador de soluciones.

10. Presione **F5**.

11. Compruebe que el DSL funciona. En el proyecto experimental, Abra `Sample.provider` . Cierre la instancia experimental de Visual Studio.

    Las referencias de ModelBus a este DSL ahora se pueden resolver en plantillas de texto y también en código ordinario.

### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Construir un DSL con una propiedad de dominio de referencia de ModelBus

1. Cree un nuevo DSL con la plantilla de solución de idioma mínima. Asigne al idioma el nombre MBConsumer y establezca la extensión de nombre de archivo en ". consume".

2. En el proyecto DSL, agregue una referencia al ensamblado DSL de MBProvider. Haga clic con el botón secundario  `MBConsumer\Dsl\References` y, a continuación, haga clic en **Agregar referencia**. En la pestaña **examinar** , busque `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    Esto le permite crear código que utiliza el otro DSL. Si desea crear referencias a varios DSL, agréguelos también.

3. En el diagrama de definición de DSL, haga clic con el botón secundario en el diagrama y haga clic en **Habilitar ModelBus**. En el cuadro de diálogo, seleccione **habilitar este DSL para usar ModelBus**.

4. En la clase `ExampleElement` , agregue una nueva propiedad de dominio `MBR` y, en el ventana Propiedades, establezca su tipo en `ModelBusReference` .

5. Haga clic con el botón secundario en la propiedad de dominio en el diagrama y, a continuación, haga clic en **Editar propiedades específicas de ModelBusReference**. En el cuadro de diálogo, seleccione **un elemento de modelo**.

    Establezca el filtro del cuadro de diálogo de archivos en lo siguiente.

    `Provider File|*.provide`

    La subcadena después de "&#124;" es un filtro para el cuadro de diálogo de selección de archivos. Puede establecerlo para permitir cualquier archivo mediante *.\*

    En la lista **tipo de elemento de modelo** , escriba los nombres de una o más clases de dominio en el DSL de proveedor (por ejemplo, Company. MBProvider. Task). Pueden ser clases abstractas. Si deja la lista en blanco, el usuario puede establecer la referencia a cualquier elemento.

6. Cierre el cuadro de diálogo y **transforme todas las plantillas**.

   Ha creado un DSL que puede contener referencias a elementos de otro DSL.

### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Crear una referencia de ModelBus a otro archivo de la solución

1. En la solución MBConsumer, presione CTRL + F5. Se abre una instancia experimental de Visual Studio en el proyecto **MBConsumer\Debugging** .

2. Agregue una copia del ejemplo. proporcione al proyecto **MBConsumer\Debugging** . Esto es necesario porque una referencia de ModelBus debe hacer referencia a un archivo en la misma solución.

   1. Haga clic con el botón secundario en el proyecto de depuración, elija **Agregar**y, a continuación, haga clic en **elemento existente**.

   2. En el cuadro de diálogo **Agregar elemento** , establezca el filtro en **todos los archivos ( \* . \* )**.

   3. Vaya a `MBProvider\Debugging\Sample.provide` y, a continuación, haga clic en **Agregar**.

3. Abra `Sample.consume`.

4. Haga clic en una forma de ejemplo y, en el ventana Propiedades, haga clic en **[...]** en la propiedad MBR. En el cuadro de diálogo, haga clic en **examinar** y seleccione `Sample.provide` . En la ventana elementos, expanda la tarea tipo y seleccione uno de los elementos.

5. Guarde el archivo. (Aún no cierre la instancia experimental de Visual Studio).

   Ha creado un modelo que contiene una referencia de ModelBus a un elemento de otro modelo.

### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Resolver una referencia de ModelBus en una plantilla de texto

1. En la instancia experimental de Visual Studio, abra un archivo de plantilla de texto de ejemplo. Establezca su contenido como se indica a continuación.

    ```
    <#@ template debug="true" hostspecific="true" language="C#"
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>
    <#@ output extension=".txt" #>
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
    <#@ import namespace="Company.MBProvider" #>
    <#
      // Property provided by the Consumer directive processor:
      ExampleModel consumerModel = this.ExampleModel;
      // Iterate through Consumer model, listing the elements:
      foreach (ExampleElement element in consumerModel.Elements)
      {
    #>
       <#= element.Name #>
    <#
        if (element.MBR != null)
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))
      {
              // If we allowed multiple types or DSLs in the MBR, discover type here.
        Task task = adapter.ResolveElementReference<Task>(element.MBR);
    #>
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>
    <#
          }
      }
    #>

    ```

     Tenga en cuenta los puntos siguientes:

    - `hostSpecific` `inherits` Se deben establecer los atributos y de la `template` Directiva.

    - Se tiene acceso al modelo de consumidor de la manera habitual a través del procesador de directivas que se generó en ese DSL.

    - Las directivas de ensamblado e importación deben poder tener acceso a ModelBus y a los tipos del DSL del proveedor.

    - Si sabe que muchos MBR están vinculados al mismo modelo, es mejor llamar a CreateAdapter solo una vez.

2. Guarde la plantilla. Compruebe que el archivo de texto resultante es similar al siguiente.

    ```
    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2
    ```

### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Resolver una referencia de ModelBus en un controlador de gestos

1. Cierre la instancia experimental de Visual Studio, si se está ejecutando.

2. Agregue un archivo denominado *MBConsumer\Dsl\Custom.CS* y establezca su contenido en lo siguiente:

    ```csharp
    namespace Company.MB2Consume
    {
      using Microsoft.VisualStudio.Modeling.Integration;
      using Company.MB3Provider;

      public partial class ExampleShape
      {
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)
        {
          base.OnDoubleClick(e);
          ExampleElement element = this.ModelElement as ExampleElement;
          if (element.MBR != null)
          {
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))
            {
              Task task = adapter.ResolveElementReference<Task>(element.MBR);
              // Open a window on this model:
              ModelBusView view = adapter.GetDefaultView();
              view.Show();
              view.SetSelection(element.MBR);
            }
          }
        }
      }
    }
    ```

3. Presione **Ctrl** + **F5**.

4. En la instancia experimental de Visual Studio, Abra `Debugging\Sample.consume` .

5. Haga doble clic en una forma.

    Si ha establecido el MBR en ese elemento, se abre el modelo al que se hace referencia y se selecciona el elemento al que se hace referencia.

## <a name="see-also"></a>Consulte también

- [Integrar modelos mediante Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
