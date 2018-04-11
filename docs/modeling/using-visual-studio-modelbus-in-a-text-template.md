---
title: Uso de ModelBus de Visual Studio en una plantilla de texto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0184e3b543e509d0e523504c0ea07f6fcc36775f
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2018
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Usar ModelBus de Visual Studio en plantillas de texto
Si escribe plantillas de texto que lee un modelo que contenga [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hace referencia a ModelBus, desea resolver las referencias para tener acceso a los modelos de destino. En ese caso, tendrá que adaptar las plantillas de texto y los que se hace referencia lenguajes específicos de dominio (DSL):  
  
-   DSL que es el destino de las referencias debe tener un adaptador de ModelBus que está configurado para el acceso de las plantillas de texto. Si también tiene acceso DSL desde otro código, el adaptador ha vuelto a configurar sea necesario además del adaptador ModelBus estándar.  
  
     El Administrador de adaptador debe heredar de <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> y debe tener el atributo `[HostSpecific(HostName)]`.  
  
-   La plantilla debe heredar de <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
> [!NOTE]
>  Si desea leer modelos DSL que no contienen referencias de ModelBus, puede usar los procesadores de directivas que se generan en los proyectos DSL. Para obtener más información, consulte [modelos de acceso a partir de plantillas de texto](../modeling/accessing-models-from-text-templates.md).  
  
 Para obtener más información acerca de las plantillas de texto, consulte [generación de código en tiempo de diseño mediante el uso de plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>Crear un adaptador de Bus de modelo para el acceso de las plantillas de texto  
 Para resolver una referencia de ModelBus en una plantilla de texto, el destino DSL debe tener un adaptador compatible. Plantillas de texto que se ejecutan en un AppDomain independiente desde el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editores de documento y, por lo tanto, el adaptador debe cargar el modelo en lugar de tener acceso a ella a través de DTE.  
  
#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>Para crear un adaptador ModelBus que sea compatible con las plantillas de texto  
  
1.  Si la solución DSL de destino no tiene un **ModelBusAdapter** del proyecto, cree uno mediante el Asistente para la Modelbus extensión:  
  
    1.  Descargue e instale el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus de extensión, si aún no lo ha hecho. Para obtener más información, consulte [SDK de visualización y modelado](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
    2.  Abra el archivo de definición de DSL. Haga clic en la superficie de diseño y, a continuación, haga clic en **habilitar Modelbus**.  
  
    3.  En el cuadro de diálogo, seleccione **desea exponer este DSL para el ModelBus**. Puede seleccionar ambas opciones si desea que este DSL para exponer sus modelos y usar referencias a otros lenguajes DSL.  
  
    4.  Haga clic en **Aceptar**. Se agrega un nuevo proyecto "ModelBusAdapter" a la solución de DSL.  
  
    5.  Haga clic en **Transformar todas las plantillas de**.  
  
    6.  Recompilar la solución.  
  
2.  Si desea obtener acceso a DSL desde una plantilla de texto y del resto del código, por ejemplo, comando, duplicar el **ModelBusAdapter** proyecto:  
  
    1.  En el Explorador de Windows, copie y pegue la carpeta que contiene **ModelBusAdapter.csproj**.  
  
    2.  Cambiar el nombre de archivo del proyecto (por ejemplo, para **T4ModelBusAdapter.csproj**).  
  
    3.  En **el Explorador de soluciones**, haga clic en el nodo de soluciones, seleccione **agregar**y, a continuación, haga clic en **proyecto existente**. Busque el nuevo proyecto de adaptador, **T4ModelBusAdapter.csproj**.  
  
    4.  En cada uno de ellos `*.tt` archivo del nuevo proyecto, cambie el espacio de nombres.  
  
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
  
    -   Cambie la declaración de AdapterManagerBase para que herede de <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  
  
         `public partial class <#= dslName =>AdapterManagerBase :`  
  
         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`  
  
    -   Casi al final del archivo, reemplace el atributo HostSpecific antes de la clase AdapterManager. Quite la línea siguiente:  
  
         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`  
  
         Inserte la siguiente línea:  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Este atributo filtra el conjunto de adaptadores que está disponible cuando un consumidor de modelbus busca un adaptador.  
  
5.  **Transformar todas las plantillas** y recompile la solución. No debería producirse ningún error de compilación.  
  
## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>Escribir una plantilla de texto que puede resolver las referencias a ModelBus  
 Normalmente, comenzar con una plantilla que lee y genera los archivos de un "origen" ADSL. Esta plantilla usa la directiva que se genera en el proyecto DSL de origen para leer archivos de modelo de código fuente de la manera que se describe en [modelos de acceso a partir de plantillas de texto](../modeling/accessing-models-from-text-templates.md). Sin embargo, el origen de DSL contiene referencias de ModelBus a un DSL "destino". Por lo tanto, desea habilitar el código de plantilla resolver las referencias y tener acceso al destino ADSL. Por lo tanto debe adaptar la plantilla, siga estos pasos:  
  
-   Cambie la clase base de la plantilla para <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
-   Incluir `hostspecific="true"` en la directiva de plantilla.  
  
-   Agregar referencias de ensamblado para el destino de DSL y su adaptador y habilitar ModelBus.  
  
-   No necesita la directiva que se genera como parte del destino ADSL.  
  
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
  
 Cuando se ejecuta esta plantilla de texto, el `SourceDsl` directiva carga el archivo `Sample.source`. La plantilla puede tener acceso a los elementos de ese modelo, a partir de `this.ModelRoot`. El código puede usar las clases de dominio y propiedades de ese DSL.  
  
 Además, la plantilla puede resolver las referencias de ModelBus. Cuando las referencias del puntero en el modelo de destino, las directivas de ensamblado dejar que el código utiliza las clases de dominio y propiedades de DSL de ese modelo.  
  
-   Si no usa una directiva que se genera un proyecto de DSL, también debe incluir lo siguiente.  
  
    ```  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>  
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>  
    ```  
  
-   Use `this.ModelBus` para obtener acceso a ModelBus de la.  
  
## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Tutorial: Probar una plantilla de texto que usa ModelBus  
 En este tutorial, siga estos pasos:  
  
1.  Cree dos DSL. Un DSL, el *consumidor*, tiene un `ModelBusReference` propiedad que puede hacer referencia a la línea ADSL, el *proveedor*.  
  
2.  Crear dos adaptadores de ModelBus en el proveedor: uno para el acceso mediante plantillas de texto, el otro código normal.  
  
3.  Crear modelos de la instancia de la DSL en un solo proyecto experimental.  
  
4.  Establecer una propiedad de dominio en un modelo para que señale a otro modelo.  
  
5.  Escribir un controlador de doble clic que se abre el modelo que apunta.  
  
6.  Escribir una plantilla de texto que se puede cargar el primer modelo, siga la referencia al otro modelo y leer el otro modelo.  
  
#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Un DSL que tenga acceso a ModelBus de construcción  
  
1.  Cree una nueva solución DSL. En este ejemplo, seleccione la plantilla de solución de flujo de tareas. Establece el nombre del idioma en `MBProvider` y la extensión de nombre de archivo a ".provide".  
  
2.  En el diagrama de definición DSL, haga clic en una parte en blanco del diagrama que no está en la parte superior y, a continuación, haga clic en **habilitar Modelbus**.  
  
    -   Si no ve **habilitar Modelbus**, debe descargar e instalar la extensión de ModelBus de VMSDK. Buscar en el sitio VMSDK: [SDK de visualización y modelado](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
3.  En el **habilitar Modelbus** cuadro de diálogo, seleccione **exponer este DSL para el ModelBus**y, a continuación, haga clic en **Aceptar**.  
  
     Un nuevo proyecto, `ModelBusAdapter`, se agrega a la solución.  
  
 Ahora tiene un DSL que puede tener acceso a las plantillas de texto a través de ModelBus. Las referencias a él pueden resolverse en el código de comandos, controladores de eventos o reglas, todos ellos funcionan en el AppDomain del editor de archivos de modelo. Sin embargo, las plantillas de texto se ejecutan en un AppDomain independiente y no pueden tener acceso a un modelo cuando se está editando. Si desea tener acceso a ModelBus referencias a este DSL desde una plantilla de texto, debe tener un ModelBusAdapter independiente.  
  
#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Para crear un adaptador ModelBus que esté configurado para las plantillas de texto  
  
1.  En el Explorador de Windows, copie y pegue la carpeta que contiene ModelBusAdapter.csproj.  
  
     Nombre de la carpeta T4ModelBusAdapter.  
  
     Cambie el nombre del archivo de proyecto T4ModelBusAdapter.csproj.  
  
2.  En el Explorador de soluciones, agregue T4ModelBusAdapter a la solución MBProvider. Haga clic en el nodo de soluciones, seleccione **agregar**y, a continuación, haga clic en **proyecto existente**.  
  
3.  Haga clic en el nodo del proyecto T4ModelBusAdapter y, a continuación, haga clic en Propiedades. En la ventana de propiedades del proyecto, cambie la **nombre de ensamblado** y **Default Namespace** a `Company.MBProvider.T4ModelBusAdapters`.  
  
4.  En cada archivo *.tt T4ModelBusAdapter, inserte "T4" en la última parte del espacio de nombres, por lo que la línea es similar al siguiente.  
  
     `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`  
  
5.  En el `DslPackage` del proyecto, agregue una referencia de proyecto `T4ModelBusAdapter`.  
  
6.  En DslPackage\source.extension.tt, agregue la siguiente línea en `<Content>`.  
  
     `<MefComponent>|T4ModelBusAdapter|</MefComponent>`  
  
7.  En el `T4ModelBusAdapter` del proyecto, agregue una referencia a: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**  
  
8.  Abra T4ModelBusAdapter\AdapterManager.tt:  
  
    1.  Cambie la clase base de AdapterManagerBase por <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>. Esta parte del archivo ahora es similar al siguiente.  
  
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
  
    2.  Casi al final del archivo, inserte el siguiente atributo adicional delante de la clase AdapterManager.  
  
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
  
11. Compruebe que funciona la DSL presionando F5. En el proyecto experimental, abra `Sample.provider`. Cierre la instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Ahora se puede resolver las referencias de ModelBus a este DSL en plantillas de texto y también en código normal.  
  
#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Construir un DSL con una propiedad de dominio de referencia de ModelBus  
  
1.  Crear un nuevo DSL mediante la plantilla de solución de lenguaje mínima. Nombre del idioma MBConsumer y establezca la extensión de nombre de archivo a ".consume".  
  
2.  En el proyecto ADSL, agregue una referencia al ensamblado MBProvider DSL. Haga clic en `MBConsumer\Dsl\References` y, a continuación, haga clic en **Agregar referencia**. En el **examinar** ficha, busque `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`  
  
     Esto le permite crear código que utilice otra DSL. Si desea crear las referencias a varias DSL, agréguela también.  
  
3.  En el diagrama de definición DSL, haga clic en el diagrama y, a continuación, haga clic en **habilitar ModelBus**. En el cuadro de diálogo, seleccione **habilitar este DSL consumir el ModelBus**.  
  
4.  En la clase `ExampleElement`, agregar una nueva propiedad de dominio `MBR`y en la ventana Propiedades, establezca su tipo en `ModelBusReference`.  
  
5.  Haga clic en la propiedad de dominio en el diagrama y, a continuación, haga clic en **propiedades específicas de editar ModelBusReference**. En el cuadro de diálogo, seleccione **un elemento del modelo**.  
  
     Establezca el filtro de cuadro de diálogo de archivo a la siguiente.  
  
     `Provider File|*.provide`  
  
     La subcadena después de "&#124;" es un filtro para el cuadro de diálogo de selección de archivos. Puede establecer para permitir que los archivos mediante el uso de *.\*  
  
     En el **tipo de elemento de modelo** lista, escriba los nombres de uno o más dominios clases en el proveedor de DSL (por ejemplo, Company.MBProvider.Task). Pueden ser clases abstractas. Si deja en blanco la lista, el usuario puede establecer la referencia a cualquier elemento.  
  
6.  Cierre el cuadro de diálogo y **Transformar todas las plantillas**.  
  
 Ha creado un DSL que puede contener referencias a los elementos de otro ADSL.  
  
#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Crear una referencia de ModelBus a otro archivo en la solución  
  
1.  En la solución MBConsumer, presione CTRL + F5. Una instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se abre en el **MBConsumer\Debugging** proyecto.  
  
2.  Agregar una copia de Sample.provide a la **MBConsumer\Debugging** proyecto. Esto es necesario porque una referencia de ModelBus debe hacer referencia a un archivo en la misma solución.  
  
    1.  Haga clic en el proyecto de depuración, seleccione **agregar**y, a continuación, haga clic en **elemento existente**.  
  
    2.  En el **Agregar elemento** cuadro de diálogo, establezca el filtro en **todos los archivos (\*.\*)** .  
  
    3.  Vaya a `MBProvider\Debugging\Sample.provide` y, a continuación, haga clic en **agregar**.  
  
3.  Abra `Sample.consume`.  
  
4.  Haga clic en una forma de ejemplo y en la ventana Propiedades, haga clic en **[...]**  en la propiedad MBR. En el cuadro de diálogo, haga clic en **examinar** y seleccione `Sample.provide`. En la ventana de elementos, expanda el tipo de tarea y seleccione uno de los elementos.  
  
5.  Guarde el archivo.  
  
     (No cierre todavía la instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].)  
  
 Ha creado un modelo que contiene una referencia de ModelBus a un elemento de otro modelo.  
  
#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Resolver una referencia de ModelBus en una plantilla de texto  
  
1.  En la instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], abra un archivo de plantilla de texto de ejemplo. Establezca su contenido como se indica a continuación.  
  
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
  
    1.  El `hostSpecific` y `inherits` atributos de la `template` se debe establecer la directiva.  
  
    2.  El modelo de consumidor se tiene acceso de la manera habitual mediante el procesador de directivas que se generó en ese DSL.  
  
    3.  Las directivas de ensamblado e importación deben poder tener acceso a ModelBus y los tipos de proveedor de DSL.  
  
    4.  Si sabe que muchos MBR se relacionan con el mismo modelo, es mejor llamar a CreateAdapter solo una vez.  
  
2.  Guarde la plantilla. Compruebe que el archivo de texto resultante es similar al siguiente.  
  
    ```  
  
    ExampleElement1   
    ExampleElement2   
         ExampleElement2 is linked to Task: Task2  
  
    ```  
  
#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Resolver una referencia de ModelBus en un controlador de gestos  
  
1.  Cierre la instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], si se está ejecutando.  
  
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
  
4.  En la instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], abra `Debugging\Sample.consume`.  
  
5.  Haga doble clic en una forma.  
  
     Si ha configurado el MBR en ese elemento, el modelo que se hace referencia se abre y se selecciona el elemento que se hace referencia.  
  
## <a name="see-also"></a>Vea también  
 [Integrar modelos utilizando Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
