---
title: "Usar ModelBus de Visual Studio en plantillas de texto | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: 13
caps.handback.revision: 13
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Usar ModelBus de Visual Studio en plantillas de texto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si escribe las plantillas de texto que leen un modelo que contenga las referencias de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus, quizás desee resolver referencias para tener acceso a los modelos de destino.  En ese caso, tiene que adaptar plantillas de texto y lenguajes \(DSLs\) específicos del dominio hace referencia:  
  
-   ADSL que es el destino de las referencias debería tener un adaptador de ModelBus configurada para el acceso de las plantillas de texto.  Si también tiene acceso a ADSL de otro código, el adaptador nuevo se requiere además de adaptador estándar de ModelBus.  
  
     El administrador del adaptador debe heredar de <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> y debe tener el atributo `[HostSpecific(HostName)]`.  
  
-   la plantilla debe heredar de <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
> [!NOTE]
>  Si desea leer los modelos ADSL que no contienen referencias de ModelBus, puede utilizar los procesadores de directivas que se generan en proyectos ADSL.  Para obtener más información, vea [Acceso a modelos a partir de plantillas de texto](../modeling/accessing-models-from-text-templates.md).  
  
 Para obtener más información acerca de las plantillas de texto, vea [Design\-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md)\).  
  
## Crear un adaptador modelo de bus para Access de plantillas de texto  
 Para resolver una referencia de ModelBus en una plantilla de texto, el destino ADSL debería tener un adaptador compatible.  Las plantillas de texto se ejecutan en un AppDomain independiente de los editores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , y por consiguiente el adaptador tiene que cargar el modelo en lugar de tenga acceso con DTE.  
  
#### Para crear un adaptador de ModelBus que es compatible con las plantillas de texto  
  
1.  Si la solución ADSL de destino no tiene un proyecto de **ModelBusAdapter** , cree una mediante el asistente de extensión de Modelbus:  
  
    1.  Descargar e instalar la extensión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus, si aún no lo ha hecho.  Para obtener más información, vea [El SDK de visualización y modelado](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
    2.  Abra el archivo de definición de ADSL.  Haga clic con el botón secundario en la superficie de diseño y haga clic en **permiso Modelbus**.  
  
    3.  En el cuadro de diálogo, seleccione **Deseo exponer este ADSL a ModelBus**.  Puede seleccionar ambas opciones si desea este ADSL para exponer los modelos y utilizar referencias al otro dominio \(ADSL\).  
  
    4.  Haga clic en **Aceptar**.  Un nuevo proyecto “ModelBusAdapter” se agrega a la solución ADSL.  
  
    5.  Haga clic en **Transformar todas las plantillas**.  
  
    6.  Recompilar la solución.  
  
2.  Si desea tener acceso a ADSL de una plantilla de texto y el otro código, como comando, duplicado el proyecto de **ModelBusAdapter** :  
  
    1.  En el Explorador de Windows, copie y pegue la carpeta que contiene **ModelBusAdapter.csproj**.  
  
    2.  Cambie el nombre del archivo de proyecto \(por ejemplo, a **T4ModelBusAdapter.csproj**\).  
  
    3.  En **Explorador de soluciones**, haga clic con el botón secundario en el nodo de la solución, elija **Agregar**, y haga clic en **Proyecto existente**.  Busque el nuevo proyecto de adaptadores, **T4ModelBusAdapter.csproj**.  
  
    4.  En cada archivo de `*.tt` del nuevo proyecto, cambie el espacio de nombres.  
  
    5.  Haga clic con el botón secundario en el nuevo proyecto en el explorador de soluciones y haga clic en propiedades.  En el editor de propiedades, cambie los nombres de ensamblado generado y el espacio de nombres predeterminado.  
  
    6.  En el proyecto de DslPackage, agregue una referencia al nuevo proyecto de adaptador de modo que tiene referencias a ambos adaptadores.  
  
    7.  En DslPackage \\ source.extension.tt, agregue una línea que haga referencia al nuevo proyecto de adaptador.  
  
        ```  
        <MefComponent>|T4ModelBusAdapter|</MefComponent>  
        ```  
  
    8.  **Transformar todas las plantillas** y recompile la solución.  Ningún error de compilación deben aparecer.  
  
3.  En el nuevo proyecto de adaptadores, agregue referencias a los ensamblados siguientes:  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
         Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
4.  en AdapterManager.tt:  
  
    -   Cambie la declaración de AdapterManagerBase de forma que herede de <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  
  
         `public partial class <#= dslName =>AdapterManagerBase :`  
  
         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`  
  
    -   Cerca del final del archivo, reemplace el atributo HostSpecific antes de la clase de AdapterManager.  Quite la línea siguiente:  
  
         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`  
  
         Inserte la línea siguiente:  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Este atributo filtra el conjunto de adaptadores que está disponible cuando un consumidor de modelbus busca un adaptador.  
  
5.  **Transformar todas las plantillas** y recompile la solución.  Ningún error de compilación deben aparecer.  
  
## Escribiendo en una resolución ModelBus de Que Pueden de plantilla de texto referencias  
 Normalmente, se inicia con una plantilla que lea y genere archivos “origen” ADSL.  Esta plantilla utiliza la directiva que se genera en el proyecto ADSL de origen de leer los archivos de modelo de origen de la manera en que se describe en [Acceso a modelos a partir de plantillas de texto](../modeling/accessing-models-from-text-templates.md).  Sin embargo, el origen ADSL contiene las referencias de ModelBus a “destino” ADSL.  Por lo tanto desea permitir que el código de plantilla para resolver las referencias y tener acceso al destino ADSL.  Por lo tanto debe adaptar la plantilla siguiendo estos pasos:  
  
-   cambie la clase base de la plantilla a <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
-   Incluyen `hostspecific="true"` en la directiva template.  
  
-   Agregue las referencias de ensamblado al destino ADSL y al adaptador, y habilitar ModelBus.  
  
-   No necesita la directiva que se presenta como parte de destino ADSL.  
  
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
    // (Let’s assume they’re all in the same model file):  
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
  
 Cuando se ejecuta esta plantilla de texto, la directiva de `SourceDsl` carga el archivo `Sample.source`.  La plantilla puede tener acceso a elementos de ese modelo, de `this.ModelRoot`.  El código puede utilizar las clases de dominio y las propiedades de ese ADSL.  
  
 además, la plantilla puede resolver las referencias de ModelBus.  Donde el punto de referencias al modelo de destino, las directivas de ensamblado mediante el uso de código las clases de dominio y propiedades ADSL de ese modelo.  
  
-   Si no utiliza una directiva generada por un proyecto ADSL, también debe incluir lo siguiente.  
  
    ```  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>  
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>  
    ```  
  
-   Utilice `this.ModelBus` para obtener acceso al ModelBus.  
  
## tutorial: Prueba una plantilla Que de texto utiliza ModelBus  
 En este tutorial, sigue estos pasos:  
  
1.  Construcción dos dominio \(ADSL\).  Un DSL, *el consumidor*, tiene una propiedad que puede hacer referencia al otro DSL, *el proveedor*de `ModelBusReference` .  
  
2.  cree dos adaptadores de ModelBus en el proveedor: uno para el acceso de las plantillas de texto, otro para el código normal.  
  
3.  Cree modelos de la instancia del dominio \(ADSL\) en un solo proyecto experimental.  
  
4.  Establezca una propiedad de dominio en un modelo para señalar el otro modelo.  
  
5.  Escriba un controlador de doble clic que abra el modelo al que se señala.  
  
6.  Escriba una plantilla de texto que se puede cargar el primer modelo, siga la referencia al otro modelo, y leer otro modelo.  
  
#### Construya ADSL que es accesible a ModelBus  
  
1.  Cree una nueva solución ADSL.  Para este ejemplo, seleccione la plantilla de solución de flujo de la tarea.  Establezca el nombre del idioma a `MBProvider` y la extensión de nombre de archivo a “.provide”.  
  
2.  En el diagrama de la definición de DSL, haga clic con el botón secundario en un espacio en blanco del diagrama que no está cerca de la parte superior, y haga clic en **permiso Modelbus**.  
  
    -   Si no ve **permiso Modelbus**, debe descargar e instalar la extensión de VMSDK ModelBus.  encuentrelo en el sitio de VMSDK: [El SDK de visualización y modelado](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
3.  En el cuadro de diálogo de **habilite Modelbus** , **Expone este ADSL a ModelBus**seleccione, y haga clic en **Aceptar**.  
  
     un nuevo proyecto, `ModelBusAdapter`, se agrega a la solución.  
  
 Ahora tiene ADSL que puedan obtener acceso plantillas de texto con ModelBus.  Las referencias a ella se pueden resolver en el código de comandos, de controladores de eventos, o de las reglas, que funcionan en AppDomain de editor modelo de archivo.  Sin embargo, el texto al funcionamiento de las plantillas en un AppDomain independiente y no puede tener acceso a un modelo cuando se edita.  Si desea tener acceso a las referencias de ModelBus a este ADSL de una plantilla de texto, debe tener un ModelBusAdapter independiente.  
  
#### Para crear un adaptador de ModelBus configurada para las plantillas de texto  
  
1.  En el Explorador de Windows, copie y pegue la carpeta que contiene ModelBusAdapter.csproj.  
  
     Llame a la carpeta T4ModelBusAdapter.  
  
     Cambie el nombre del archivo de proyecto T4ModelBusAdapter.csproj.  
  
2.  En el explorador de soluciones, agregue T4ModelBusAdapter a la solución de MBProvider.  Haga clic con el botón secundario en el nodo de la solución, elija **Agregar**, y haga clic en **Proyecto existente**.  
  
3.  Haga clic con el botón secundario en el proyecto de T4ModelBusAdapter y haga clic en propiedades.  En la ventana propiedades del proyecto, cambie **Nombre del ensamblado** y **espacio de nombres predeterminado** a `Company.MBProvider.T4ModelBusAdapters`.  
  
4.  En cada archivo de \*.tt en T4ModelBusAdapter, inserción “T4” en la última parte del espacio de nombres, de modo que la línea se asemeje a lo siguiente.  
  
     `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`  
  
5.  En el proyecto de `DslPackage` , agregue una referencia de proyecto a `T4ModelBusAdapter`.  
  
6.  En DslPackage \\ source.extension.tt, agregue la línea siguiente en `<Content>`.  
  
     `<MefComponent>|T4ModelBusAdapter|</MefComponent>`  
  
7.  en el proyecto de `T4ModelBusAdapter` , agregue una referencia a: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**  
  
8.  T4ModelBusAdapter abierto \\AdapterManager .tt:  
  
    1.  cambie la clase base de AdapterManagerBase a <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  Esta parte del archivo se parece ahora al siguiente.  
  
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
  
    2.  Cerca del final del archivo, inserte el atributo adicional siguiente delante de la clase AdapterManager.  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         El resultado se parece a lo siguiente.  
  
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
  
9. Haga clic en **Transformar todas las plantillas** en la barra de título del explorador de soluciones.  
  
10. Recompilar la solución.  F5 en.  
  
11. Compruebe que ADSL funciona presionando F5.  En el proyecto experimental, abra `Sample.provider`.  Cierre la instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Las referencias de ModelBus a este ADSL ahora se puede resolver en plantillas de texto y también en código normal.  
  
#### Construya ADSL con una propiedad del dominio de la referencia de ModelBus  
  
1.  Cree nuevo ADSL mediante la plantilla de solución de lenguaje mínimos.  Llame al lenguaje MBConsumer y establezca la extensión de nombre de archivo a “.consume”.  
  
2.  En el proyecto ADSL, agregue una referencia al ensamblado de MBProvider ADSL.  Haga clic con el botón secundario en `MBConsumer\Dsl\References` y haga clic en **Agregar referencia**.  En la pestaña de **Examinar** , busque `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`  
  
     Esto permite crear código que utiliza el otro ADSL.  Si desea crear referencias a varios dominio \(ADSL\), agréguelos también.  
  
3.  En el diagrama de la definición de DSL, haga clic con el botón secundario en el diagrama y haga clic en **permiso ModelBus**.  En el cuadro de diálogo, seleccione **Permite a este ADSL para consumir el ModelBus**.  
  
4.  En la clase `ExampleElement`, agregue una nueva propiedad `MBR`de dominio, y en la ventana Propiedades, establezca su tipo en `ModelBusReference`.  
  
5.  Haga clic con el botón secundario en la propiedad del dominio en el diagrama y haga clic en **Propiedades específicas de ModelBusReference de edición**.  En el cuadro de diálogo, seleccione **un elemento de modelo**.  
  
     Establecer el filtro del cuadro de diálogo de archivos al siguiente.  
  
     `Provider File|*.provide`  
  
     la subcadena después “&#124;” es un filtro del cuadro de diálogo de selección de archivos.  Puede establecerlo para permitir cualquier archivo mediante \*.\*  
  
     En la lista de **Tipo de elemento de modelo** , escriba los nombres de un mineral más clases de dominio en el proveedor ADSL \(por ejemplo, Company.MBProvider.Task\).  pueden ser clases abstractas.  Si se deja en blanco la lista, puede establecer la referencia a cualquier elemento.  
  
6.  Cierre el cuadro de diálogo y **Transformar todas las plantillas**.  
  
 Ha creado un ADSL que puede contener referencias a elementos en otro ADSL.  
  
#### Cree una referencia de ModelBus a otro archivo de la solución  
  
1.  en la solución de MBConsumer, presione CTRL\+F5.  Una instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se abre en el proyecto de **MBConsumer\\Debugging** .  
  
2.  Agregue una copia de Sample.provide al proyecto de **MBConsumer\\Debugging** .  Esto es necesario porque una referencia de ModelBus debe hacer referencia a un archivo en la misma solución.  
  
    1.  Haga clic con el botón secundario en el proyecto de depuración, elija **Agregar**, y haga clic en **Elemento existente**.  
  
    2.  En el cuadro de diálogo **Agregar elemento** , establezca el filtro a **Todos los archivos \(\*.\*\)**.  
  
    3.  Navegue a `MBProvider\Debugging\Sample.provide` y haga clic en **Agregar**.  
  
3.  Abra `Sample.consume`.  
  
4.  Haga clic en una forma de ejemplo y, en la ventana Propiedades, haga clic **\[...\]** en la propiedad de MBR.  En el cuadro de diálogo, haga clic **Examinar** y `Sample.provide`seleccione.  En la ventana de elementos, expanda la tarea de tipo y seleccione uno de los elementos.  
  
5.  Guarde el archivo.  
  
     \(No cierre la instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].\)  
  
 Ha creado un modelo que contiene una referencia de ModelBus a un elemento de otro modelo.  
  
#### Resuelve una referencia de ModelBus en una plantilla de texto  
  
1.  En la instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], abra un archivo de plantilla de texto de muestra.  establezca su contenido como sigue.  
  
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
  
     Tenga en cuenta los siguientes puntos:  
  
    1.  Los atributos de `hostSpecific` y de `inherits` de la directiva de `template` establecido.  
  
    2.  El modelo de consumidor se obtiene de la manera habitual a través del procesador de directivas que se generó en ese ADSL.  
  
    3.  Las directivas de ensamblado e importación deben poder tener acceso a ModelBus y los tipos de proveedor ADSL.  
  
    4.  Si sabe que mucho MBRs está vinculado al mismo modelo, es mejor llamar CreateAdapter sólo una vez.  
  
2.  Guarde la plantilla.  Compruebe que el archivo de texto resultante es similar a la siguiente.  
  
    ```  
  
    ExampleElement1   
    ExampleElement2   
         ExampleElement2 is linked to Task: Task2  
  
    ```  
  
#### Resuelve una referencia de ModelBus en un controlador de gestos  
  
1.  Cierre la instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], si se está ejecutando.  
  
2.  Agregue un archivo denominado MBConsumer \\Dsl\\Custom .cs y establezca su contenido al siguiente.  
  
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
  
3.  Presione CTRL\+F5.  
  
4.  En la instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], abra `Debugging\Sample.consume`.  
  
5.  Forma de doble clic uno.  
  
     Si ha establecido el MBR en ese elemento, el modelo se hace referencia se abre y el elemento de referencia está seleccionado.  
  
## Vea también  
 [Integrar modelos utilizando Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Code Generation and T4 Text Templates](../modeling/code-generation-and-t4-text-templates.md)