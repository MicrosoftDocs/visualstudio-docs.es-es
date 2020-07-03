---
title: Creación de un sistema de proyectos básico, parte 1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: e95f760712f46632120540091b9f8f408aad9da4
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903426"
---
# <a name="create-a-basic-project-system-part-1"></a>Crear un sistema de proyectos básico, parte 1
En Visual Studio, los proyectos son los contenedores que los desarrolladores usan para organizar los archivos de código fuente y otros recursos. Los proyectos aparecen como elementos secundarios de soluciones en el **Explorador de soluciones**. Los proyectos permiten organizar, compilar, depurar e implementar código fuente y crear referencias a servicios Web, bases de datos y otros recursos.

 Los proyectos de se definen en archivos de proyecto, por ejemplo, un archivo *. csproj* para un proyecto de Visual C#. Puede crear su propio tipo de proyecto que tenga su propia extensión de nombre de archivo de proyecto. Para obtener más información sobre los tipos de proyecto, vea [tipos de proyecto](../extensibility/internals/project-types.md).

> [!NOTE]
> Si necesita extender Visual Studio con un tipo de proyecto personalizado, se recomienda encarecidamente aprovechar el [sistema de proyectos de Visual Studio](https://github.com/Microsoft/VSProjectSystem) (VSPS), que tiene una serie de ventajas en comparación con la creación de un sistema de proyectos desde cero:
>
> - Incorporación más sencilla.  Incluso un sistema de proyectos básico requiere decenas de miles de líneas de código.  El aprovechamiento de VSPS reduce el costo de incorporación a unos pocos clics antes de que esté listo para personalizarlo según sus necesidades.
> - Mantenimiento más sencillo.  Al aprovechar VSPS, solo necesita mantener sus propios escenarios.  Nos encargamos del mantenimiento de toda la infraestructura del sistema del proyecto.
>
>   Si necesita tener como destino versiones de Visual Studio anteriores a Visual Studio 2013, no podrá aprovechar VSPS en una extensión de Visual Studio.  En ese caso, este tutorial es un buen lugar para comenzar.

 En este tutorial se muestra cómo crear un tipo de proyecto con la extensión de nombre de archivo de proyecto *. MyProj*. En este tutorial se toma prestado del sistema de proyectos de Visual C# existente.

> [!NOTE]
> Para obtener más ejemplos de proyectos de extensión, vea [ejemplos de VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

 En este tutorial se enseña cómo realizar estas tareas:

- Cree un tipo de proyecto básico.

- Cree una plantilla de proyecto básica.

- Registre la plantilla de proyecto con Visual Studio.

- Cree una instancia de proyecto; para ello, abra el cuadro de diálogo **nuevo proyecto** y, a continuación, use la plantilla.

- Cree un generador de proyectos para el sistema del proyecto.

- Cree un nodo de proyecto para el sistema del proyecto.

- Agregue iconos personalizados para el sistema del proyecto.

- Implementar la sustitución de parámetros de plantilla básica.

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

 También debe descargar el código fuente de [Managed Package Framework para los proyectos de](https://github.com/tunnelvisionlabs/MPFProj10). Extraiga el archivo en una ubicación que sea accesible para la solución que va a crear.

## <a name="create-a-basic-project-type"></a>Crear un tipo de proyecto básico
 Cree un proyecto VSIX de C# denominado **SimpleProject**. (**Archivo**  >  **Nueva**  >  **Proyecto** y, a continuación, extensibilidad de **Visual C#**  >  **Extensibility**  >  **Proyecto VSIX** Agregue una plantilla de elemento de proyecto de paquete de Visual Studio (en el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar**  >  **nuevo elemento**y, a continuación, vaya a **extensibilidad**  >  **Visual Studio Package**). Asigne al archivo el nombre *SimpleProjectPackage*.

## <a name="creating-a-basic-project-template"></a>Crear una plantilla de proyecto básica
 Ahora, puede modificar este VSPackage básico para implementar el nuevo tipo de proyecto *. MyProj* . Para crear un proyecto basado en el tipo de proyecto *. MyProj* , Visual Studio tiene que saber qué archivos, recursos y referencias se van a agregar al nuevo proyecto. Para proporcionar esta información, coloque los archivos de proyecto en una carpeta de plantillas de proyecto. Cuando un usuario usa el proyecto *. MyProj* para crear un proyecto, los archivos se copian en el nuevo proyecto.

### <a name="to-create-a-basic-project-template"></a>Para crear una plantilla de proyecto básica

1. Agregue tres carpetas al proyecto, una debajo de la otra: *Templates\Projects\SimpleProject*. (En **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto **SimpleProject** , seleccione **Agregar**y, a continuación, haga clic en **nueva carpeta**. Asigne a la carpeta el nombre *plantillas*. En la carpeta *plantillas* , agregue una carpeta denominada *Projects*. En la carpeta *proyectos* , agregue una carpeta denominada *SimpleProject*).

2. En la carpeta *Templates\Projects\SimpleProject* , agregue un archivo de imagen de mapa de bits para usarlo como el icono denominado *SimpleProject. ico*. Al hacer clic en **Agregar**, se abre el editor de iconos.

3. Haga que el icono sea distintivo. Este icono aparecerá en el cuadro de diálogo **nuevo proyecto** más adelante en el tutorial.

    ![Icono de proyecto simple](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. Guarde el icono y cierre el editor de iconos.

5. En la carpeta *Templates\Projects\SimpleProject* , agregue un elemento de **clase** denominado *Program.CS*.

6. Reemplace el código existente por las líneas siguientes.

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
   > Esta no es la forma final del código *Program.CS* ; los parámetros de reemplazo se tratarán en un paso posterior. Es posible que vea errores de compilación, pero siempre que el **contenido**de la **BuildAction** del archivo sea, debería poder compilar y ejecutar el proyecto como de costumbre.

7. Guarde el archivo.

8. Copie el archivo *AssemblyInfo.CS* de la carpeta *Properties* en la carpeta *Projects\SimpleProject* .

9. En la carpeta *Projects\SimpleProject* , agregue un archivo XML denominado *SimpleProject. MyProj*.

   > [!NOTE]
   > La extensión de nombre de archivo de todos los proyectos de este tipo es *. MyProj*. Si desea cambiarlo, debe cambiarlo en cualquier lugar en el que se mencione en el tutorial.

10. Reemplace el contenido existente por las líneas siguientes.

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

12. En la ventana **propiedades** , establezca la **acción de compilación** de *AssemblyInfo.CS*, *Program.CS*, *SimpleProject. ico*y *SimpleProject. MYPROJ* en **Content**, y establezca su **include en** las propiedades VSIX en **true**.

    Esta plantilla de proyecto describe un proyecto básico de Visual C# que tiene una configuración de depuración y una configuración de versión. El proyecto incluye dos archivos de código fuente, *AssemblyInfo.CS* y *Program.CS*, y varias referencias de ensamblado. Cuando se crea un proyecto a partir de la plantilla, el valor de ProjectGuid se reemplaza automáticamente por un nuevo GUID.

    En **Explorador de soluciones**, la carpeta de **plantillas** expandidas debe aparecer de la siguiente manera:

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>Creación de un generador de proyectos básico
 Debe indicar a Visual Studio la ubicación de la carpeta de plantillas de proyecto. Para ello, agregue un atributo a la clase VSPackage que implementa el generador de proyectos, de modo que la ubicación de la plantilla se escriba en el registro del sistema cuando se compile el VSPackage. Empiece por crear un generador de proyectos básico que se identifica mediante un GUID de generador de proyectos. Use el <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atributo para conectar el generador de proyectos a la `SimpleProjectPackage` clase.

### <a name="to-create-a-basic-project-factory"></a>Para crear un generador de proyectos básico

1. Cree GUID para el generador de proyectos (en el menú **herramientas** , haga clic en **crear GUID**) o use uno en el ejemplo siguiente. Agregue los GUID a la `SimpleProjectPackage` clase cerca de la sección con el ya definido `PackageGuidString` . Los GUID deben estar en formato de GUID y de cadena. El código resultante debe ser similar al ejemplo siguiente.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. Agregue una clase a la carpeta Top *SimpleProject* denominada *SimpleProjectFactory.CS*.

3. Agregue lo siguiente mediante directivas:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Agregue un atributo GUID a la `SimpleProjectFactory` clase. El valor del atributo es el nuevo GUID del generador de proyectos.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Ahora puede registrar la plantilla de proyecto.

### <a name="to-register-the-project-template"></a>Para registrar la plantilla de proyecto

1. En *SimpleProjectPackage.CS*, agregue un <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atributo a la `SimpleProjectPackage` clase, como se indica a continuación.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Recompile la solución y compruebe que se compila sin errores.

    Al volver a generar, se registra la plantilla de proyecto.

   Los parámetros `defaultProjectExtension` y `possibleProjectExtensions` se establecen en la extensión de nombre de archivo de proyecto (*. MyProj*). El `projectTemplatesDirectory` parámetro se establece en la ruta de acceso relativa de la carpeta de *plantillas* . Durante la compilación, esta ruta de acceso se convertirá en una compilación completa y se agregará al registro para registrar el sistema del proyecto.

## <a name="test-the-template-registration"></a>Prueba del registro de la plantilla
 El registro de plantillas indica a Visual Studio la ubicación de la carpeta de plantillas de proyecto para que Visual Studio pueda mostrar el nombre de la plantilla y el icono en el cuadro de diálogo **nuevo proyecto** .

### <a name="to-test-the-template-registration"></a>Para probar el registro de la plantilla

1. Presione **F5** para iniciar la depuración de una instancia experimental de Visual Studio.

2. En la instancia experimental, cree un nuevo proyecto del tipo de proyecto recién creado. En el cuadro de diálogo **nuevo proyecto** , debería ver **SimpleProject** en **plantillas instaladas**.

   Ahora tiene un generador de proyectos registrado. Sin embargo, aún no puede crear un proyecto. El paquete del proyecto y el generador del proyecto funcionan juntos para crear e inicializar un proyecto.

## <a name="add-the-managed-package-framework-code"></a>Agregar el código de Managed Package Framework
 Implemente la conexión entre el paquete de proyecto y el generador de proyectos.

- Importe los archivos de código fuente para el marco de trabajo de paquetes administrados.

    1. Descargue el proyecto SimpleProject (en **Explorador de soluciones**, seleccione el nodo del proyecto y, en el menú contextual, haga clic en **descargar el proyecto**) y abra el archivo del proyecto en el editor XML.

    2. Agregue los siguientes bloques al archivo de proyecto (justo encima de los \<Import> bloques). Establézcalo en `ProjectBasePath` la ubicación del archivo *ProjectBase. files* en el código de Managed Package Framework que acaba de descargar. Es posible que tenga que agregar una barra diagonal inversa al directorio. Si no lo hace, es posible que el proyecto no encuentre el código fuente de Managed Package Framework.

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > No olvide la barra diagonal inversa al final de la ruta de acceso.

    3. Vuelva a cargar el proyecto.

    4. Agregue referencias a los siguientes ensamblados:

        - `Microsoft.VisualStudio.Designer.Interfaces`(en * \<VSSDK install> \VisualStudioIntegration\Common\Assemblies\v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Para inicializar el generador de proyectos

1. En el archivo *SimpleProjectPackage.CS* , agregue la siguiente `using` Directiva.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. Derive la `SimpleProjectPackage` clase de `Microsoft.VisualStudio.Package.ProjectPackage` .

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Registre el generador de proyectos. Agregue la siguiente línea al `SimpleProjectPackage.Initialize` método, justo después de `base.Initialize` .

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Implemente la propiedad abstracta `ProductUserContext` :

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. En *SimpleProjectFactory.CS*, agregue la siguiente `using` Directiva después de las `using` directivas existentes.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. Derive la `SimpleProjectFactory` clase de `ProjectFactory` .

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Agregue el siguiente método ficticio a la `SimpleProjectFactory` clase. Este método se implementará en una sección posterior.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Agregue el siguiente campo y constructor a la `SimpleProjectFactory` clase. Esta `SimpleProjectPackage` referencia se almacena en caché en un campo privado para que se pueda usar en la configuración de un sitio de proveedor de servicios.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Recompile la solución y compruebe que se compila sin errores.

## <a name="test-the-project-factory-implementation"></a>Prueba de la implementación del generador de proyectos
 Compruebe si se llama al constructor de la implementación del generador de proyectos.

### <a name="to-test-the-project-factory-implementation"></a>Para probar la implementación del generador de proyectos

1. En el archivo *SimpleProjectFactory.CS* , establezca un punto de interrupción en la línea siguiente en el `SimpleProjectFactory` constructor.

    ```csharp
    this.package = package;
    ```

2. Presione **F5** para iniciar una instancia experimental de Visual Studio.

3. En la instancia experimental, empiece a crear un nuevo proyecto. En el cuadro de diálogo **nuevo proyecto** , seleccione el tipo de proyecto **SimpleProject** y, a continuación, haga clic en **Aceptar**. La ejecución se detiene en el punto de interrupción.

4. Borre el punto de interrupción y detenga la depuración. Puesto que aún no hemos creado un nodo de proyecto, el código de creación del proyecto todavía produce excepciones.

## <a name="extend-the-projectnode-class"></a>Extensión de la clase ProjectNode
 Ahora puede implementar la `SimpleProjectNode` clase, que deriva de la `ProjectNode` clase. La `ProjectNode` clase base controla las siguientes tareas de creación del proyecto:

- Copia el archivo de plantilla de proyecto, *SimpleProject. MyProj*, en la nueva carpeta de proyecto. Se cambia el nombre de la copia según el nombre especificado en el cuadro de diálogo **nuevo proyecto** . El `ProjectGuid` valor de la propiedad se sustituye por un nuevo GUID.

- Atraviesa los elementos de MSBuild del archivo de plantilla de proyecto, *SimpleProject. MyProj*, y busca `Compile` los elementos. Para cada `Compile` archivo de destino, copia el archivo en la nueva carpeta de proyecto.

  La `SimpleProjectNode` clase derivada controla estas tareas:

- Habilita los iconos para los nodos de proyecto y archivo en **Explorador de soluciones** que se van a crear o seleccionar.

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

   Esta `SimpleProjectNode` implementación de clase tiene estos métodos invalidados:

- `ProjectGuid`, que devuelve el GUID del generador de proyectos.

- `ProjectType`, que devuelve el nombre localizado del tipo de proyecto.

- `AddFileFromTemplate`, que copia los archivos seleccionados de la carpeta de plantillas en el proyecto de destino. Este método se implementa en una sección posterior.

  El `SimpleProjectNode` constructor, al igual que el `SimpleProjectFactory` constructor, almacena `SimpleProjectPackage` en caché una referencia en un campo privado para su uso posterior.

  Para conectar la `SimpleProjectFactory` clase a la `SimpleProjectNode` clase, debe crear una instancia de un nuevo `SimpleProjectNode` en el `SimpleProjectFactory.CreateProject` método y almacenarlo en caché en un campo privado para su uso posterior.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Para conectar la clase de generador de proyectos y la clase node

1. En el archivo *SimpleProjectFactory.CS* , agregue la siguiente `using` Directiva:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. Reemplace el `SimpleProjectFactory.CreateProject` método mediante el código siguiente.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Recompile la solución y compruebe que se compila sin errores.

## <a name="test-the-projectnode-class"></a>Prueba de la clase ProjectNode
 Pruebe el generador de proyectos para ver si crea una jerarquía de proyecto.

### <a name="to-test-the-projectnode-class"></a>Para probar la clase ProjectNode

1. Pulse **F5** para iniciar la depuración. En la instancia experimental, cree un nuevo SimpleProject.

2. Visual Studio debe llamar al generador de proyectos para crear un proyecto.

3. Cierre la instancia experimental de Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Icono Agregar un nodo de proyecto personalizado
 El icono del nodo de proyecto de la sección anterior es un icono predeterminado. Puede cambiarlo a un icono personalizado.

### <a name="to-add-a-custom-project-node-icon"></a>Para agregar un icono de nodo de proyecto personalizado

1. En la carpeta **recursos** , agregue un archivo de mapa de bits denominado *SimpleProjectNode.bmp*.

2. En las ventanas **propiedades** , reduzca el mapa de bits a 16 por 16 píxeles. Haga que el mapa de bits sea distintivo.

    ![Comando de proyecto simple](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. En la ventana **propiedades** , cambie la **acción de compilación** del mapa de bits a **recurso incrustado**.

4. En *SimpleProjectNode.CS*, agregue las siguientes `using` directivas:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Agregue el siguiente campo estático y el constructor a la `SimpleProjectNode` clase.

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Agregue la siguiente propiedad al principio de la `SimpleProjectNode` clase.

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

   Durante la construcción estática, `SimpleProjectNode` recupera el mapa de bits del nodo de proyecto de los recursos del manifiesto del ensamblado y lo almacena en un campo privado para su uso posterior. Observe la sintaxis de la <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> ruta de acceso de la imagen. Para ver los nombres de los recursos del manifiesto insertados en un ensamblado, use el <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> método. Cuando este método se aplica al `SimpleProject` ensamblado, los resultados deberían ser los siguientes:

- *SimpleProject. Resources. Resources*

- *VisualStudio. Project. Resources*

- *SimpleProject. VSPackage. Resources*

- *Resources.imagelis.bmp*

- *Microsoft. VisualStudio. Project. DontShowAgainDialog. Resources*

- *Microsoft. VisualStudio. Project. SecurityWarningDialog. Resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Durante la construcción de la instancia, la `ProjectNode` clase base carga *Resources.imagelis.bmp*, en las que se utilizan habitualmente 16 x 16 mapas de bits de *Resources\imagelis.bmp*. Esta lista de mapas de bits se pone a disposición de `SimpleProjectNode` como `ImageHandler.ImageList` . `SimpleProjectNode`anexa el mapa de bits del nodo de proyecto a la lista. El desplazamiento del mapa de bits del nodo de proyecto en la lista de imágenes se almacena en caché para su uso posterior como valor de la `ImageIndex` propiedad pública. Visual Studio usa esta propiedad para determinar qué mapa de bits se debe mostrar como el icono del nodo de proyecto.

## <a name="test-the-custom-project-node-icon"></a>Probar el icono del nodo de proyecto personalizado
 Pruebe el generador de proyectos para ver si crea una jerarquía de proyecto que tenga el icono de nodo de proyecto personalizado.

### <a name="to-test-the-custom-project-node-icon"></a>Para probar el icono del nodo de proyecto personalizado

1. Inicie la depuración y, en la instancia experimental, cree un nuevo SimpleProject.

2. En el proyecto creado recientemente, observe que *SimpleProjectNode.bmp* se usa como el icono del nodo del proyecto.

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

     Tenga en cuenta que los parámetros de plantilla $nameSpace $ y $className $ no tienen nuevos valores. Obtendrá información sobre cómo implementar la sustitución de parámetros de plantilla en la sección siguiente.

## <a name="substitute-template-parameters"></a>Sustituir parámetros de plantilla
 En una sección anterior, registró la plantilla de proyecto con Visual Studio mediante el `ProvideProjectFactory` atributo. El registro de la ruta de acceso de una carpeta de plantilla de esta manera le permite habilitar la sustitución de parámetros de plantilla básica invalidando y expandiendo la `ProjectNode.AddFileFromTemplate` clase. Para obtener más información, vea [nueva generación de proyectos: debajo del capó, parte dos](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Ahora, agregue el código de reemplazo a la `AddFileFromTemplate` clase.

### <a name="to-substitute-template-parameters"></a>Para sustituir los parámetros de plantilla

1. En el archivo *SimpleProjectNode.CS* , agregue la siguiente `using` Directiva.

   ```csharp
   using System.IO;
   ```

2. Reemplace el `AddFileFromTemplate` método mediante el código siguiente.

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

3. Establezca un punto de interrupción en el método, justo después de la `className` instrucción de asignación.

   Las instrucciones de asignación determinan valores razonables para un espacio de nombres y un nuevo nombre de clase. Las dos `ProjectNode.FileTemplateProcessor.AddReplace` llamadas al método reemplazan los valores de parámetro de plantilla correspondientes mediante estos nuevos valores.

## <a name="test-the-template-parameter-substitution"></a>Prueba de la sustitución de parámetros de plantilla
 Ahora puede probar la sustitución de parámetros de plantilla.

### <a name="to-test-the-template-parameter-substitution"></a>Para probar la sustitución de parámetros de plantilla

1. Inicie la depuración y, en la instancia experimental, cree un nuevo SimpleProject.

2. La ejecución se detiene en el punto de interrupción en el `AddFileFromTemplate` método.

3. Examine los valores de los `nameSpace` `className` parámetros y.

   - `nameSpace`se proporciona el valor del \<RootNamespace> elemento en el archivo de plantilla de proyecto *\Templates\Projects\SimpleProject\SimpleProject.MyProj* . En este caso, el valor es `MyRootNamespace`.

   - `className`se proporciona el valor del nombre del archivo de código fuente de la clase, sin la extensión de nombre de archivo. En este caso, el primer archivo que se va a copiar en la carpeta de destino es *AssemblyInfo.CS*; por lo tanto, el valor de className es `AssemblyInfo` .

4. Quite el punto de interrupción y presione **F5** para continuar con la ejecución.

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

    Observe que el espacio de nombres es ahora `MyRootNamespace` y el nombre de la clase es ahora `Program` .

6. Inicie la depuración del proyecto. El nuevo proyecto debe compilarse, ejecutarse y mostrar "Hello VSX!!!" en la ventana de la consola.

    ![Comando de proyecto simple](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   ¡Enhorabuena! Ha implementado un sistema de proyectos administrado básico.
