---
title: Creación de un sistema básico de proyectos, Parte 1 Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ff969a905d48ef16b3cb036fa897bf0307b929d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739723"
---
# <a name="create-a-basic-project-system-part-1"></a>Crear un sistema básico de proyectos, parte 1
En Visual Studio, los proyectos son los contenedores que los desarrolladores usan para organizar archivos de código fuente y otros activos. Los proyectos aparecen como elementos secundarios de soluciones en el Explorador de **soluciones.** Los proyectos le permiten organizar, compilar, depurar e implementar código fuente y crear referencias a servicios web, bases de datos y otros recursos.

 Los proyectos se definen en archivos de proyecto, por ejemplo, un archivo *.csproj* para un proyecto de Visual C. Puede crear su propio tipo de proyecto que tenga su propia extensión de nombre de archivo de proyecto. Para obtener más información acerca de los tipos de proyecto, vea [Tipos de proyecto](../extensibility/internals/project-types.md).

> [!NOTE]
> Si necesita ampliar Visual Studio con un tipo de proyecto personalizado, se recomienda aprovechar el sistema de proyectos de [Visual Studio](https://github.com/Microsoft/VSProjectSystem) (VSPS) que tiene una serie de ventajas sobre la creación de un sistema de proyecto desde cero:
>
> - Incorporación más fácil.  Incluso un sistema de proyecto básico requiere decenas de miles de líneas de código.  Aprovechar VSPS reduce el costo de incorporación a unos pocos clics antes de estar listo para personalizarlo según sus necesidades.
> - Mantenimiento más fácil.  Al aprovechar VSPS, solo necesita mantener sus propios escenarios.  Nos encargamos del mantenimiento de toda la infraestructura del sistema del proyecto.
>
>   Si necesita tener como destino versiones de Visual Studio anteriores a Visual Studio 2013, no podrá aprovechar VSPS en una extensión de Visual Studio.  Si ese es el caso, este tutorial es un buen lugar para empezar.

 En este tutorial se muestra cómo crear un tipo de proyecto que tiene la extensión de nombre de archivo de proyecto *.myproj*. En este tutorial se toma prestado del sistema de proyectos de Visual C. existente.

> [!NOTE]
> Para obtener más ejemplos de proyectos de extensión, vea [ejemplos de VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

 Este tutorial enseña cómo realizar estas tareas:

- Cree un tipo de proyecto básico.

- Cree una plantilla de proyecto básica.

- Registre la plantilla de proyecto con Visual Studio.

- Cree una instancia de proyecto abriendo el cuadro de diálogo **Nuevo proyecto** y, a continuación, utilizando la plantilla.

- Cree un generador de proyectos para el sistema de proyectos.

- Cree un nodo de proyecto para el sistema de proyectos.

- Agregue iconos personalizados para el sistema de proyectos.

- Implemente la sustitución básica de parámetros de plantilla.

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

 También debe descargar el código fuente para [Managed Package Framework para proyectos.](https://github.com/tunnelvisionlabs/MPFProj10) Extraiga el archivo en una ubicación accesible para la solución que va a crear.

## <a name="create-a-basic-project-type"></a>Crear un tipo de proyecto básico
 Cree un proyecto de VSIX de C- denominado **SimpleProject**. (**Archivo** > **nuevo** > **proyecto** y, a continuación, proyecto**VSIX**de**extensibilidad** > de Visual **C.** > ). Agregue una plantilla de elemento de proyecto paquete de Visual Studio (en el Explorador de **soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar** > **nuevo elemento**y, a continuación, vaya a Paquete de Visual**Studio** **de extensibilidad** > ). Asigne al archivo el nombre *SimpleProjectPackage*.

## <a name="creating-a-basic-project-template"></a>Creación de una plantilla de proyecto básica
 Ahora, puede modificar este VSPackage básico para implementar el nuevo tipo de proyecto *.myproj.* Para crear un proyecto basado en el tipo de proyecto *.myproj,* Visual Studio tiene que saber qué archivos, recursos y referencias agregar al nuevo proyecto. Para proporcionar esta información, coloque los archivos de proyecto en una carpeta de plantilla de proyecto. Cuando un usuario utiliza el proyecto *.myproj* para crear un proyecto, los archivos se copian en el nuevo proyecto.

### <a name="to-create-a-basic-project-template"></a>Para crear una plantilla de proyecto básica

1. Agregue tres carpetas al proyecto, una debajo de la otra: *Plantillas, Proyectos, SimpleProject*. (En **el Explorador**de soluciones , haga clic con el botón secundario en el nodo del proyecto **SimpleProject,** seleccione **Agregar**y, a continuación, haga clic en Nueva **carpeta**. Asigne a la carpeta el nombre *Plantillas*. En la carpeta *Plantillas,* agregue una carpeta denominada *Proyectos*. En la carpeta *Proyectos,* agregue una carpeta denominada *SimpleProject*.)

2. En la carpeta *Templates-Projects-SimpleProject* , agregue un archivo de imagen de mapa de bits para usarlo como icono denominado *SimpleProject.ico*. Al hacer clic en **Agregar**, se abre el editor de iconos.

3. Haga que el icono sea distintivo. Este icono aparecerá en el cuadro de diálogo **Nuevo proyecto** más adelante en el tutorial.

    ![Icono de proyecto simple](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. Guarde el icono y cierre el editor de iconos.

5. En la carpeta *Plantillas, Proyectos, SimpleProject,* agregue un elemento **Clase** denominado *Program.cs*.

6. Reemplace el código existente por las siguientes líneas.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Text;

   namespace $nameSpace$
   {
       public class $className$
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

   > [!IMPORTANT]
   > Esta no es la forma final del código *Program.cs;* los parámetros de sustitución se tratarán en un paso posterior. Es posible que vea errores de compilación, pero siempre que **BuildAction** del archivo sea **Content**, debería poder compilar y ejecutar el proyecto como de costumbre.

7. Guarde el archivo.

8. Copie el archivo *de AssemblyInfo.cs* de la carpeta *Propiedades* a la carpeta *Proyectos-SimpleProject.*

9. En la carpeta *Projects-SimpleProject,* agregue un archivo XML denominado *SimpleProject.myproj*.

   > [!NOTE]
   > La extensión de nombre de archivo para todos los proyectos de este tipo es *.myproj*. Si desea cambiarlo, debe cambiarlo en todas partes que se menciona en el tutorial.

10. Reemplace el contenido existente por las siguientes líneas.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <SchemaVersion>2.0</SchemaVersion>
        <ProjectGuid></ProjectGuid>
        <OutputType>Exe</OutputType>
        <RootNamespace>MyRootNamespace</RootNamespace>
        <AssemblyName>MyAssemblyName</AssemblyName>
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        <DebugSymbols>true</DebugSymbols>
        <OutputPath>bin\Debug\</OutputPath>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
        <DebugSymbols>false</DebugSymbols>
        <OutputPath>bin\Release\</OutputPath>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="mscorlib" />
        <Reference Include="System" />
        <Reference Include="System.Data" />
        <Reference Include="System.Xml" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="AssemblyInfo.cs">
          <SubType>Code</SubType>
        </Compile>
        <Compile Include="Program.cs">
          <SubType>Code</SubType>
        </Compile>
      </ItemGroup>
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
    </Project>
    ```

11. Guarde el archivo.

12. En la ventana **Propiedades** , establezca la acción de **compilación** de *AssemblyInfo.cs*, *Program.cs*, *SimpleProject.ico*y *SimpleProject.myproj* en **Content**y establezca sus propiedades Include **in VSIX en** **True**.

    Esta plantilla de proyecto describe un proyecto básico de Visual C. que tiene una configuración de depuración y una configuración de versión. El proyecto incluye dos archivos de origen, *AssemblyInfo.cs* y *Program.cs,* y varias referencias de ensamblado. Cuando se crea un proyecto a partir de la plantilla, el Valor ProjectGuid se reemplaza automáticamente por un nuevo GUID.

    En el Explorador de **soluciones**, la carpeta **Plantillas** expandidas debe aparecer de la siguiente manera:

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>Crear una fábrica de proyectos básica
 Debe indicar a Visual Studio la ubicación de la carpeta de plantilla de proyecto. Para ello, agregue un atributo a la clase VSPackage que implementa el generador de proyectos para que la ubicación de la plantilla se escriba en el registro del sistema cuando se compila el VSPackage. Comience por crear un generador de proyectos básico que se identifica mediante un GUID de generador de proyectos. Utilice <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> el atributo para conectar `SimpleProjectPackage` el generador de proyectos a la clase.

### <a name="to-create-a-basic-project-factory"></a>Para crear una fábrica de proyectos básica

1. Cree GUID para el generador de proyectos (en el menú **Herramientas,** haga clic en **Crear GUID**) o use el del ejemplo siguiente. Agregue los GUID a `SimpleProjectPackage` la clase cerca de `PackageGuidString`la sección con el ya definido. Los GUID deben estar en forma GUID y forma de cadena. El código resultante debe ser similar al ejemplo siguiente.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. Agregue una clase a la carpeta *SimpleProject* superior denominada *SimpleProjectFactory.cs*.

3. Agregue lo siguiente mediante directivas:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Agregue un atributo `SimpleProjectFactory` GUID a la clase. El valor del atributo es el nuevo GUID de generador de proyectos.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Ahora puede registrar su plantilla de proyecto.

### <a name="to-register-the-project-template"></a>Para registrar la plantilla de proyecto

1. En *SimpleProjectPackage.cs*, <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> agregue `SimpleProjectPackage` un atributo a la clase, como se indica a continuación.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Vuelva a generar la solución y compruebe que se compila sin errores.

    La reconstrucción registra la plantilla de proyecto.

   Los `defaultProjectExtension` parámetros y `possibleProjectExtensions` se establecen en la extensión de nombre de archivo de proyecto (*.myproj*). El `projectTemplatesDirectory` parámetro se establece en la ruta relativa de la carpeta *Plantillas.* Durante la compilación, esta ruta de acceso se convertirá en una compilación completa y se agregará al registro para registrar el sistema del proyecto.

## <a name="test-the-template-registration"></a>Pruebe el registro de la plantilla
 El registro de plantilla indica a Visual Studio la ubicación de la carpeta de plantilla de proyecto para que Visual Studio pueda mostrar el nombre y el icono de la plantilla en el cuadro de diálogo **Nuevo proyecto.**

### <a name="to-test-the-template-registration"></a>Para probar el registro de la plantilla

1. Presione **F5** para iniciar la depuración de una instancia experimental de Visual Studio.

2. En la instancia experimental, cree un nuevo proyecto del tipo de proyecto recién creado. En el cuadro de diálogo **Nuevo proyecto,** debería ver **SimpleProject** en **Plantillas instaladas**.

   Ahora tiene una fábrica de proyectos que está registrada. Sin embargo, todavía no puede crear un proyecto. El paquete de proyecto y el generador de proyectos trabajan juntos para crear e inicializar un proyecto.

## <a name="add-the-managed-package-framework-code"></a>Agregue el código de Managed Package Framework
 Implemente la conexión entre el paquete del proyecto y el generador del proyecto.

- Importe los archivos de código fuente para Managed Package Framework.

    1. Descargue el proyecto SimpleProject (en el **Explorador**de soluciones , seleccione el nodo del proyecto y, en el menú contextual, haga clic en **Descargar proyecto**.) y abra el archivo de proyecto en el editor XML.

    2. Agregue los siguientes bloques al archivo \<de proyecto (justo encima de los bloques Importar>). Establézalo `ProjectBasePath` en la ubicación del archivo *ProjectBase.files* en el código de Managed Package Framework que acaba de descargar. Es posible que tenga que agregar una barra diagonal inversa al nombre de ruta de acceso. Si no lo hace, es posible que el proyecto no encuentre el código fuente de Managed Package Framework.

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > No olvide la barra diagonal inversa al final del camino.

    3. Vuelva a cargar el proyecto.

    4. Agregue referencias a los siguientes ensamblados:

        - `Microsoft.VisualStudio.Designer.Interfaces`(en * \<VSSDK instalar>, VisualStudioIntegration, Common, Assemblies, v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Para inicializar la fábrica del proyecto

1. En el archivo *SimpleProjectPackage.cs,* agregue la siguiente `using` directiva.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. Derive `SimpleProjectPackage` la `Microsoft.VisualStudio.Package.ProjectPackage`clase de .

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Registre la fábrica del proyecto. Agregue la siguiente `SimpleProjectPackage.Initialize` línea al `base.Initialize`método, justo después de .

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Implemente la `ProductUserContext`propiedad abstracta:

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. En *SimpleProjectFactory.cs*, `using` agregue la `using` siguiente directiva después de las directivas existentes.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. Derive `SimpleProjectFactory` la `ProjectFactory`clase de .

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Agregue el siguiente método `SimpleProjectFactory` ficticio a la clase. Implementará este método en una sección posterior.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Agregue el siguiente campo `SimpleProjectFactory` y constructor a la clase. Esta `SimpleProjectPackage` referencia se almacena en caché en un campo privado para que se pueda usar en la configuración de un sitio de proveedor de servicios.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Vuelva a generar la solución y compruebe que se compila sin errores.

## <a name="test-the-project-factory-implementation"></a>Pruebe la implementación de la fábrica del proyecto
 Compruebe si se llama al constructor de la implementación de fábrica de proyectos.

### <a name="to-test-the-project-factory-implementation"></a>Para probar la implementación de la fábrica del proyecto

1. En el *archivo SimpleProjectFactory.cs,* establezca un punto `SimpleProjectFactory` de interrupción en la línea siguiente en el constructor.

    ```csharp
    this.package = package;
    ```

2. Presione **F5** para iniciar una instancia experimental de Visual Studio.

3. En la instancia experimental, comience a crear un nuevo proyecto. En el cuadro de diálogo **Nuevo proyecto,** seleccione el tipo de proyecto **SimpleProject** y, a continuación, haga clic en **Aceptar**. La ejecución se detiene en el punto de interrupción.

4. Borre el punto de interrupción y detenga la depuración. Puesto que aún no hemos creado un nodo de proyecto, el código de creación del proyecto sigue generando excepciones.

## <a name="extend-the-projectnode-class"></a>Extender la clase ProjectNode
 Ahora puede implementar `SimpleProjectNode` la clase, que `ProjectNode` deriva de la clase. La `ProjectNode` clase base controla las siguientes tareas de creación de proyectos:

- Copia el archivo de plantilla de proyecto, *SimpleProject.myproj*, en la nueva carpeta del proyecto. Se cambia el nombre de la copia según el nombre que se introduce en el cuadro de diálogo **Nuevo proyecto.** El `ProjectGuid` valor de la propiedad se reemplaza por un nuevo GUID.

- Recorre los elementos de MSBuild del archivo de plantilla de `Compile` proyecto, *SimpleProject.myproj,* y busca elementos. Para `Compile` cada archivo de destino, copia el archivo en la nueva carpeta del proyecto.

  La clase `SimpleProjectNode` derivada controla estas tareas:

- Habilita los iconos de los nodos de proyecto y archivo en el Explorador de **soluciones** que se van a crear o seleccionar.

- Permite especificar sustituciones de parámetros de plantilla de proyecto adicionales.

### <a name="to-extend-the-projectnode-class"></a>Para extender la clase ProjectNode

1. Agregue una clase denominada `SimpleProjectNode.cs`.

2. Reemplace el código existente por el siguiente código.

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Project;

   namespace SimpleProject
   {
       public class SimpleProjectNode : ProjectNode
       {
           private SimpleProjectPackage package;

           public SimpleProjectNode(SimpleProjectPackage package)
           {
               this.package = package;
           }
           public override Guid ProjectGuid
           {
               get { return SimpleProjectPackage.guidSimpleProjectFactory; }
           }
           public override string ProjectType
           {
               get { return "SimpleProjectType"; }
           }

           public override void AddFileFromTemplate(
               string source, string target)
           {
               this.FileTemplateProcessor.UntokenFile(source, target);
               this.FileTemplateProcessor.Reset();
           }
       }
   }
   ```

   Esta `SimpleProjectNode` implementación de clase ha invalidado estos métodos:

- `ProjectGuid`, que devuelve el GUID del generador de proyectos.

- `ProjectType`, que devuelve el nombre localizado del tipo de proyecto.

- `AddFileFromTemplate`, que copia los archivos seleccionados de la carpeta de plantilla en el proyecto de destino. Este método se implementa en una sección posterior.

  El `SimpleProjectNode` constructor, `SimpleProjectFactory` al igual que `SimpleProjectPackage` el constructor, almacena en caché una referencia en un campo privado para su uso posterior.

  Para conectar `SimpleProjectFactory` la `SimpleProjectNode` clase a la clase, debe crear una instancia de un nuevo `SimpleProjectNode` en el `SimpleProjectFactory.CreateProject` método y almacenarla en caché en un campo privado para su uso posterior.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Para conectar la clase de generador de proyectos y la clase de nodo

1. En el archivo *SimpleProjectFactory.cs,* agregue la siguiente `using` directiva:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. Reemplace `SimpleProjectFactory.CreateProject` el método mediante el código siguiente.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Vuelva a generar la solución y compruebe que se compila sin errores.

## <a name="test-the-projectnode-class"></a>Pruebe la clase ProjectNode
 Pruebe el generador de proyectos para ver si crea una jerarquía de proyectos.

### <a name="to-test-the-projectnode-class"></a>Para probar la clase ProjectNode

1. Pulse **F5** para iniciar la depuración. En la instancia experimental, cree un nuevo SimpleProject.

2. Visual Studio debe llamar a la fábrica de proyectos para crear un proyecto.

3. Cierre la instancia experimental de Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Agregar un icono de nodo de proyecto personalizado
 El icono de nodo de proyecto en la sección anterior es un icono predeterminado. Puede cambiarlo a un icono personalizado.

### <a name="to-add-a-custom-project-node-icon"></a>Para agregar un icono de nodo de proyecto personalizado

1. En la carpeta **Resources** , agregue un archivo de mapa de bits denominado *SimpleProjectNode.bmp*.

2. En las **ventanas Propiedades,** reduzca el mapa de bits a 16 por 16 píxeles. Haga que el mapa de bits sea distintivo.

    ![Comando de proyecto simple](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. En la ventana **Propiedades,** cambie la **acción Generar** del mapa de bits a **Recurso incrustado**.

4. En *SimpleProjectNode.cs*, `using` agregue las siguientes directivas:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Agregue el siguiente campo estático `SimpleProjectNode` y constructor a la clase.

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Agregue la siguiente propiedad al `SimpleProjectNode` principio de la clase.

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. Reemplace el constructor de instancia por el código siguiente.

   ```csharp
   public SimpleProjectNode(SimpleProjectPackage package)
   {
       this.package = package;

       imageIndex = this.ImageHandler.ImageList.Images.Count;

       foreach (Image img in imageList.Images)
       {
           this.ImageHandler.AddImage(img);
       }
   }
   ```

   Durante la `SimpleProjectNode` construcción estática, recupera el mapa de bits del nodo del proyecto de los recursos del manifiesto del ensamblado y lo almacena en caché en un campo privado para su uso posterior. Observe la sintaxis de la ruta de acceso de la <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> imagen. Para ver los nombres de los recursos de <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> manifiesto incrustados en un ensamblado, utilice el método. Cuando este método se `SimpleProject` aplica al ensamblado, los resultados deben ser los siguientes:

- *SimpleProject.Resources.resources*

- *VisualStudio.Project.resources*

- *SimpleProject.VSPackage.resources*

- *Resources.imagelis.bmp*

- *Microsoft.VisualStudio.Project.DontShowAgainDialog.resources*

- *Microsoft.VisualStudio.Project.SecurityWarningDialog.resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Durante la construcción `ProjectNode` de instancias, la clase base carga *Resources.imagelis.bmp*, en el que se incrustan comúnmente 16 x 16 mapas de bits de *Resources-imagelis.bmp*. Esta lista de mapas `SimpleProjectNode` `ImageHandler.ImageList`de bits está disponible para como . `SimpleProjectNode`anexa el mapa de bits del nodo del proyecto a la lista. El desplazamiento del mapa de bits del nodo de proyecto en la `ImageIndex` lista de imágenes se almacena en caché para su uso posterior como valor de la propiedad pública. Visual Studio usa esta propiedad para determinar qué mapa de bits se mostrará como el icono del nodo del proyecto.

## <a name="test-the-custom-project-node-icon"></a>Pruebe el icono del nodo de proyecto personalizado
 Pruebe el generador de proyectos para ver si crea una jerarquía de proyectos que tiene el icono de nodo de proyecto personalizado.

### <a name="to-test-the-custom-project-node-icon"></a>Para probar el icono de nodo de proyecto personalizado

1. Inicie la depuración y, en la instancia experimental, cree un nuevo SimpleProject.

2. En el proyecto recién creado, observe que *SimpleProjectNode.bmp* se utiliza como el icono de nodo del proyecto.

     ![Nodo Nuevo proyecto Proyecto simple](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")

3. Abra el archivo *Program.cs* en el editor de código. Debería ver el código fuente similar al código siguiente.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;

    namespace $nameSpace$
    {
        public class $className$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

     Observe que los parámetros de plantilla $nameSpace$ y $className$ no tienen nuevos valores. Aprenderá a implementar la sustitución de parámetros de plantilla en la siguiente sección.

## <a name="substitute-template-parameters"></a>Parámetros de plantilla sustitutos
 En una sección anterior, registró la plantilla de `ProvideProjectFactory` proyecto con Visual Studio mediante el atributo. Registrar la ruta de acceso de una carpeta de plantilla de esta manera `ProjectNode.AddFileFromTemplate` le permite habilitar la sustitución de parámetros de plantilla básico reemplazando y expandiendo la clase. Para obtener más información, consulte Nueva generación de [proyectos: Bajo el capó, segunda parte.](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Ahora agregue código `AddFileFromTemplate` de reemplazo a la clase.

### <a name="to-substitute-template-parameters"></a>Para sustituir los parámetros de plantilla

1. En el archivo *SimpleProjectNode.cs,* agregue la siguiente `using` directiva.

   ```csharp
   using System.IO;
   ```

2. Reemplace `AddFileFromTemplate` el método mediante el código siguiente.

   ```csharp
   public override void AddFileFromTemplate(
       string source, string target)
   {
       string nameSpace =
           this.FileTemplateProcessor.GetFileNamespace(target, this);
       string className = Path.GetFileNameWithoutExtension(target);

       this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);
       this.FileTemplateProcessor.AddReplace("$className$", className);

       this.FileTemplateProcessor.UntokenFile(source, target);
       this.FileTemplateProcessor.Reset();
   }
   ```

3. Establezca un punto de interrupción `className` en el método, justo después de la instrucción de asignación.

   Las instrucciones de asignación determinan valores razonables para un espacio de nombres y un nuevo nombre de clase. Las `ProjectNode.FileTemplateProcessor.AddReplace` dos llamadas al método reemplazan los valores de parámetro de plantilla correspondientes mediante estos nuevos valores.

## <a name="test-the-template-parameter-substitution"></a>Pruebe la sustitución del parámetro de plantilla
 Ahora puede probar la sustitución de parámetros de plantilla.

### <a name="to-test-the-template-parameter-substitution"></a>Para probar la sustitución de parámetros de plantilla

1. Inicie la depuración y, en la instancia experimental, cree un nuevo SimpleProject.

2. La ejecución se detiene `AddFileFromTemplate` en el punto de interrupción del método.

3. Examine los valores `nameSpace` `className` de los parámetros y.

   - `nameSpace`se le da \<el valor del elemento de> De_Arracensel raíz en el archivo de plantilla de proyecto *.* En este caso, el valor es `MyRootNamespace`.

   - `className`recibe el valor del nombre de archivo de origen de clase, sin la extensión de nombre de archivo. En este caso, el primer archivo que se copia en la carpeta de destino se *AssemblyInfo.cs;* por lo tanto, el `AssemblyInfo`valor de className es .

4. Quite el punto de interrupción y presione **F5** para continuar la ejecución.

    Visual Studio debe terminar de crear un proyecto.

5. Abra el archivo *Program.cs* en el editor de código. Debería ver el código fuente similar al código siguiente.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;

   namespace MyRootNamespace
   {
       public class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

    Observe que el `MyRootNamespace` espacio de nombres `Program`es ahora y el nombre de clase es ahora .

6. Inicie la depuración del proyecto. El nuevo proyecto debe compilar, ejecutar y mostrar "Hello VSX!!!" en la ventana de la consola.

    ![Comando de proyecto simple](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   ¡Enhorabuena! Ha implementado un sistema de proyectos administrado básico.
