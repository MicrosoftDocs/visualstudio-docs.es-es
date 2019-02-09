---
title: Usar ModelBus en una plantilla de texto
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d048dc82d76cb8eb3e7cf00edb84126ba4cf15f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951259"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Usar ModelBus de Visual Studio en plantillas de texto
Si escribe plantillas de texto que leer un modelo que contiene las referencias de ModelBus de Visual Studio, es posible que desee resolver las referencias para obtener acceso a los modelos de destino. En ese caso, tendrá que adaptar las plantillas de texto y los lenguajes específicos de dominio que se hace referencia (DSL):

-   El DSL que es el destino de las referencias debe tener un adaptador de ModelBus que está configurado para el acceso desde las plantillas de texto. Si también acceder al DSL desde otro código, es necesario además del adaptador de ModelBus estándar el adaptador ha vuelto a configurar.

     El Administrador de adaptador debe heredar de <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> y debe tener el atributo `[HostSpecific(HostName)]`.

-   La plantilla debe heredar de <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.

> [!NOTE]
>  Si desea leer modelos DSL que no contienen referencias de ModelBus, puede usar los procesadores de directivas que se generan en los proyectos DSL. Para obtener más información, consulte [acceso a los modelos de plantillas de texto](../modeling/accessing-models-from-text-templates.md).

 Para obtener más información acerca de las plantillas de texto, consulte [generación de código de tiempo de diseño mediante el uso de plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>Creación de un adaptador de Bus de modelo para el acceso desde las plantillas de texto
 Para resolver una referencia de ModelBus en una plantilla de texto, el DSL de destino debe tener un adaptador compatible. Las plantillas de texto que se ejecutan en un AppDomain independiente de los editores de documento de Visual Studio y, por lo tanto, el adaptador se tiene que cargar el modelo en lugar de tener acceso a él a través de DTE.

#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>Para crear un adaptador de ModelBus que sea compatible con las plantillas de texto

1.  Si la solución de DSL de destino no tiene un **ModelBusAdapter** del proyecto, cree uno mediante el Asistente para la Modelbus extensión:

    1.  Descargue e instale la ModelBus extensión de Visual Studio, si aún no lo ha hecho. Para obtener más información, consulte [SDK de visualización y modelado](http://go.microsoft.com/fwlink/?LinkID=185579).

    2.  Abra el archivo de definición de DSL. Haga clic en la superficie de diseño y, a continuación, haga clic en **habilitar Modelbus**.

    3.  En el cuadro de diálogo, seleccione **quiero exponer este DSL a ModelBus**. Puede seleccionar ambas opciones si desea que este DSL exponga sus modelos y consumir referencias a otros DSL.

    4.  Haga clic en **Aceptar**. Se agrega un nuevo proyecto "ModelBusAdapter" a la solución de DSL.

    5.  Haga clic en **Transformar todas las plantillas**.

    6.  Recompilar la solución.

2.  Si desea acceder al DSL desde una plantilla de texto y desde otro código, por ejemplo, el comando, duplicar el **ModelBusAdapter** proyecto:

    1.  En el Explorador de Windows, copie y pegue la carpeta que contiene **ModelBusAdapter.csproj**.

    2.  Cambiar el nombre de archivo del proyecto (por ejemplo, para **T4ModelBusAdapter.csproj**).

    3.  En **el Explorador de soluciones**, haga clic en el nodo de solución, seleccione **agregar**y, a continuación, haga clic en **proyecto existente**. Busque el nuevo proyecto de adaptador, **T4ModelBusAdapter.csproj**.

    4.  En cada `*.tt` archivo del proyecto nuevo, cambie el espacio de nombres.

    5.  Haga clic en el nuevo proyecto en el Explorador de soluciones y, a continuación, haga clic en Propiedades. En el editor de propiedades, cambie los nombres de ensamblado generado y el espacio de nombres predeterminado.

    6.  En el proyecto DslPackage, agregue una referencia al nuevo proyecto de adaptador para que tenga las referencias a ambos adaptadores.

    7.  En DslPackage\source.extension.tt, agregue una línea que hace referencia a su nuevo proyecto de adaptador.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8.  **Transformar todas las plantillas** y recompile la solución. No debería producirse ningún error de compilación.

3.  En el nuevo proyecto de adaptador, agregue referencias a los ensamblados siguientes:

    -   Microsoft.VisualStudio.TextTemplating.11.0

         Microsoft.VisualStudio.TextTemplating.Modeling.11.0

4.  En AdapterManager.tt:

    -   Cambie la declaración de adaptermanagerbase por para que herede de <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    -   Casi al final del archivo, reemplace el atributo HostSpecific antes de la clase AdapterManager. Quite la línea siguiente:

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Inserte la siguiente línea:

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Este atributo filtra el conjunto de adaptadores que está disponible cuando un consumidor de modelbus busca un adaptador.

5.  **Transformar todas las plantillas** y recompile la solución. No debería producirse ningún error de compilación.

## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>Escribir una plantilla de texto que se puede resolver las referencias de ModelBus
 Normalmente, comenzar con una plantilla que lee y genera archivos de un DSL "origen". Esta plantilla usa la directiva que se genera en el proyecto DSL de origen para leer archivos de modelo de código fuente de la manera en que se describe en [acceso a los modelos de plantillas de texto](../modeling/accessing-models-from-text-templates.md). Sin embargo, el DSL de origen contiene referencias de ModelBus a un DSL "target". Por lo tanto, desea habilitar el código de plantilla resolver las referencias y acceder a lo DSL de destino. Por tanto, debe adaptar la plantilla siguiendo estos pasos:

-   Cambie la clase base de la plantilla para <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.

-   Incluir `hostspecific="true"` en la directiva de plantilla.

-   Agregar referencias de ensamblado para el DSL de destino y su adaptador y habilitar ModelBus.

-   No necesita la directiva que se genera como parte del DSL de destino.

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

 Cuando se ejecuta esta plantilla de texto, el `SourceDsl` directiva carga el archivo `Sample.source`. La plantilla puede tener acceso a los elementos de ese modelo, a partir de `this.ModelRoot`. El código puede utilizar las clases de dominio y las propiedades de ese DSL.

 Además, la plantilla puede resolver las referencias de ModelBus. Cuando seleccione las referencias al modelo de destino, las directivas de ensamblado permitir que el código de usar las clases de dominio y las propiedades de DSL de ese modelo.

-   Si no usa una directiva que se genera un proyecto de DSL, también debe incluir lo siguiente.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

-   Use `this.ModelBus` para obtener acceso a ModelBus.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Tutorial: Prueba de una plantilla de texto que usa ModelBus
 En este tutorial, siga estos pasos:

1.  Construir dos DSL. Un DSL, la *consumidor*, tiene un `ModelBusReference` propiedad que puede hacer referencia a la línea ADSL, el *proveedor*.

2.  Cree dos adaptadores de ModelBus en el proveedor: uno para el acceso a las plantillas de texto, el otro código normal.

3.  Crear modelos de la instancia de los DSL en un solo proyecto experimental.

4.  Establecer una propiedad de dominio en un modelo para que apunte a otro modelo.

5.  Escribir un controlador de doble clic que se abre el modelo que señala.

6.  Escribir una plantilla de texto que se puede cargar el primer modelo, siga la referencia a otro modelo y el otro modelo de lectura.

#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Construir un DSL que puede tener acceso a ModelBus

1. Crear una nueva solución DSL. En este ejemplo, seleccione la plantilla de solución de flujo de tareas. Establece el nombre del idioma en `MBProvider` y la extensión de nombre de archivo a ".provide".

2. En el diagrama de definición de DSL, haga clic en una parte en blanco del diagrama que no se encuentra en la parte superior y, a continuación, haga clic en **habilitar Modelbus**.

   -   Si no ve **habilitar Modelbus**, debe descargar e instalar la extensión ModelBus de VMSDK. Puede encontrarlo en el sitio VMSDK: [SDK de modelado y](http://go.microsoft.com/fwlink/?LinkID=185579).

3. En el **habilitar Modelbus** cuadro de diálogo, seleccione **exponer este DSL a ModelBus**y, a continuación, haga clic en **Aceptar**.

    Un nuevo proyecto, `ModelBusAdapter`, se agrega a la solución.

   Ahora dispone de un DSL que puede tener acceso a las plantillas de texto a través de ModelBus. Las referencias a él pueden resolverse en el código de comandos, controladores de eventos o las reglas, que operan en el AppDomain del editor de archivos de modelo. Sin embargo, las plantillas de texto se ejecutan en un AppDomain independiente y no pueden tener acceso a un modelo cuando se está editando. Si desea tener acceso a las referencias de ModelBus a este DSL desde una plantilla de texto, debe tener un ModelBusAdapter independiente.

#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Para crear un adaptador de ModelBus que esté configurado para las plantillas de texto

1. En el Explorador de Windows, copie y pegue la carpeta que contiene ModelBusAdapter.csproj.

    Nombre de la carpeta T4ModelBusAdapter.

    Cambie el nombre del archivo de proyecto T4ModelBusAdapter.csproj.

2. En el Explorador de soluciones, agregue T4ModelBusAdapter a la solución MBProvider. Haga clic en el nodo de solución, elija **agregar**y, a continuación, haga clic en **proyecto existente**.

3. Haga clic en el nodo del proyecto T4ModelBusAdapter y, a continuación, haga clic en Propiedades. En la ventana Propiedades del proyecto, cambie el **nombre del ensamblado** y **Default Namespace** a `Company.MBProvider.T4ModelBusAdapters`.

4. En cada archivo *.tt T4ModelBusAdapter, inserte "T4" en la última parte del espacio de nombres, por lo que la línea es similar al siguiente.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. En el `DslPackage` proyecto, agregue una referencia al proyecto `T4ModelBusAdapter`.

6. En DslPackage\source.extension.tt, agregue la siguiente línea bajo `<Content>`.

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. En el `T4ModelBusAdapter` del proyecto, agregue una referencia al: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**

8. Abra T4ModelBusAdapter\AdapterManager.tt:

   1.  Cambie la clase base de AdapterManagerBase por <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>. Ahora esta parte del archivo es similar al siguiente.

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

   2.  Casi al final del archivo, inserte el siguiente atributo adicional frente a la clase AdapterManager.

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

9. Haga clic en **Transformar todas las plantillas** en la barra de título de solución de explorador.

10. Recompilar la solución. Haga clic en F5.

11. Comprobar que funciona el DSL, presione F5. En el proyecto experimental, abra `Sample.provider`. Cierre la instancia experimental de Visual Studio.

    Ahora se pueden resolver las referencias de ModelBus para este DSL en las plantillas de texto y en código normal.

#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Construir un DSL con una propiedad de dominio de referencia de ModelBus

1. Cree un DSL nuevo mediante el uso de la plantilla de solución de lenguaje mínimo. Nombre del lenguaje MBConsumer y establezca la extensión de nombre de archivo a ".consume".

2. En el proyecto DSL, agregue una referencia al ensamblado MBProvider DSL. Haga clic en `MBConsumer\Dsl\References` y, a continuación, haga clic en **Agregar referencia**. En el **examinar** pestaña, busque `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    Esto le permite crear código que usa otro DSL. Si desea crear referencias a varios DSL, agregarlos también.

3. En el diagrama de definición de DSL, haga clic en el diagrama y, a continuación, haga clic en **habilitar ModelBus**. En el cuadro de diálogo, seleccione **que este DSL pueda consumir el ModelBus**.

4. En la clase `ExampleElement`, agregue una nueva propiedad de dominio `MBR`y en la ventana Propiedades, establezca su tipo en `ModelBusReference`.

5. Haga clic en la propiedad de dominio en el diagrama y, a continuación, haga clic en **propiedades específicas de ModelBusReference editar**. En el cuadro de diálogo, seleccione **un elemento de modelo**.

    Establecer el filtro del cuadro de diálogo de archivo a la siguiente.

    `Provider File|*.provide`

    La subcadena después de "&#124;" es un filtro para el cuadro de diálogo de selección de archivo. Podría establecerlo para permitir que los archivos mediante el uso de *.\*

    En el **el tipo de elemento de modelo** lista, escriba los nombres de uno o más dominios clases en el proveedor de DSL (por ejemplo, Company.MBProvider.Task). Pueden ser clases abstractas. Si se deja en blanco la lista, el usuario puede establecer la referencia a cualquier elemento.

6. Cierre el cuadro de diálogo y **Transformar todas las plantillas**.

   Ha creado un DSL que puede contener referencias a elementos de otro DSL.

#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Crear una referencia de ModelBus a otro archivo en la solución

1. En la solución MBConsumer, presione CTRL + F5. Se abre una instancia experimental de Visual Studio en el **MBConsumer\Debugging** proyecto.

2. Agregar una copia de Sample.provide a la **MBConsumer\Debugging** proyecto. Esto es necesario porque una referencia de ModelBus debe hacer referencia a un archivo en la misma solución.

   1.  Haga clic en el proyecto de depuración, elija **agregar**y, a continuación, haga clic en **elemento existente**.

   2.  En el **Agregar elemento** cuadro de diálogo, establezca el filtro en **todos los archivos (\*.\*)** .

   3.  Vaya a `MBProvider\Debugging\Sample.provide` y, a continuación, haga clic en **agregar**.

3. Abra `Sample.consume`.

4. Haga clic en una forma de ejemplo y en la ventana Propiedades, haga clic en **[...]**  en la propiedad MBR. En el cuadro de diálogo, haga clic en **examinar** y seleccione `Sample.provide`. En la ventana de elementos, expanda el tipo de tarea y seleccione uno de los elementos.

5. Guarde el archivo.

    (No cierre todavía la instancia experimental de Visual Studio.)

   Ha creado un modelo que contiene una referencia de ModelBus a un elemento de otro modelo.

#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Resolver una referencia de ModelBus en una plantilla de texto

1.  En la instancia experimental de Visual Studio, abra un archivo de plantilla de texto de ejemplo. Establezca su contenido como sigue.

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

    1.  El `hostSpecific` y `inherits` los atributos de la `template` se debe establecer la directiva.

    2.  El modelo de consumidor se tiene acceso de la forma habitual a través del procesador de directivas que se generó en ese DSL.

    3.  Las directivas de ensamblado y la importación deben poder tener acceso a ModelBus y los tipos del proveedor de DSL.

    4.  Si sabe que muchas MBR se relacionan con el mismo modelo, es mejor llamar a CreateAdapter solo una vez.

2.  Guarde la plantilla. Compruebe que el archivo de texto resultante es similar al siguiente.

    ```

    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2

    ```

#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Resolver una referencia de ModelBus en un controlador de gestos

1.  Cierre la instancia experimental de Visual Studio, si se está ejecutando.

2.  Agregue un archivo denominado MBConsumer\Dsl\Custom.cs y establezca su contenido en el siguiente.

    ```

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

3.  Presione CTRL+F5.

4.  En la instancia experimental de Visual Studio, abra `Debugging\Sample.consume`.

5.  Haga doble clic en una forma.

     Si ha establecido el MBR en ese elemento, el modelo que se hace referencia se abre y se selecciona el elemento que se hace referencia.

## <a name="see-also"></a>Vea también

- [Integrar modelos mediante Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
