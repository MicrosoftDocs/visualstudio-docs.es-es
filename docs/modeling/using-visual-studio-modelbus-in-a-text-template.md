---
title: Usar ModelBus en una plantilla de texto
description: Obtenga información sobre cómo resolver las referencias para acceder a los modelos de destino si escribe plantillas de texto que leen un modelo que contiene Visual Studio ModelBus referencias.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2afe8de66b109793a4e15e8320c3f498a08b25ec
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388391"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Usar ModelBus de Visual Studio en plantillas de texto

Si escribe plantillas de texto que leen un modelo que contiene Visual Studio ModelBus referencias, es posible que desee resolver las referencias para acceder a los modelos de destino. En ese caso, debe adaptar las plantillas de texto y los lenguajes específicos de dominio (DSL) a los que se hace referencia:

- El DSL que es el destino de las referencias debe tener un adaptador de ModelBus configurado para el acceso desde plantillas de texto. Si también tiene acceso al DSL desde otro código, se requiere el adaptador reconfigurado además del adaptador de ModelBus estándar.

     El administrador del adaptador debe heredar [de VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)) y debe tener el atributo `[HostSpecific(HostName)]` .

- La plantilla debe heredar de [ModelBusEnabledTextTransformation.](/previous-versions/ee844263(v=vs.140))

> [!NOTE]
> Si desea leer modelos DSL que no contienen referencias de ModelBus, puede usar los procesadores de directivas que se generan en los proyectos DSL. Para obtener más información, vea [Accessing Models from Text Templates](../modeling/accessing-models-from-text-templates.md).

Para obtener más información sobre las plantillas de texto, vea Generación de código [en tiempo de diseño mediante plantillas de texto T4.](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

## <a name="create-a-model-bus-adapter-for-access-from-text-templates"></a>Creación de un adaptador de Bus de modelos para el acceso desde plantillas de texto

Para resolver una referencia de ModelBus en una plantilla de texto, el DSL de destino debe tener un adaptador compatible. Las plantillas de texto se ejecutan en un AppDomain independiente de los editores de documentos Visual Studio y, por tanto, el adaptador tiene que cargar el modelo en lugar de acceder a él a través de DTE.

1. Si la solución DSL de destino no tiene un **proyecto ModelBusAdapter,** cree uno mediante el Asistente para extensiones de Modelbus:

    1. Descargue e instale la extensión Visual Studio ModelBus, si aún no lo ha hecho. Para obtener más información, vea [SDK de visualización y modelado.](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)

    2. Abra el archivo de definición de DSL. Haga clic con el botón derecho en la superficie de diseño y, a continuación, **haga clic en Habilitar bus de modelo.**

    3. En el cuadro de diálogo, seleccione I want to expose this DSL to the ModelBus (Quiero **exponer este DSL a ModelBus).** Puede seleccionar ambas opciones si desea que este DSL exponga sus modelos y consuma referencias a otras DSL.

    4. Haga clic en **Aceptar**. Se agrega un nuevo proyecto "ModelBusAdapter" a la solución de DSL.

    5. Haga clic **en Transformar todas las plantillas.**

    6. Recompilar la solución.

2. Si desea acceder al DSL desde una plantilla de texto y desde otro código, como el comando , duplique el **proyecto ModelBusAdapter:**

    1. En Explorador de Windows, copie y pegue la carpeta que contiene **ModelBusAdapter.csproj**.

    2. Cambie el nombre del archivo de proyecto (por ejemplo, **a T4ModelBusAdapter.csproj).**

    3. En **Explorador de soluciones**, haga clic con el botón derecho en el nodo de la solución, seleccione **Agregar** y, a continuación, haga clic en **Proyecto existente.** Busque el nuevo proyecto de adaptador, **T4ModelBusAdapter.csproj**.

    4. En cada `*.tt` archivo del nuevo proyecto, cambie el espacio de nombres .

    5. Haga clic con el botón derecho en el nuevo **proyecto Explorador de soluciones,** a continuación, haga clic **en Propiedades**. En el editor de propiedades, cambie los nombres del ensamblado generado y el espacio de nombres predeterminado.

    6. En el proyecto DslPackage, agregue una referencia al nuevo proyecto de adaptador para que tenga referencias a ambos adaptadores.

    7. En DslPackage\source.extension.tt, agregue una línea que haga referencia al nuevo proyecto de adaptador.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **Transforme Todas las plantillas** y recompile la solución. No debe producirse ningún error de compilación.

3. En el nuevo proyecto de adaptador, agregue referencias a los ensamblados siguientes:

    - Microsoft.VisualStudio.TextTemplating.11.0
    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

4. En AdapterManager.tt:

    - Cambie la declaración de AdapterManagerBase para que herede de [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)).

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - Cerca del final del archivo, reemplace el atributo HostSpecific antes de la clase AdapterManager. Quite la línea siguiente:

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Inserte la línea siguiente:

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Este atributo filtra el conjunto de adaptadores que está disponible cuando un consumidor de modelbus busca un adaptador.

5. **Transforme Todas las plantillas** y recompile la solución. No debe producirse ningún error de compilación.

## <a name="write-a-text-template-that-can-resolve-modelbus-references"></a>Escribir una plantilla de texto que pueda resolver referencias de ModelBus

Normalmente, se comienza con una plantilla que lee y genera archivos a partir de un DSL de "origen". Esta plantilla usa la directiva que se genera en el proyecto DSL de origen para leer los archivos de modelo de origen de la manera que se describe en Acceso a modelos desde [plantillas de texto](../modeling/accessing-models-from-text-templates.md). Sin embargo, el DSL de origen contiene referencias de ModelBus a un DSL de "destino". Por lo tanto, quiere habilitar el código de plantilla para resolver las referencias y acceder al DSL de destino. Por lo tanto, debe adaptar la plantilla siguiendo estos pasos:

- Cambie la clase base de la plantilla a [ModelBusEnabledTextTransformation.](/previous-versions/ee844263(v=vs.140))

- Incluya `hostspecific="true"` en la directiva de plantilla.

- Agregue referencias de ensamblado al DSL de destino y su adaptador, y para habilitar ModelBus.

- No necesita la directiva que se genera como parte del DSL de destino.

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

 Cuando se ejecuta esta plantilla de texto, la `SourceDsl` directiva carga el archivo `Sample.source` . La plantilla puede tener acceso a los elementos de ese modelo, empezando por `this.ModelRoot` . El código puede usar las clases de dominio y las propiedades de ese DSL.

 Además, la plantilla puede resolver las referencias de ModelBus. Cuando las referencias apuntan al modelo de destino, las directivas de ensamblado permiten que el código use las clases de dominio y las propiedades del DSL de ese modelo.

- Si no usa una directiva generada por un proyecto DSL, también debe incluir lo siguiente.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- Use `this.ModelBus` para obtener acceso a ModelBus.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Tutorial: Probar una plantilla de texto que usa ModelBus
 En este tutorial, siga estos pasos:

1. Construya dos DSL. Un DSL, *consumer*, tiene una propiedad que puede hacer referencia al `ModelBusReference` otro DSL, el *proveedor*.

2. Cree dos adaptadores modelbus en el proveedor: uno para el acceso mediante plantillas de texto y el otro para código normal.

3. Cree modelos de instancia de las DSL en un único proyecto experimental.

4. Establezca una propiedad de dominio en un modelo para que apunte al otro modelo.

5. Escriba un controlador de doble clic que abra el modelo al que se apunta.

6. Escriba una plantilla de texto que pueda cargar el primer modelo, siga la referencia al otro modelo y lea el otro modelo.

### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Construcción de un DSL accesible para ModelBus

1. Cree una nueva solución DSL. En este ejemplo, seleccione la plantilla de solución Flujo de tareas. Establezca el nombre de idioma en `MBProvider` y la extensión de nombre de archivo en ".provide".

2. En el diagrama de definición de DSL, haga clic con el botón derecho en una parte en blanco del diagrama que no esté cerca de la parte superior y, a continuación, haga clic **en Habilitar bus de modelos.**

   Si no ve Habilitar **Modelbus,** descargue e instale la extensión ModelBus de VMSDK.

3. En el **cuadro de diálogo Habilitar Bus** de modelos , seleccione Exponer este DSL a **ModelBus** y, a continuación, haga clic **en Aceptar.**

    Se agrega un nuevo proyecto, , a `ModelBusAdapter` la solución.

Ahora tiene un DSL al que se puede acceder mediante plantillas de texto a través de ModelBus. Las referencias a él se pueden resolver en el código de comandos, controladores de eventos o reglas, que funcionan en el AppDomain del editor de archivos del modelo. Sin embargo, las plantillas de texto se ejecutan en un AppDomain independiente y no pueden tener acceso a un modelo cuando se está editando. Si desea acceder a las referencias de ModelBus a este DSL desde una plantilla de texto, debe tener un ModelBusAdapter independiente.

### <a name="create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Crear un adaptador de ModelBus configurado para plantillas de texto

1. En Explorador de archivos, copie y pegue la carpeta que contiene *ModelBusAdapter.csproj*.

    Asigne a la **carpeta el nombre T4ModelBusAdapter.**

    Cambie el nombre del archivo de *proyecto T4ModelBusAdapter.csproj*.

2. En Explorador de soluciones, agregue T4ModelBusAdapter a la solución MBProvider. Haga clic con el botón derecho en el nodo de la solución, **seleccione Agregar** y, a continuación, haga clic en **Proyecto existente.**

3. Haga clic con el botón derecho en el nodo de proyecto T4ModelBusAdapter y, a continuación, haga clic en Propiedades. En la ventana de propiedades del proyecto, cambie el nombre **del ensamblado y** el espacio de nombres **predeterminado** a `Company.MBProvider.T4ModelBusAdapters` .

4. En cada archivo *.tt de T4ModelBusAdapter, inserte "T4" en la última parte del espacio de nombres, de modo que la línea se parezca a la siguiente.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. En el `DslPackage` proyecto, agregue una referencia de proyecto a `T4ModelBusAdapter` .

6. En DslPackage\source.extension.tt, agregue la siguiente línea en `<Content>` .

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. En el `T4ModelBusAdapter` proyecto, agregue una referencia a: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**

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

9. Haga **clic en Transformar todas las** plantillas en la barra de título Explorador de soluciones.

10. Presione **F5**.

11. Compruebe que el DSL funciona. En el proyecto experimental, abra `Sample.provider` . Cierre la instancia experimental de Visual Studio.

    Las referencias de ModelBus a este DSL ahora se pueden resolver en plantillas de texto y también en código normal.

### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Construcción de un DSL con una propiedad de dominio de referencia de ModelBus

1. Cree un DSL mediante la plantilla de solución Lenguaje mínimo. Asigne al lenguaje el nombre MBConsumer y establezca la extensión de nombre de archivo en ".consume".

2. En el proyecto DSL, agregue una referencia al ensamblado DSL de MBProvider. Haga clic con el botón `MBConsumer\Dsl\References` derecho y, a continuación, **haga clic en Agregar referencia.** En la **pestaña** Examinar, busque `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    Esto le permite crear código que usa el otro DSL. Si desea crear referencias a varias DSL, agrégrélas también.

3. En el diagrama de definición de DSL, haga clic con el botón derecho en el diagrama y, a continuación, haga clic **en Habilitar ModelBus**. En el cuadro de diálogo, seleccione **Habilitar este DSL para consumir modelbus.**

4. En la clase , agregue una nueva propiedad de dominio y, en `ExampleElement` `MBR` la ventana Propiedades, establezca su tipo en `ModelBusReference` .

5. Haga clic con el botón derecho en la propiedad de dominio en el diagrama y, a continuación, haga clic **en Editar modeloBusReferencia de propiedades específicas**. En el cuadro de diálogo, seleccione **un elemento de modelo**.

    Establezca el filtro de cuadro de diálogo de archivo en lo siguiente.

    `Provider File|*.provide`

    La subcadena después de "&#124;" es un filtro para el cuadro de diálogo de selección de archivos. Puede establecerlo para permitir cualquier archivo mediante *.\*

    En la **lista Tipo de** elemento de modelo , escriba los nombres de una o varias clases de dominio en el DSL del proveedor (por ejemplo, Company.MBProvider.Task). Pueden ser clases abstractas. Si deja la lista en blanco, el usuario puede establecer la referencia en cualquier elemento.

6. Cierre el cuadro de diálogo y **transforme todas las plantillas.**

   Ha creado un DSL que puede contener referencias a elementos de otro DSL.

### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Creación de una referencia de ModelBus a otro archivo de la solución

1. En la solución MBConsumer, presione CTRL+F5. Se abre una instancia experimental Visual Studio en el **proyecto MBConsumer\Debugging.**

2. Agregue una copia de Sample.provide al **proyecto MBConsumer\Debugging.** Esto es necesario porque una referencia de ModelBus debe hacer referencia a un archivo de la misma solución.

   1. Haga clic con el botón derecho en el proyecto Depuración, **seleccione Agregar** y, a continuación, haga clic en **Elemento existente.**

   2. En el **cuadro de diálogo Agregar** elemento, establezca el filtro en Todos los archivos ( . **\* \* )**.

   3. Vaya a `MBProvider\Debugging\Sample.provide` y, a continuación, haga clic **en Agregar**.

3. Abra `Sample.consume`.

4. Haga clic en una forma de ejemplo y, en la ventana Propiedades, haga clic **en [...]** en la propiedad MBR. En el cuadro de diálogo, haga clic **en Examinar** y seleccione `Sample.provide` . En la ventana de elementos, expanda el tipo Tarea y seleccione uno de los elementos.

5. Guarde el archivo. (Aún no cierre la instancia experimental de Visual Studio).

   Ha creado un modelo que contiene una referencia de ModelBus a un elemento de otro modelo.

### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Resolución de una referencia de ModelBus en una plantilla de texto

1. En la instancia experimental de Visual Studio, abra un archivo de plantilla de texto de ejemplo. Establezca su contenido como se muestra a continuación.

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

    - Se `hostSpecific` deben establecer los atributos y de la directiva `inherits` `template` .

    - Se accede al modelo de consumidor de la manera habitual a través del procesador de directivas que se generó en ese DSL.

    - Las directivas de ensamblado e importación deben poder acceder a ModelBus y a los tipos del DSL del proveedor.

    - Si sabe que muchos MBR están vinculados al mismo modelo, es mejor llamar a CreateAdapter solo una vez.

2. Guarde la plantilla. Compruebe que el archivo de texto resultante sea similar al siguiente.

    ```
    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2
    ```

### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Resolución de una referencia de ModelBus en un controlador de gestos

1. Cierre la instancia experimental de Visual Studio, si se está ejecutando.

2. Agregue un archivo denominado *MBConsumer\Dsl\Custom.cs* y establezca su contenido en lo siguiente:

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

4. En la instancia experimental de Visual Studio, abra `Debugging\Sample.consume` .

5. Haga doble clic en una forma.

    Si ha establecido mbr en ese elemento, se abre el modelo al que se hace referencia y se selecciona el elemento al que se hace referencia.

## <a name="see-also"></a>Vea también

- [Integrar modelos mediante Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
