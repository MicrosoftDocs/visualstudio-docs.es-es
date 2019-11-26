---
title: Ejecutar pruebas unitarias en extensiones UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 745d74ae-e48c-4fd9-a755-4354b81b9f8a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f634f028dafea3260a69537893513f13cc0ebe83
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292535"
---
# <a name="run-unit-tests-on-uml-extensions"></a>Ejecutar pruebas unitarias en extensiones UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para ayudar a mantener estable el código durante los cambios sucesivos, recomendamos escribir pruebas unitarias y realizarlas como parte de un proceso de compilación normal. Para obtener más información, vea [Haga una prueba unitaria de su código](../test/unit-test-your-code.md). Para configurar las pruebas para las extensiones de modelado de Visual Studio, necesita algunos fragmentos de información clave. En breve:

- [Configurar una prueba unitaria para las extensiones VSIX](#Host)

   Ejecute las pruebas con el adaptador host del IDE de VS. Anteponga `[HostType("VS IDE")]`a cada método de prueba. Este adaptador host inicia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] cuando las pruebas se ejecutan.

- [Acceso a DTE y ModelStore](#DTE)

   Normalmente, deberá abrir un modelo y sus diagramas y acceder a `IModelStore` en la inicialización de pruebas.

- [Abrir un diagrama del modelo](#Opening)

   Puede convertir `EnvDTE.ProjectItem` en `IDiagramContext`y viceversa.

- [Realizar cambios en el subproceso de la interfaz de usuario](#UiThread)

   Las pruebas que realizan cambios en el almacén del modelo se deben realizar en el subproceso de la interfaz de usuario. Para ello, puede usar `Microsoft.VSSDK.Tools.VsIdeTesting.UIThreadInvoker` .

- [Comandos de prueba, gestos y otros componentes de MEF](#MEF)

   Para probar los componentes MEF, debe conectar explícitamente sus propiedades importadas a valores.

  Estos aspectos se desarrollan en mayor profundidad en las siguientes secciones.

## <a name="requirements"></a>Requisitos
 Vea [Requisitos](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="Host"></a>Configurar una prueba unitaria para las extensiones VSIX
 Los métodos de las extensiones de modelado suelen funcionar con un diagrama que ya está abierto. Los métodos usan importaciones MEF como **IDiagramContext** y **ILinkedUndoContext**. Su entorno de prueba debe tener este contexto configurado antes de ejecutar las pruebas.

#### <a name="to-set-up-a-unit-test-that-executes-in-includevsprvsincludesvsprvs-mdmd"></a>Para configurar una prueba unitaria que se ejecuta en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

1. Cree el proyecto de extensión UML y el proyecto de prueba unitaria.

    1. **Un proyecto de extensión UML.** Se suele crear mediante el comando, el gesto o las plantillas de proyecto de validación. Por ejemplo, vea [definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

    2. **Un proyecto de prueba unitaria.** Para obtener más información, vea [Haga una prueba unitaria de su código](../test/unit-test-your-code.md).

2. Cree una solución de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que contenga un proyecto de modelado UML. Usará esta solución como el estado inicial de las pruebas. Debe ser independiente de la solución en la que escribe la extensión UML y las pruebas unitarias. Para obtener más información, vea [crear proyectos y diagramas de modelado UML](../modeling/create-uml-modeling-projects-and-diagrams.md).

3. **En el proyecto de extensión UML**, edite el archivo .csproj como texto y asegúrese de que las siguientes líneas muestran `true`:

    ```
    <CopyBuildOutputToOutputDirectory>true</CopyBuildOutputToOutputDirectory>
        <CopyOutputSymbolsToOutputDirectory>true</CopyOutputSymbolsToOutputDirectory>
    ```

     Para editar el archivo .csproj como texto, elija **Descargar el proyecto** en el menú contextual del proyecto, en el Explorador de soluciones. Luego, elija **Editar ….csproj**. Tras haber editado el texto, elija **Volver a cargar el proyecto**.

4. En el proyecto de extensión UML, agregue la siguiente línea a **Properties\AssemblyInfo.cs**. Esto permite que las pruebas unitarias tengan acceso a los métodos que quiere comprobar:

    ```csharp
    [assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
    ```

5. **En el proyecto de prueba unitaria**, agregue las siguientes referencias de ensamblado:

    - *El proyecto de extensión UML*

    - **EnvDTE. dll**

    - **Microsoft. VisualStudio. ArchitectureTools. Extensibility. dll**

    - **Microsoft. VisualStudio. ComponentModelHost. dll**

    - **Microsoft. VisualStudio. QualityTools. UnitTestFramework. dll**

    - **Microsoft. VisualStudio. UML. interfaces. dll**

    - **Microsoft. VSSDK. TestHostFramework. dll**

6. Anteponga el atributo `[HostType("VS IDE")]` a cada método de prueba, incluidos los métodos de inicialización.

     Esto garantizará que la prueba se ejecute en una instancia experimental de Visual Studio.

## <a name="DTE"></a>Acceso a DTE y ModelStore
 Escriba un método para abrir un proyecto de modelado en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Normalmente, es conveniente abrir una solución solo una vez en cada ejecución de pruebas. Para ejecutar el método solo una vez, anteponga el atributo `[AssemblyInitialize]` en el método. No olvide que también necesita el atributo [HostType("VS IDE")] en cada método de prueba.  Por ejemplo:

```csharp
using EnvDTE;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Microsoft.VSSDK.Tools.VsIdeTesting;

namespace UnitTests
{
  [TestClass]
  public static class TestSetup
  {

    // Location of a VS Solution that defines an initial state for your tests:
    private const string testSolutionFilePath = @"C:\MyTestFolder\TestModelSln\TestModel.sln";
    // Name of a modeling project within the test solution:
    private const string testModelingProjectName = "MyTestModel";

    // Make Solution and IModelStore available to test methods:
    public static Solution ModelSolution = null;
    public static IModelingProject ModelingProject = null;
    public static IModelStore ModelStore = null;

    // This method will be performed once to initialize tests for this assembly:
    [AssemblyInitialize]
    [HostType("VS IDE")]
    public static void OpenTestModelingProject(TestContext testContext)
    {
      // To make sure that we always start the tests in the same state,
      // copy the test solution from a read-only directory:
      // TODO: copy test solution folder.

      // Open a solution that is the initial state for your tests:
      ModelSolution = VsIdeTestHostContext.Dte.Solution;
      ModelSolution.Open(testSolutionFilePath);

      // Find the ModelingProject and IModelStore:
      foreach (Project project in ModelSolution.Projects)
      {
        // https://msdn.microsoft.com/library/ee791691.aspx
        ModelingProject = project as IModelingProject;
        if (ModelingProject != null)
        {
          // This is a modeling project.
          ModelStore = ModelingProject.Store;
          break;
        }
        // else this is another kind of project.
      }

      Assert.IsNotNull(ModelSolution, "VS solution not found");
      Assert.IsNotNull(ModelStore, "Modeling store not found");
    }
    [AssemblyCleanup]
    public static void RemoveTestSolution ()
    {
      // TODO: Remove copied test solution directory.
    }
  }
}

```

 Si una instancia de <xref:EnvDTE.Project?displayProperty=fullName> representa un proyecto de modelado, puede convertirla a y desde [IModelingProject](/previous-versions/ee789474(v=vs.140)).

## <a name="Opening"></a>Abrir un diagrama del modelo
 En cada prueba o clase de pruebas probablemente le interese trabajar con un diagrama abierto. En el siguiente ejemplo se usa el atributo `[ClassInitialize]` , que ejecuta este método antes que otros métodos de esta clase de prueba. Una vez más, no olvide que también necesita el atributo [HostType("VS IDE")] en cada método de prueba:

```csharp
//
private IDiagram diagram;
// This class contains unit tests:
[TestClass]
public class MyTestClass
{
  // Map filenames to open diagram files:
  private static Dictionary<string, IDiagram> diagrams = new Dictionary<string, IDiagram>();

  // This method will be called once for this test class:
  [ClassInitialize]
  [HostType("VS IDE")]
  public static void TestClassInitialize(TestContext testContext)
  {
    // Open all the diagrams in the model:
    foreach (ProjectItem item in (TestSetup.ModelingProject as Project).ProjectItems)
    {
      // Get the filename of the principal file (not the .layout subsidiary):
      string fileName = item.FileNames[0];
      // If this is a model diagram file, it can be cast to IDiagramContext:
      IDiagramContext modelingItem = item as IDiagramContext;
      if (modelingItem != null)
      {
        IDiagram diagram = modelingItem.CurrentDiagram;
        if (diagram == null)
        {
          // Diagram is closed. Open it:
          item.Open().Activate();
          diagram = modelingItem.CurrentDiagram;
        }
        diagrams[fileName] = diagram;
      }
      // else item is not a model diagram.
    }
    Assert.IsTrue(diagrams.Count>0, "UML diagram not found");
  }
// Insert test methods here ...
}

```

## <a name="UiThread"></a>Realizar cambios en el modelo en el subproceso de la interfaz de usuario
 Si las pruebas o los métodos en pruebas realizan cambios en el almacén de modelos, deberá ejecutarlos en el subproceso de la interfaz de usuario. Si no hace esto, puede que surja una `AccessViolationException`. Inserte el código del método de prueba en una llamada a Invoke:

```
using System.Windows.Forms;
using Microsoft.VSSDK.Tools.VsIdeTesting;
 ...
    [TestMethod]
    [HostType("VS IDE")]
    public void MyTest1()
    {
      // Store operations must run in the UI thread:
      UIThreadInvoker.Invoke((System.Action)delegate()
      {
        SetupTestState(TestSetup.ModelStore, diagram);
        ExecuteMethodUnderTest(TestSetup.ModelStore, diagram);
      });
    }
```

## <a name="MEF"></a>Comando de prueba, gestos y otros componentes de MEF
 Los componentes MEF usan las declaraciones de propiedad que tienen el atributo `[Import]` y cuyos valores son establecidos por sus hosts. Estas propiedades suelen englobar IDiagramContext, SVsServiceProvider y ILinkedUndoContext. Cuando se prueba un método que usa alguna de estas propiedades, hay que establecer sus valores antes de ejecutar el método en cuestión. Por ejemplo, si ha escrito una extensión de comando parecida a este código:

```

  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  class MyCommand : ICommandExtension
  {
    [Import] IDiagramContext context { get; set; }
    [Import]
Microsoft.VisualStudio.Shell.SVsServiceProvider
serviceProvider {get;set;}
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }
    public void Execute(IMenuCommand command)
    {
      DoCommand();
    }
    private void DoCommand()
    {
      IDiagram diagram = context.CurrentDiagram;
      using (ILinkedUndoTransaction t = linkedUndoContext.BeginTransaction("go"))
      { ... }}}

```

 Podrá establecer las propiedades importadas de la siguiente forma:

```

using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ComponentModelHost;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Microsoft.VSSDK.Tools.VsIdeTesting;
...
    [TestMethod]
    [HostType("VS IDE")]
    public void Test1()
    {
      // Create an instance of the class under test:
      MyCommand myCommand = new MyCommand();
      // Get the components service:
      IComponentModel components = VsIdeTestHostContext.ServiceProvider
        .GetService(typeof(SComponentModel)) as IComponentModel;
      // Set the imported properties of the instance under test:
      // Extension requires "using System.ComponentModel.Composition;" :
      components.DefaultCompositionService.SatisfyImportsOnce(myCommand);
      // Call method(s) under test:
      UIThreadInvoker.Invoke((System.Action)delegate()
      {
        myCommand.DoCommand();
      });
...}
```

 Si desea probar un método que toma una propiedad importada como parámetro, puede importar la propiedad a la clase de prueba y aplicar `SatisfyImportsOnce` a la instancia de prueba. Por ejemplo:

```

using System.ComponentModel.Composition;
...
  [TestClass]
  public class MyTestClass
  {
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }

    // Called before each test method:
    [TestInitialize, HostType("VS IDE")]
    public void TestInitializer()
    {
      IComponentModel components = VsIdeTestHostContext.ServiceProvider
            .GetService(typeof(SComponentModel)) as IComponentModel;
      // Extension requires "using System.ComponentModel.Composition;" :
      components.DefaultCompositionService.SatisfyImportsOnce(this);
    }
    [TestMethod, HostType("VS IDE")]
    public void Test2()
    {
     UIThreadInvoker.Invoke((System.Action)delegate()
      {
      // Pass context items to class under test:
      Class1 item1 = new Class1(this.linkedUndoContext);
      item1.Method1(); // Can use linkedUndoContext
     });
   }
}

```

 En este ejemplo, los dos atributos en cada método de prueba se combinan en una sola línea para su comodidad.

## <a name="access-from-tests-to-private-methods-and-variables"></a>Acceso desde las pruebas a métodos y variables privados
 Hay veces en las que querrá probar un método que es privado, o confirmar el estado de un campo privado, antes y después de ejecutar un método en pruebas. Esto supone una dificultad, porque las pruebas están en un ensamblado independiente de las clases en pruebas. Hay varias tácticas que se pueden considerar, como las siguientes:

 Probar solo mediante elementos públicos e internos escriba las pruebas de modo que usen solo clases y miembros públicos (o internos). Este es el mejor método. Las pruebas seguirán funcionando aunque se refactorice la implementación interna del ensamblado en pruebas. Si aplica las mismas pruebas antes y después de confirmar los cambios, puede estar seguro de que los cambios no han modificado el comportamiento del ensamblado.

 Para que esto sea posible, puede que tenga que reestructurar el código. Por ejemplo, puede que necesite separar algunos métodos en otra clase.

 Si tiene en cuenta realmente este método, verá con frecuencia que el código es más fácil de leer y cambiar, así como menos propenso a errores cuando es necesario efectuar cambios.

 Puede permitir que el ensamblado de prueba acceda a los elementos internos si agrega un atributo en **Properties\AssemblyInfo.cs** en el proyecto que se va a probar:

```csharp
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
```

 Defina una interfaz de prueba defina una interfaz que incluya los miembros públicos de una clase que se va a probar y otras propiedades y métodos para los miembros privados que desea que las pruebas puedan usar. Agregue esta interfaz al proyecto que se va a probar. Por ejemplo:

```csharp
internal interface MyClassTestInterface {
  void PublicMethod1();
  string PublicProperty1 { get; }
  string privateField1_Accessor { get; }
  int privateMethod1_Accessor (string p1);
 }
```

 Agregue los métodos a la clase que se va a probar para implementar los métodos de descriptor de acceso explícitamente. Escriba estos métodos extra en una definición de clase parcial en un archivo independiente para mantenerlos aparte de la clase principal. Por ejemplo:

```csharp
partial public class MyClass
{
  string MyClassTestInterface.privateField1_Accessor
  { get { return privateField1; } }
  int MyClassTestInterface.privateMethod1_Accessor (string p1)
  { return privateMethod1(p1); }
}

```

 Agregue este atributo al ensamblado que va a probar para permitir que el ensamblado de prueba use las interfaces de prueba:

```csharp
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
```

 En los métodos de prueba unitaria, use la interfaz de prueba. Por ejemplo:

```csharp
MyClassTestInterface testInstance = new MyClass();
testInstance.PublicMethod1();
Assert.AreEqual("hello", testInstance.privateField1_Accessor);
```

 Definir los descriptores de acceso mediante la reflexión esta es la manera en que se recomienda menos. Las versiones anteriores de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proporcionaban una utilidad que creaba automáticamente un método de descriptor de acceso para cada método privado. Aunque esto resulta cómodo, la experiencia nos dice que tiende a producir pruebas unitarias que se acoplan estrechamente a la estructura interna de la aplicación que están probando. Esto supone un trabajo extra cuando los requisitos o la arquitectura cambian, porque las pruebas tienen que modificarse junto con la implementación. Además, cualquier suposición errónea en el diseño de implementación también se integra en las pruebas, de modo que las pruebas no encuentran errores.

## <a name="see-also"></a>Vea también
 [Anatomía de una prueba unitaria](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144) [definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
