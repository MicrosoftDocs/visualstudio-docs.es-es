---
title: Creación de un sistema de proyectos básico, parte 1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19c73e47e8c07ebcf7c1124e6e59d80f76101458
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341656"
---
# <a name="create-a-basic-project-system-part-1"></a>Crear un sistema de proyectos básico, parte 1
En Visual Studio, los proyectos son los contenedores que los desarrolladores usan para organizar los archivos de código fuente y otros activos. Los proyectos aparecen como elementos secundarios de soluciones en la **el Explorador de soluciones**. Los proyectos permiten organizar, compilar, depurar e implementar el código fuente y crear referencias a servicios Web, bases de datos y otros recursos.

 Los proyectos se definen en archivos de proyecto, por ejemplo un *.csproj* archivo para un proyecto de Visual C#. Puede crear su propio tipo de proyecto que tiene su propia extensión de nombre de archivo de proyecto. Para obtener más información acerca de los tipos de proyecto, vea [tipos de proyecto](../extensibility/internals/project-types.md).

> [!NOTE]
> Si necesita ampliar Visual Studio con un tipo de proyecto personalizado, se recomienda aprovechar el [sistema de proyectos de Visual Studio](https://github.com/Microsoft/VSProjectSystem) (vsp) que tiene una serie de ventajas con respecto a la creación de un sistema de proyecto desde cero:
>
> - Incorporación de más fácil.  Incluso en un sistema de proyectos básico requiere decenas de miles de líneas de código.  Aprovechamiento de VSPS reduce el costo de incorporación a unos pocos clics antes de que esté listo para personalizarlo según sus necesidades.
> - Mantenimiento más sencillo.  Al aprovechar VSPS, basta con mantener sus propios escenarios.  Nosotros nos encargaremos de mantenimiento de toda la infraestructura de sistema de proyecto.
>
>   Si necesita destinadas a versiones de Visual Studio anteriores a Visual Studio 2013, no podrá aprovechar VSPS en una extensión de Visual Studio.  Si es así, en este tutorial es un buen lugar para empezar a trabajar.

 En este tutorial se muestra cómo crear un tipo de proyecto que tiene la extensión de nombre de archivo de proyecto *.myproj*. En este tutorial adopta el sistema de proyectos de Visual C# existente.

> [!NOTE]
> Para obtener más ejemplos de proyectos de extensión, vea [muestras de VSSDK](https://aka.ms/vs2015sdksamples).

 En este tutorial se enseña cómo realizar estas tareas:

- Crear un tipo de proyecto básico.

- Crear una plantilla de proyecto básico.

- Registre la plantilla de proyecto con Visual Studio.

- Crear una instancia de proyecto abriendo el **nuevo proyecto** cuadro de diálogo y, a continuación, usar la plantilla.

- Crear un generador de proyectos para el sistema del proyecto.

- Crear un nodo de proyecto para el sistema del proyecto.

- Agregar iconos personalizados para el sistema del proyecto.

- Implementar la sustitución de parámetros de plantilla básica.

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

 También debe descargar el código fuente para el [Managed Package Framework para proyectos](https://github.com/tunnelvisionlabs/MPFProj10). Extraiga el archivo en una ubicación que sea accesible a la solución que se va a crear.

## <a name="create-a-basic-project-type"></a>Crear un tipo de proyecto básico
 Cree un proyecto de VSIX de C# denominado **SimpleProject**. (**Archivo** > **nueva** > **proyecto** y, a continuación, **Visual C#**  >   **Extensibilidad** > **proyecto VSIX**). Agregar una plantilla de elemento de proyecto de paquete de Visual Studio (en el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **agregar** > **nuevo elemento**, a continuación, vaya a **Extensibilidad** > **paquete de Visual Studio**). Nombre del archivo *SimpleProjectPackage*.

## <a name="creating-a-basic-project-template"></a>Creación de una plantilla de proyecto básico
 Ahora, puede modificar este VSPackage básico para implementar el nuevo *.myproj* tipo de proyecto. Para crear un proyecto que se basa en el *.myproj* tipo de proyecto, Visual Studio tiene que saber qué archivos, recursos y referencias para agregar al nuevo proyecto. Para proporcionar esta información, coloque los archivos de proyecto en una carpeta de plantillas de proyecto. Cuando un usuario usa el *.myproj* de proyecto para crear un proyecto, los archivos se copian al nuevo proyecto.

### <a name="to-create-a-basic-project-template"></a>Para crear una plantilla de proyecto básico

1. Agregue tres carpetas al proyecto, uno en la otra: *Templates\Projects\SimpleProject*. (En **el Explorador de soluciones**, haga clic en el **SimpleProject** nodo de proyecto, seleccione **agregar**y, a continuación, haga clic en **nueva carpeta**. Nombre de la carpeta *plantillas*. En el *plantillas* carpeta, agregue una carpeta denominada *proyectos*. En el *proyectos* carpeta, agregue una carpeta denominada *SimpleProject*.)

2. En el *Templates\Projects\SimpleProject* carpeta, agregue un archivo de imagen de mapa de bits que se usará como el icono denominado *SimpleProject.ico*. Al hacer clic en **agregar**, se abre el editor de iconos.

3. Hacer que el icono distintivo. Este icono aparecerá en el **nuevo proyecto** cuadro de diálogo más adelante en el tutorial.

    ![Simple Project Icon](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. El icono Guardar y cerrar el editor de iconos.

5. En el *Templates\Projects\SimpleProject* carpeta, agregue un **clase** denominado elemento *Program.cs*.

6. Reemplace el código existente con las siguientes líneas.

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
   > Esto no es la forma final de la *Program.cs* código; el reemplazo de parámetros se tratarán en un paso posterior. Es posible que vea errores de compilación, pero siempre que el archivo **BuildAction** es **contenido**, podrá compilar y ejecutar el proyecto como de costumbre.

7. Guarde el archivo.

8. Copia el *AssemblyInfo.cs* de archivos desde el *propiedades* carpeta a la *Projects\SimpleProject* carpeta.

9. En el *Projects\SimpleProject* carpeta agregar un archivo XML denominado *SimpleProject.myproj*.

   > [!NOTE]
   > La extensión de nombre de archivo para todos los proyectos de este tipo es *.myproj*. Si desea cambiarla, debe cambiarla en todas partes que se menciona en el tutorial.

10. Reemplace el contenido existente con las siguientes líneas.

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

12. En el **propiedades** ventana, establezca el **acción de compilación** de *AssemblyInfo.cs*, *Program.cs*, *SimpleProject.ico* , y *SimpleProject.myproj* a **contenido**y establezca sus **incluir en VSIX** propiedades a **True**.

    Esta plantilla de proyecto describe un proyecto básico de Visual C# que tiene una configuración de depuración y una configuración de lanzamiento. El proyecto incluye dos archivos de código fuente, *AssemblyInfo.cs* y *Program.cs*y varias referencias de ensamblado. Cuando se crea un proyecto de la plantilla, el valor de ProjectGuid automáticamente se sustituye por un nuevo GUID.

    En **el Explorador de soluciones**, ampliado **plantillas** carpeta debería aparecer como sigue:

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>Crear un generador de proyectos básico
 Debe indicar la ubicación de la carpeta de plantillas de proyecto a Visual Studio. Para ello, agregue un atributo a la clase de VSPackage que implementa el generador de proyectos para que la ubicación de la plantilla se escribe en el registro del sistema cuando se compila el VSPackage. Empiece por crear un generador de proyectos básico que se identifica mediante un GUID de generador de proyectos. Use la <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atributo para conectar el generador de proyectos para el `SimpleProjectPackage` clase.

### <a name="to-create-a-basic-project-factory"></a>Para crear un generador de proyectos básico

1. Creación de GUID para el generador de proyectos (en el **herramientas** menú, haga clic en **crear GUID**), o utilizar uno en el ejemplo siguiente. Agregue los GUID para el `SimpleProjectPackage` clase cerca de la sección con ya definido `PackageGuidString`. Los GUID deben estar en formato GUID y en forma de cadena. El código resultante debe parecerse al ejemplo siguiente.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. Agregue una clase a la parte superior *SimpleProject* carpeta denominada *SimpleProjectFactory.cs*.

3. Agregue las siguientes instrucciones using:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Agregue un atributo GUID a la `SimpleProjectFactory` clase. El valor del atributo es el generador de proyectos nuevos GUID.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Ahora puede registrar la plantilla de proyecto.

### <a name="to-register-the-project-template"></a>Para registrar la plantilla de proyecto

1. En *SimpleProjectPackage.cs*, agregue un <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atributo a la `SimpleProjectPackage` clase, como se indica a continuación.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Recompile la solución y comprobar que se compila sin errores.

    Volver a generar, registra la plantilla de proyecto.

   Los parámetros `defaultProjectExtension` y `possibleProjectExtensions` se establecen en la extensión de nombre de archivo de proyecto ( *.myproj*). El `projectTemplatesDirectory` parámetro se establece en la ruta de acceso relativa de la *plantillas* carpeta. Durante la compilación, esta ruta de acceso se convierte en una compilación completa y agrega al registro para registrar el sistema del proyecto.

## <a name="test-the-template-registration"></a>Probar el registro de plantilla
 Registro de plantilla indica a Visual Studio la ubicación de la carpeta de plantillas de proyecto para que Visual Studio puede mostrar el nombre de la plantilla y el icono en el **nuevo proyecto** cuadro de diálogo.

### <a name="to-test-the-template-registration"></a>Para probar el registro de plantilla

1. Presione **F5** para iniciar la depuración de una instancia experimental de Visual Studio.

2. En la instancia experimental, cree un nuevo proyecto del tipo de proyecto recién creado. En el **nuevo proyecto** cuadro de diálogo, debería ver **SimpleProject** en **plantillas instaladas**.

   Ahora tiene un generador de proyectos que se ha registrado. Sin embargo, todavía no puede crear un proyecto. El paquete del proyecto y el generador de proyectos que funcionan conjuntamente para crear e inicializar un proyecto.

## <a name="add-the-managed-package-framework-code"></a>Agregue el código de Managed Package Framework
 Implementar la conexión entre el paquete del proyecto y el generador de proyectos.

- Importe los archivos de código fuente de Managed Package Framework.

    1. Descargue el proyecto SimpleProject (en **el Explorador de soluciones**, seleccione el nodo del proyecto y en el menú contextual, haga clic en **descargar el proyecto**.) y abra el archivo de proyecto en el editor XML.

    2. Agregue los siguientes bloques de archivo de proyecto (justo encima el \<importación > bloques). Establecer `ProjectBasePath` a la ubicación de la *ProjectBase.files* archivo en el que acaba de descargar el código de Managed Package Framework. Es posible que deba agregar una barra diagonal inversa a la ruta de acceso. Si no lo hace, se puede producir un error en el proyecto encontrar el código fuente de Managed Package Framework.

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

        - `Microsoft.VisualStudio.Designer.Interfaces` (en  *\<install VSSDK > \VisualStudioIntegration\Common\Assemblies\v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Para inicializar el generador de proyectos

1. En el *SimpleProjectPackage.cs* , agregue la siguiente `using` instrucción.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. Derivar la `SimpleProjectPackage` clase `Microsoft.VisualStudio.Package.ProjectPackage`.

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Registre el generador de proyectos. Agregue la siguiente línea a la `SimpleProjectPackage.Initialize` método, justo después `base.Initialize`.

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Implementa la propiedad abstracta `ProductUserContext`:

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. En *SimpleProjectFactory.cs*, agregue la siguiente `using` instrucción posterior a la existente `using` instrucciones.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. Derivar la `SimpleProjectFactory` clase `ProjectFactory`.

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Agregue el siguiente método ficticio para el `SimpleProjectFactory` clase. Este método que implementará en una sección posterior.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Agregue el siguiente campo y el constructor para la `SimpleProjectFactory` clase. Esto `SimpleProjectPackage` referencia se almacena en caché en un campo privado para que se puede usar en la configuración de un sitio de proveedor de servicio.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Recompile la solución y comprobar que se compila sin errores.

## <a name="test-the-project-factory-implementation"></a>Probar la implementación del generador de proyecto
 Comprobar si se llama al constructor para su implementación del generador de proyecto.

### <a name="to-test-the-project-factory-implementation"></a>Para probar la implementación del generador de proyecto

1. En el *SimpleProjectFactory.cs* de archivos, establezca un punto de interrupción en la línea siguiente en el `SimpleProjectFactory` constructor.

    ```csharp
    this.package = package;
    ```

2. Presione **F5** para iniciar una instancia experimental de Visual Studio.

3. En la instancia experimental, comience a crear un nuevo proyecto. En el **nuevo proyecto** cuadro de diálogo, seleccione el **SimpleProject** tipo de proyecto y, a continuación, haga clic en **Aceptar**. La ejecución se detiene en el punto de interrupción.

4. Desactive el punto de interrupción y detener la depuración. Dado que aún no hemos creado un nodo de proyecto, el código de creación del proyecto todavía inicia excepciones.

## <a name="extend-the-projectnode-class"></a>Extender la clase ProjectNode
 Ahora puede implementar la `SimpleProjectNode` (clase), que se deriva de la `ProjectNode` clase. La `ProjectNode` clase base controla las siguientes tareas de creación del proyecto:

- Copia el archivo de plantilla de proyecto, *SimpleProject.myproj*, a la nueva carpeta de proyecto. Se cambia el nombre de la copia según el nombre especificado en el **nuevo proyecto** cuadro de diálogo. El `ProjectGuid` el valor de propiedad se sustituye por un nuevo GUID.

- Recorre los elementos de MSBuild del archivo de plantilla del proyecto, *SimpleProject.myproj*y busca `Compile` elementos. Para cada `Compile` archivo de destino, copia el archivo a la nueva carpeta de proyecto.

  La clase derivada `SimpleProjectNode` clase controla estas tareas:

- Permite que los iconos para los nodos de proyecto y archivo en **el Explorador de soluciones** que deben crearse o seleccionado.

- Habilita las sustituciones de parámetros de plantilla de proyecto adicionales especificarse.

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

   Esto `SimpleProjectNode` implementación de la clase tiene estos métodos invalidados:

- `ProjectGuid`, que devuelve el GUID del generador de proyectos.

- `ProjectType`, que devuelve el nombre localizado del tipo de proyecto.

- `AddFileFromTemplate`, que copia los archivos seleccionados de la carpeta de plantillas para el proyecto de destino. Además, este método se implementa en una sección posterior.

  El `SimpleProjectNode` constructor, como el `SimpleProjectFactory` constructor, almacena en caché un `SimpleProjectPackage` referencia en un campo privado para su uso posterior.

  Para conectar el `SimpleProjectFactory` clase a la `SimpleProjectNode` (clase), debe crear una nueva instancia `SimpleProjectNode` en el `SimpleProjectFactory.CreateProject` método y lo almacena en caché en un campo privado para su uso posterior.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Para conectarse a la clase de generador de proyecto y la clase de nodo

1. En el *SimpleProjectFactory.cs* , agregue la siguiente `using` instrucción:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. Reemplace el `SimpleProjectFactory.CreateProject` método utilizando el código siguiente.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Recompile la solución y comprobar que se compila sin errores.

## <a name="test-the-projectnode-class"></a>Probar la clase ProjectNode
 Pruebe el generador de proyectos para ver si crea una jerarquía de proyectos.

### <a name="to-test-the-projectnode-class"></a>Para probar la clase ProjectNode

1. Presiona **F5** para iniciar la depuración. En la instancia experimental, cree un nuevo SimpleProject.

2. Visual Studio debe llamar a la factoría de proyecto para crear un proyecto.

3. Cierre la instancia experimental de Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Agregar un icono de nodo de proyecto personalizadas
 El icono del nodo de proyecto en la sección anterior es un icono predeterminado. Se puede cambiar a un icono personalizado.

### <a name="to-add-a-custom-project-node-icon"></a>Para agregar un icono de nodo de proyecto personalizadas

1. En el **recursos** carpeta, agregue un archivo de mapa de bits denominado *SimpleProjectNode.bmp*.

2. En el **propiedades** windows, reduzca el mapa de bits a 16 por 16 píxeles. Asegúrese de distintivo el mapa de bits.

    ![Simple Project Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. En el **propiedades** ventana, cambie el **acción de compilación** del mapa de bits a **recurso incrustado**.

4. En *SimpleProjectNode.cs*, agregue las siguientes `using` instrucciones:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Agregue el siguiente campo estático y el constructor para la `SimpleProjectNode` clase.

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

7. Reemplace el constructor de instancia con el código siguiente.

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

   Durante la construcción estática, `SimpleProjectNode` recupera el mapa de bits del nodo de proyecto de los recursos de manifiesto de ensamblado y lo guarda en un campo privado para su uso posterior. Tenga en cuenta la sintaxis de la <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> ruta de acceso de imagen. Para ver los nombres de los recursos de manifiesto incrustados en un ensamblado, use el <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> método. Cuando este método se aplica a la `SimpleProject` ensamblado, los resultados deben ser como sigue:

- *SimpleProject.Resources.resources*

- *VisualStudio.Project.resources*

- *SimpleProject.VSPackage.resources*

- *Resources.imagelis.bmp*

- *Microsoft.VisualStudio.Project.DontShowAgainDialog.resources*

- *Microsoft.VisualStudio.Project.SecurityWarningDialog.resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Durante la construcción de la instancia, el `ProjectNode` base clase cargas *Resources.imagelis.bmp*, en que se incrustan normalmente usa mapas de bits de 16 x 16 de *Resources\imagelis.bmp*. Esta lista de mapa de bits debe ponerse a disposición `SimpleProjectNode` como `ImageHandler.ImageList`. `SimpleProjectNode` Anexa el mapa de bits del nodo de proyecto a la lista. El desplazamiento del mapa de bits de nodo de proyecto en la lista de imágenes se almacenan en caché para su uso posterior como el valor del público `ImageIndex` propiedad. Visual Studio usa esta propiedad para determinar qué mapa de bits para mostrar como icono del nodo de proyecto.

## <a name="test-the-custom-project-node-icon"></a>Probar el icono del nodo de proyecto personalizado
 Pruebe el generador de proyectos para ver si crea una jerarquía de proyecto que tiene el icono del nodo de proyecto personalizado.

### <a name="to-test-the-custom-project-node-icon"></a>Para probar el icono del nodo de proyecto personalizado

1. Inicie la depuración y, en la instancia experimental, cree un nuevo SimpleProject.

2. En el proyecto recién creado, tenga en cuenta que *SimpleProjectNode.bmp* sirve como icono del nodo de proyecto.

     ![Proyecto sencillo nuevo nodo de proyecto](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")

3. Abra *Program.cs* en el editor de código. Debería ver el código fuente que es similar al código siguiente.

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

     Tenga en cuenta que los parámetros de plantilla $nameSpace$ y $className$ no tienen valores nuevos. Obtendrá información sobre cómo implementar la sustitución de parámetros de plantilla en la sección siguiente.

## <a name="substitute-template-parameters"></a>Sustituir los parámetros de plantilla
 En una sección anterior, se registra la plantilla de proyecto con Visual Studio mediante el `ProvideProjectFactory` atributo. Registro de la ruta de acceso de una carpeta de plantillas de esta manera le permite habilitar la sustitución de parámetros de plantilla básica reemplazando y expandir el `ProjectNode.AddFileFromTemplate` clase. Para obtener más información, consulte [nueva generación de proyectos: Internamente, la segunda parte](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Ahora, agregue código de reemplazo para el `AddFileFromTemplate` clase.

### <a name="to-substitute-template-parameters"></a>Sustituir los parámetros de plantilla

1. En el *SimpleProjectNode.cs* , agregue la siguiente `using` instrucción.

   ```csharp
   using System.IO;
   ```

2. Reemplace el `AddFileFromTemplate` método utilizando el código siguiente.

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

3. Establecer un punto de interrupción en el método, justo después de la `className` instrucción de asignación.

   Las instrucciones de asignación determinan valores razonables para un espacio de nombres y un nuevo nombre de clase. Los dos `ProjectNode.FileTemplateProcessor.AddReplace` llamadas al método reemplace los valores de parámetro de plantilla correspondientes mediante el uso de estos nuevos valores.

## <a name="test-the-template-parameter-substitution"></a>Probar la sustitución de parámetros de plantilla
 Ahora puede probar la sustitución de parámetros de plantilla.

### <a name="to-test-the-template-parameter-substitution"></a>Para probar la sustitución de parámetros de plantilla

1. Inicie la depuración y, en la instancia experimental, cree un nuevo SimpleProject.

2. La ejecución se detiene en el punto de interrupción en el `AddFileFromTemplate` método.

3. Examinar los valores para el `nameSpace` y `className` parámetros.

   - `nameSpace` se le asigna el valor de la \<RootNamespace > elemento en el *\Templates\Projects\SimpleProject\SimpleProject.myproj* archivo de plantilla de proyecto. En este caso, el valor es `MyRootNamespace`.

   - `className` se le asigna el valor del nombre de archivo de origen de clase, sin la extensión de nombre de archivo. En este caso, el primer archivo se copien en la carpeta de destino es *AssemblyInfo.cs*; por lo tanto, es el valor de className `AssemblyInfo`.

4. Quitar el punto de interrupción y presione **F5** para continuar la ejecución.

    Visual Studio debe terminar de crear un proyecto.

5. Abra *Program.cs* en el editor de código. Debería ver el código fuente que es similar al código siguiente.

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

    Tenga en cuenta que el espacio de nombres es ahora `MyRootNamespace` y el nombre de clase es ahora `Program`.

6. Empiece a depurar el proyecto. El nuevo proyecto debe compilar, ejecutar y mostrar "Hola VSX!!!" en la ventana de la consola.

    ![Simple Project Command](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   ¡Enhorabuena! Ha implementado un sistema de proyectos administrados básico.