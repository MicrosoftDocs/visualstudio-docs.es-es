---
title: Generar archivos a partir de un modelo UML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, generating files
ms.assetid: 4e28b0e6-ce8f-45ee-9e3a-e4d600a0ad81
caps.latest.revision: 21
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5c126fab0226198fc182fe2c6c956594a11dc2ed
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831723"
---
# <a name="generate-files-from-a-uml-model"></a>Generar archivos a partir de un modelo UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A partir de un modelo UML, puede generar código de programa, esquemas, documentos, recursos y otros artefactos de cualquier tipo. Un método práctico para generar archivos de texto a partir de un modelo UML es usar [plantillas de texto](../modeling/code-generation-and-t4-text-templates.md). Estas le permiten incrustar el código de programa dentro del texto que desea generar.  
  
 Hay tres escenarios principales:  
  
- [Generar archivos a partir de un comando de menú](#Command) o de gestos. Con esta opción, define un comando [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que está disponible en los modelos UML.  
  
- [Generar archivos a partir de una aplicación](#Application). Con esta opción, puede escribir una aplicación que lee modelos UML y genera archivos.  
  
- [Generar en tiempo de diseño](#Design). Con esta opción, puede usar un modelo para definir algunas de las funciones de la aplicación y generar código, recursos, etc. en su solución [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
  En este tema finaliza con una explicación de [cómo usar la generación de texto](#What). Para obtener más información, consulte [generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md).  
  
##  <a name="Command"></a> Generar archivos a partir de un comando de menú  
 Puede usar plantillas de texto en un comando de menú UML de preprocesamiento. En el código de la plantilla de texto o en una clase parcial independiente, puede leer el modelo que se ve en el diagrama.  
  
 Consulte los siguientes temas para obtener más información acerca de estas características:  
  
- [Definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md)  
  
- [Generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md)  
  
- [Navegar por el modelo UML](../modeling/navigate-the-uml-model.md)  
  
  El enfoque que se muestra en el ejemplo siguiente es adecuado para generar texto desde un único modelo, al iniciar la operación desde uno de los diagramas de modelo. Para procesar un modelo en un contexto independiente, considere el uso de [Modelbus de Visual Studio](../modeling/integrate-uml-models-with-other-models-and-tools.md) para tener acceso al modelo y sus elementos.  
  
### <a name="example"></a>Ejemplo  
 Para ejecutar este ejemplo, cree un proyecto de extensión (VSIX) de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. El nombre del proyecto que se usa en este ejemplo es `VdmGenerator`. En el **source.extension.vsixmanifest** de archivos, haga clic en **agregar contenido** y establezca el campo de tipo en **componente MEF** y ruta de acceso de origen que hacen referencia a la del proyecto actual. Para obtener más información acerca de cómo configurar este tipo de proyecto, vea [definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
 Agregue al proyecto un archivo de C# que contenga este código. Esta clase define un comando de menú que aparecerá en un diagrama de clases UML.  
  
```  
using System;  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace VdmGenerator  
{  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  public class GenerateVdmFromClasses : ICommandExtension  
  {  
    [Import] public IDiagramContext DiagramContext { get; set; }  
    public void Execute(IMenuCommand command)  
    {  
      // Initialize the template with the Model Store.  
      VdmGen generator = new VdmGen(  
             DiagramContext.CurrentDiagram.ModelStore);  
      // Generate the text and write it.  
      System.IO.File.WriteAllText  
        (System.IO.Path.Combine(  
            Environment.GetFolderPath(  
                Environment.SpecialFolder.Desktop),  
            "Generated.txt")   
         , generator.TransformText());  
    }  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Enabled = command.Visible = true;  
    }  
    public string Text  
    { get { return "Generate VDM"; } }  
  }  
}  
```  
  
 El siguiente archivo es la plantilla de texto. Dicho archivo genera una línea de texto para cada clase UML del modelo y una línea para cada atributo de cada clase. En el texto (delimitado por `<# ... #>`) hay código incrustado para leer el modelo.  
  
 Para crear este archivo, haga clic en el proyecto en el Explorador de soluciones, seleccione **agregar**y, a continuación, haga clic en **nuevo elemento**. Seleccione **plantilla de texto preprocesada**. Debe ser el nombre de archivo para este ejemplo **VdmGen.tt**. El **Custom Tool** debe ser propiedad del archivo **TextTemplatingFilePreprocessor**. Para obtener más información acerca de las plantillas de texto preprocesadas, vea [generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
```  
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>  
<#   
   foreach (IClass classElement in store.AllInstances<IClass>())   {  
#>  
Type <#= classElement.Name #> ::  
<#  
     foreach (IProperty attribute in classElement.OwnedAttributes)     {  
#>  
       <#= attribute.Name #> : <#=   
           attribute.Type == null ? ""  
                                  : attribute.Type.Name #>   
<#  
     }   }  
#>  
```  
  
 La plantilla de texto genera una clase parcial en C#, que se convierte en parte de su proyecto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. En un archivo independiente, agregue otra declaración parcial de la misma clase. Este código proporciona la plantilla con acceso al almacén de modelos UML:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
namespace VdmGenerator  
{  
    public partial class VdmGen  
    {  
        private IModelStore store;  
        public VdmGen(IModelStore s)  
        { store = s; }  
    }  
}  
```  
  
 Para probar el proyecto, presione **F5**. Se iniciará una nueva instancia de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. En esta instancia, abra o cree un modelo UML que contenga un diagrama de clases. Agregue algunas clases al diagrama y algunos atributos a cada clase. Haga clic en el diagrama y, a continuación, haga clic en el comando de ejemplo `Generate VDM`. El comando crea el archivo `C:\Generated.txt`. Inspeccione este archivo. Su contenido debe parecerse al siguiente texto, pero mostrará sus propias clases y atributos:  
  
```  
Type Class1 ::  
          Attribute1 : int   
          Attribute2 : string   
Type Class2 ::   
          Attribute3 : string   
```  
  
##  <a name="Application"></a> Generar archivos a partir de una aplicación  
 Puede generar archivos desde una aplicación que lee un modelo UML. Para ello, es un método más flexible y eficaz de obtener acceso a los modelos y sus elementos [Modelbus de Visual Studio](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
 También puede usar la API básica para cargar el modelo y pasarlo a plantillas de texto usando las mismas técnicas que en la sección anterior. Para obtener más información acerca de cómo cargar un modelo, vea [leer un modelo UML en código de programa](../modeling/read-a-uml-model-in-program-code.md).  
  
##  <a name="Design"></a> Generar archivos en tiempo de diseño  
 Si el proyecto tiene un método estándar para interpretar UML como código, puede crear plantillas de texto que le permiten generar código dentro del proyecto a partir de un modelo UML. Normalmente tendría una solución que contiene el proyecto de modelo UML y uno o más proyectos para el código de aplicación. Cada proyecto de código podría contener varias plantillas que generan código de programa, recursos y archivos de configuración, según el contenido del modelo. El desarrollador puede ejecutar todas las plantillas, haga clic en el **Transformar todas las plantillas** en la barra de herramientas del explorador de soluciones. El código de programa se genera normalmente en forma de clases parciales para facilitar la integración de las partes escritas de forma manual.  
  
 Un proyecto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] de este tipo se puede distribuir en forma de plantilla para que todos los miembros de un equipo puedan crear proyectos que generen código a partir de un modelo de la misma manera. Normalmente, la plantilla forma parte de un paquete de extensión que incluye restricciones de validación en el modelo para garantizar que se cumplen las condiciones previas del código de generación.  
  
### <a name="outline-procedure-for-generating-files"></a>Procedimiento básico para generar archivos  
  
-   Para agregar una plantilla a un proyecto, seleccione **plantilla de texto** en el cuadro de diálogo Agregar nuevo archivo. Puede agregar una plantilla a la mayoría de los tipos de proyecto, pero no a los proyectos de modelado.  
  
-   La propiedad Custom Tools del archivo de plantilla debe ser **TextTemplatingFileGenerator**, y la extensión de nombre de archivo debe ser TT.  
  
-   La plantilla debe tener al menos una directiva de salida:  
  
     `<#@ output extension=".cs" #>`  
  
     Establezca el campo de extensión según el lenguaje del proyecto.  
  
-   Para permitir que el código de generación de la plantilla tenga acceso al modelo, escriba directivas de `<#@ assembly #>` para los ensamblados que son necesarios para leer un modelo UML. Use `ModelingProject.LoadReadOnly()` para abrir el modelo. Para obtener más información, consulte [leer un modelo UML en código de programa](../modeling/read-a-uml-model-in-program-code.md).  
  
-   La plantilla se ejecuta al guardarla y al hacer clic en **Transformar todas las plantillas** en la barra de herramientas del explorador de soluciones.  
  
-   Para obtener más información acerca de este tipo de plantilla, consulte [generación de código de tiempo de diseño mediante el uso de plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
-   En un proyecto típico, tendrá varias plantillas que generan diferentes archivos a partir del mismo modelo. La primera parte de cada plantilla será la misma. Para reducir esta duplicación, traslade las partes comunes a un archivo de texto independiente y, después, invóquelo usando la directiva `<#@include file="common.txt"#>` en cada plantilla.  
  
-   También puede definir un procesador de directivas especializado que permita proporcionar parámetros al proceso de generación de texto. Para obtener más información, consulte [personalizar la transformación de texto T4](../modeling/customizing-t4-text-transformation.md).  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo genera una clase en C# para cada clase UML del modelo de origen.  
  
##### <a name="to-set-up-a-visual-studio-solution-for-this-example"></a>Para configurar una solución de Visual Studio para este ejemplo  
  
1. Cree un diagrama de clases UML en un proyecto de modelado en una nueva solución.  
  
   1.  En el **arquitectura** menú, haga clic en **nuevo diagrama**.  
  
   2.  Seleccione **diagrama de clases UML**.  
  
   3.  Siga las indicaciones para crear una nueva solución y proyecto de modelado.  
  
   4.  Agregue algunas clases al diagrama arrastrando la herramienta de clases UML desde el cuadro de herramientas.  
  
   5.  Guarde el archivo.  
  
2. Cree un proyecto en C# o Visual Basic en la misma solución.  
  
   -   En el Explorador de soluciones, haga clic en la solución, seleccione **agregar**y, a continuación, haga clic en **nuevo proyecto**. En **plantillas instaladas**, haga clic en **Visual Basic** o **Visual C#,** y, a continuación, seleccione un tipo de proyecto como **aplicación de consola**.  
  
3. Agregue un archivo de texto sin formato al proyecto de Visual Basic o C#. Este archivo contendrá código que se comparte si desea escribir varias plantillas de texto.  
  
   - En el Explorador de soluciones, haga clic en el proyecto, seleccione **agregar**y, a continuación, haga clic en **nuevo elemento**. Seleccione **archivo de texto**.  
  
     Inserte el texto que se muestra en esta sección.  
  
4. Agregue un archivo de plantilla de texto al proyecto de Visual Basic o C#.  
  
   - En el Explorador de soluciones, haga clic en el proyecto, seleccione **agregar**y, a continuación, haga clic en **nuevo elemento**. Seleccione **plantilla de texto**.  
  
     Inserte el código siguiente en el archivo de plantilla de texto.  
  
5. Guarde el archivo de plantilla de texto.  
  
6. Inspeccione el código en el archivo subsidiario. Debe contener una clase para cada clase UML del modelo.  
  
   1.  En un proyecto de Visual Basic, haga clic en **mostrar todos los archivos** en la barra de herramientas del explorador de soluciones.  
  
   2.  Expanda el nodo del archivo de plantilla en el Explorador de soluciones.  
  
#### <a name="content-of-the-shared-text-file"></a>Contenido del archivo de texto compartido  
 En este ejemplo, el archivo se denomina SharedTemplateCode.txt y se encuentra en la misma carpeta que las plantillas de texto.  
  
```  
<# /* Common material for inclusion in my model templates */ #>  
<# /* hostspecific allows access to the Visual Studio API */ #>  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ assembly name="Microsoft.VisualStudio.Uml.Interfaces.dll"#>  
<#@ assembly name="Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll"#>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>  
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility" #>  
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>  
<#+  // Note this is a Class Feature Block  
///<summary>  
/// Text templates are run in a common AppDomain, so   
/// we can cache the model store that we find.  
///</summary>  
private IModelStore StoreCache  
{  
  get { return AppDomain.CurrentDomain.GetData("ModelStore") as IModelStore; }  
  set { AppDomain.CurrentDomain.SetData("ModelStore", value); }   
}  
private bool CacheIsOld()  
{  
    DateTime? dt = AppDomain.CurrentDomain  
           .GetData("latestAccessTime") as DateTime?;  
    DateTime t = dt.HasValue ? dt.Value : new DateTime();   
    DateTime now = DateTime.Now;  
    AppDomain.CurrentDomain.SetData("latestAccessTime", now);  
    return now.Subtract(t).Seconds > 3;  
}  
  
///<summary>  
/// Find the UML modeling project in this solution,  
/// and load the model.  
///</summary>  
private IModelStore ModelStore  
{  
  get   
  {  
    // Avoid loading the model for every template:  
    if (StoreCache == null || CacheIsOld())  
    {  
      // Use Visual Studio API to find modeling project:  
      EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
      EnvDTE.Project project = null;  
      foreach (EnvDTE.Project p in dte.Solution.Projects)  
      {  
        if (p.FullName.EndsWith(".modelproj"))  
        {  
          project = p;  
          break;  
        }              
      }  
      if (project == null) return null;  
  
      // Load UML model into this AppDomain  
      // and access model store:  
      IModelingProjectReader reader =   
           ModelingProject.LoadReadOnly(project.FullName);  
      StoreCache = reader.Store;  
    }  
    return StoreCache;  
  }  
}  
#>  
```  
  
#### <a name="content-of-the-text-template-file"></a>Contenido del archivo de plantilla de texto  
 El siguiente texto se coloca en el **.tt** archivo. Este ejemplo genera clases en un archivo en C# a partir de las clases UML del modelo. Sin embargo, puede generar archivos de cualquier tipo. El lenguaje del archivo generado no está relacionado con el lenguaje en el que está escrito el código de plantilla de texto.  
  
```  
<#@include file="SharedTemplateCode.txt"#>  
<#@ output extension=".cs" #>  
namespace Test{  
<#  
      foreach (IClass c in ModelStore.AllInstances<IClass>())  
      {  
#>  
   public partial class <#=c.Name#>  
   {   }  
<#  
      }  
#>  
}  
```  
  
##  <a name="What"></a> Cómo usar la generación de texto  
 La verdadera eficacia de modelado se obtiene al usar modelos para diseñar en el nivel de requisitos o la arquitectura. Puede usar plantillas de texto para realizar parte del trabajo de convertir ideas de alto nivel en código. En muchos casos, esto no provocar una correspondencia uno a uno entre los elementos de los modelos UML y las clases u otras partes del código de programa.  
  
 Además, la transformación depende del dominio del problema; no existe ninguna asignación universal entre los modelos y el código.  
  
 A continuación le presentamos algunos ejemplos sobre generación de código a partir de modelos:  
  
-   **Líneas de productos**. Fabrikam, Inc. se compila y se instala sistemas de control de equipaje en aeropuertos. Gran parte del software es muy similar entre una instalación y la siguiente, pero la configuración del software depende de la maquinaria de control de equipaje que esté instalada y cómo estén interconectadas estas partes mediante cintas transportadoras. Al principio de un contrato, los analistas de Fabrikam estudian los requisitos con la administración del aeropuerto y elaboran el plan de hardware usando un diagrama de actividades UML. A partir de este modelo, el equipo de desarrollo genera los archivos de configuración, el código de programa, los planes y los documentos de usuario. Luego completan el trabajo agregando elementos y ajustando el código manualmente. A medida que ganan experiencia con los proyectos, extienden el ámbito del material generado.  
  
-   **Patrones**. Los desarrolladores de Contoso, Ltd. suelen crear sitios web y diseñar el esquema de navegación mediante diagramas de clases UML. Cada página web se representa mediante una clase y las asociaciones representan vínculos de navegación. Los desarrolladores generan gran parte del código de un sitio web a partir del modelo. Cada página web se corresponde con varias clases y entradas del archivo de recursos.  Este método tiene la ventaja que la construcción de cada página se ajusta a un patrón único, lo que hace que sea más confiable y flexible que el código escrito a mano. El patrón está en las plantillas de generación, mientras que el modelo se usa para capturar aspectos variables.  
  
-   **Esquemas**. Humongous Insurance tiene miles de sistemas en todo el mundo. Estos sistemas usan distintas interfaces, idiomas y bases de datos. El equipo de arquitectura central publica internamente modelos de conceptos y procesos de negocio. A partir de estos modelos, los equipos locales generan partes de sus esquemas de intercambio y base de datos, declaraciones en código de programa y demás. La presentación gráfica de los modelos ayuda a los equipos a estudiar las propuestas. Los equipos crean varios diagramas que muestran los subconjuntos del modelo que se aplican a cada departamento de la empresa. También se usa el color para resaltar áreas sujetas a cambios.  
  
## <a name="important-techniques-for-generating-artifacts"></a>Técnicas importantes para generar artefactos  
 En los ejemplos anteriores, los modelos se usan para diversos fines empresariales y la interpretación de los elementos de modelado, como clases y actividades, varía de una aplicación a otra. Las siguientes técnicas son útiles para generar artefactos a partir de modelos.  
  
-   **Perfiles**. Incluso dentro de un área empresarial, la interpretación de un tipo de elemento puede variar. Por ejemplo, en un diagrama de sitio web, algunas clases podrían representar páginas web y otras representar bloques de contenido. Para facilitar que los usuarios identifiquen estas distinciones, defina estereotipos. Los estereotipos también permiten adjuntar propiedades adicionales que se aplican a los elementos de ese tipo. Los estereotipos se empaquetan dentro de perfiles. Para obtener más información, consulte [definir un perfil para ampliar UML](../modeling/define-a-profile-to-extend-uml.md).  
  
     En el código de plantilla es fácil tener acceso a los estereotipos que se definen en un objeto. Por ejemplo:  
  
    ```  
    public bool HasStereotype(IClass c, string profile, string stereo)  
    { return c.AppliedStereotypes.Any  
       (s => s.Profile == profile && s.Name == stereo ); }  
    ```  
  
-   **Modelos restringidos**. No todos los modelos que se pueden crear son válidos para todos los propósitos. Por ejemplo, en los modelos de equipaje del aeropuerto de Fabrikam, sería incorrecto tener un mostrador de facturación sin una cinta transportadora de salida. Puede definir funciones de validación que ayudan a los usuarios a cumplir estas restricciones. Para obtener más información, consulte [definir restricciones de validación para modelos UML](../modeling/define-validation-constraints-for-uml-models.md).  
  
-   **Conservar los cambios manuales**. Sólo algunos de los archivos de solución se pueden generar a partir de un modelo. En la mayoría de los casos, necesitará poder agregar o ajustar a mano el contenido generado. Sin embargo, es importante que estos cambios manuales se conserven cuando la transformación de plantilla se ejecute de nuevo.  
  
     Si sus plantillas generan código en [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] idiomas, deberán generar clases parciales para que los desarrolladores pueden agregar métodos y código. También es útil generar cada clase como un par: una clase base abstracta que contiene los métodos y una clase heredera que solo contiene el constructor. Esto permite a los desarrolladores reemplazar los métodos. Para permitir que se reemplace la inicialización, se realiza en un método independiente en lugar de en los constructores.  
  
     Si una plantilla genera XML y otros tipos de salida, puede ser más difícil separar el contenido manual del contenido generado. Un posible método pasa por crear una tarea en el proceso de compilación que combina dos archivos. Otro método consiste en que los desarrolladores ajusten una copia local de la plantilla de generación.  
  
-   **Mover código a ensamblados independientes**. No se recomienda escribir grandes cantidades de código en las plantillas. Es preferible mantener separado el contenido generado del cálculo y las plantillas de texto no son adecuadas para editar código.  
  
     En su lugar, si tiene que realizar numerosos cálculos para generar texto, compile esas funciones en un ensamblado independiente y llame a sus métodos desde la plantilla.



