---
title: "Crear un sistema de proyectos b&#225;sico, parte 1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "escribir un sistema de proyectos"
  - "sistema de proyectos"
  - "tutorial"
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 47
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 47
---
# Crear un sistema de proyectos b&#225;sico, parte 1
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En Visual Studio, los proyectos son los contenedores que los desarrolladores usan para organizar los archivos de código fuente y otros activos. Proyectos aparecen como elementos secundarios de soluciones en el **el Explorador de soluciones**. Los proyectos permiten organizar, compilar, depurar, implementar el código fuente y crear referencias a servicios Web, bases de datos y otros recursos.  
  
 Los proyectos se definen en archivos de proyecto, por ejemplo, un archivo .csproj para un proyecto de Visual C\#. Puede crear su propio tipo de proyecto que tiene su propia extensión de nombre de archivo de proyecto. Para obtener más información acerca de los tipos de proyecto, vea [Tipos de proyecto](../extensibility/internals/project-types.md).  
  
> [!NOTE]
>  Si necesita ampliar Visual Studio con un tipo de proyecto personalizado, se recomienda aprovechar la [sistema de proyectos de Visual Studio](https://github.com/Microsoft/VSProjectSystem) que tiene una serie de ventajas sobre la creación de un sistema de proyecto desde cero:  
>   
>  -   Incorporación de más fácil.  Incluso en un sistema de proyectos básico requiere decenas de miles de líneas de código.  Aprovechamiento de CPS reduce el costo de incorporación a unos pocos clics antes de personalizarla para sus necesidades.  
> -   Facilitar el mantenimiento.  Mediante el aprovechamiento de CPS, sólo necesitará mantener sus propios escenarios.  Administramos el mantenimiento de toda la infraestructura del sistema de proyecto de.  
>   
>  Si necesita destinadas a versiones de Visual Studio anteriores a Visual Studio 2013, no podrá aprovechar CPS en una extensión de Visual Studio.  Si ese es el caso, este tutorial es un buen lugar para empezar a trabajar.  
  
 Este tutorial muestra cómo crear un tipo de proyecto que tiene la .myproj de extensión de nombre de archivo de proyecto. En este tutorial se toma prestado del sistema de proyecto de Visual C\# existente.  
  
> [!NOTE]
>  Para obtener un ejemplo de extremo a extremo de un sistema de proyectos de lenguaje completo, vea el ejemplo de IronPython Deep Dive en [Muestras de VSSDK](../misc/vssdk-samples.md).  
  
 Este tutorial enseña cómo realizar estas tareas:  
  
-   Crear un tipo de proyecto básico.  
  
-   Crear una plantilla de proyecto básico.  
  
-   Registre la plantilla de proyecto con Visual Studio.  
  
-   Crear una instancia de proyecto, abra el **nuevo proyecto** cuadro de diálogo y, a continuación, utilice la plantilla.  
  
-   Crear un generador de proyecto para el sistema del proyecto.  
  
-   Crear un nodo de proyecto para el sistema de proyectos.  
  
-   Agregar iconos personalizados para el sistema del proyecto.  
  
-   Implementar la sustitución de parámetros de plantilla básica.  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
 También debe descargar el código fuente para la [Managed Package Framework para proyectos](http://mpfproj12.codeplex.com/). Extraiga el archivo en una ubicación que sea accesible a la solución que se va a crear.  
  
## Creación de un tipo de proyecto básico  
 Cree un proyecto de VSIX de C\# llamado **SimpleProject**. \(**Archivo, nuevo, proyecto** y, a continuación, **el paquete de Visual Studio C\#, extensibilidad,**\). Agregar una plantilla de elemento de proyecto de paquete de Visual Studio \(en el Explorador de soluciones, haga clic en el nodo del proyecto y seleccione **Agregar \/ nuevo elemento**, a continuación, vaya a **extensibilidad \/ paquete de Visual Studio**\). Nombre de archivo **SimpleProjectPackage**.  
  
## Creación de una plantilla de proyecto básico  
 Ahora, puede modificar este básica de VSPackage para implementar el nuevo tipo de proyecto .myproj. Para crear un proyecto que se basa en el tipo de proyecto .myproj, Visual Studio debe saber qué archivos, recursos y referencias para agregar al nuevo proyecto. Para proporcionar esta información, coloque los archivos de proyecto en una carpeta de plantilla de proyecto. Cuando un usuario usa el proyecto .myproj para crear un proyecto, los archivos se copian en el nuevo proyecto.  
  
#### Para crear una plantilla de proyecto básico  
  
1.  Agregue tres carpetas al proyecto, uno en el otro: **Templates\\Projects\\SimpleProject**. \(En **el Explorador de soluciones**, haga clic en el **SimpleProject** nodo de proyecto, seleccione **Agregar**, y, a continuación, haga clic en **nueva carpeta**. Nombre de la carpeta `Templates`. En el **plantillas** carpeta, agregue una carpeta denominada `Projects`. En el **proyectos** carpeta, agregue una carpeta denominada `SimpleProject`.\)  
  
2.  En el **Projects\\SimpleProject** carpeta agregar un archivo de icono llamado `SimpleProject.ico`. Al hacer clic en **Agregar**, se abre el editor de iconos.  
  
3.  Hacer que el icono distintivo. Este icono aparecerá en el **nuevo proyecto** cuadro de diálogo más adelante en el tutorial.  
  
     ![Icono de proyecto simple](~/docs/extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4.  El icono Guardar y cerrar el editor de iconos.  
  
5.  En el **Projects\\SimpleProject** carpeta, agregue un **clase** elemento denominado `Program.cs`.  
  
6.  Reemplace el código existente con las líneas siguientes.  
  
    ```c#  
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
    >  Esto no es la forma final del código Program.cs. los parámetros de reemplazo se tratará en un paso posterior. Es posible que vea errores de compilación, pero siempre que el archivo **BuildAction** es **contenido**, podrá compilar y ejecutar el proyecto como de costumbre.  
  
1.  Guarde el archivo.  
  
2.  Copie el archivo AssemblyInfo.cs de la **propiedades** carpeta a la **Projects\\SimpleProject** carpeta.  
  
3.  En el **Projects\\SimpleProject** carpeta agregar un archivo XML denominado `SimpleProject.myproj`.  
  
    > [!NOTE]
    >  La extensión de nombre de archivo para todos los proyectos de este tipo es .myproj. Si desea cambiarla, debe cambiarlo en todas partes mencionado en el tutorial.  
  
4.  Reemplace el contenido existente con las líneas siguientes.  
  
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
  
5.  Guarde el archivo.  
  
6.  En el **propiedades** ventana, establezca el **acción de compilación** de AssemblyInfo.cs, Program.cs, SimpleProject.ico y SimpleProject.myproj a **contenido**, y establezca sus **incluir en VSIX** propiedades **True**.  
  
 Esta plantilla de proyecto describe un proyecto básico en Visual C\# que tiene una configuración de depuración y una configuración de lanzamiento. El proyecto incluye archivos de origen de dos, AssemblyInfo.cs y Program.cs y ensamblado de varias referencias. Cuando se crea un proyecto de la plantilla, el valor de ProjectGuid se reemplaza automáticamente por un nuevo GUID.  
  
 En **el Explorador de soluciones**, el texto expandido **plantillas** carpeta debería aparecer como sigue:  
  
 Plantillas  
  
 Proyectos  
  
 SimpleProject  
  
 AssemblyInfo.cs  
  
 Program.cs  
  
 SimpleProject.ico  
  
 SimpleProject.myproj  
  
## Crear un generador del proyecto básico  
 Debe indicar la ubicación de la carpeta de la plantilla de proyecto a Visual Studio. Para ello, agregue un atributo a la clase de VSPackage que implementa el generador del proyecto para que la ubicación de la plantilla se escribe en el registro del sistema cuando se compila el VSPackage. Empiece por crear un generador de proyecto básico que se identifica mediante un generador GUID de proyecto. Utilice la <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atributo para conectar el generador del proyecto a la clase SimpleProjectPackage.  
  
#### Para crear un generador del proyecto básico  
  
1.  Abra SimpleProjectPackageGuids.cs en el editor de código.  
  
2.  Crear GUID para el generador del proyecto \(en el **herramientas** menú, haga clic en **Crear GUID**\), o utilizar uno en el ejemplo siguiente. Agregue los GUID para la clase SimpleProjectPackageGuids. Los GUID deben estar en forma de GUID y en forma de cadena. El código resultante debe parecerse al ejemplo siguiente.  
  
    ```  
    static class SimpleProjectPackageGuids  
    {  
        public const string guidSimpleProjectPkgString =   
            "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
        public const string guidSimpleProjectCmdSetString =   
            "72c23e1d-f389-410a-b5f1-c938303f1391";  
        public const string guidSimpleProjectFactoryString =   
            "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
  
        public static readonly Guid guidSimpleProjectCmdSet =   
            new Guid(guidSimpleProjectCmdSetString);  
        public static readonly Guid guidSimpleProjectFactory =   
            new Guid(guidSimpleProjectFactoryString);  
    }  
    ```  
  
3.  Agregar una clase a la parte superior **SimpleProject** carpeta denominada `SimpleProjectFactory.cs`.  
  
4.  Agregue las siguientes instrucciones using:  
  
    ```  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  Agregue un atributo de Guid para la clase SimpleProjectFactory. El valor del atributo es el nuevo generador GUID de proyecto.  
  
    ```  
    [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
    class SimpleProjectFactory  
    {  
    }  
    ```  
  
 Ahora puede registrar la plantilla de proyecto.  
  
#### Para registrar la plantilla de proyecto  
  
1.  En SimpleProjectPackage.cs, agregue un <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> de atributo a la clase SimpleProjectPackage, como se indica a continuación.  
  
    ```  
    [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
        @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
    [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
    public sealed class SimpleProjectPackage : Package  
    ```  
  
2.  Recompile la solución y compruebe que se compila sin errores.  
  
     Volver a generar, registra la plantilla de proyecto.  
  
 Los parámetros `defaultProjectExtension` y `possibleProjectExtensions` se establecen en la extensión de nombre de archivo de proyecto \(.myproj\). El `projectTemplatesDirectory` parámetro se establece en la ruta de acceso relativa de la carpeta de plantillas. Durante la compilación, se convierte en una compilación completa y agregarán al registro para registrar el sistema de proyectos esta ruta de acceso.  
  
## Probar el registro de plantilla  
 Registro de plantilla indica a Visual Studio la ubicación de la carpeta de la plantilla de proyecto para que Visual Studio puede mostrar el nombre de la plantilla y el icono en el **nuevo proyecto** cuadro de diálogo.  
  
#### Para probar el registro de plantilla  
  
1.  Presione F5 para iniciar la depuración de una instancia experimental de Visual Studio.  
  
2.  En la instancia experimental, cree un nuevo proyecto de su tipo de proyecto recién creado. En el **nuevo proyecto** cuadro de diálogo, verá **SimpleProject** en **Plantillas instaladas**.  
  
 Ahora dispone de un generador del proyecto que está registrado. Sin embargo, aún no puede crear un proyecto. El paquete del proyecto y el generador de proyecto colaboran para crear e inicializar un proyecto.  
  
## Agregue el código de Managed Package Framework  
 Implementar la conexión entre el paquete del proyecto y el generador del proyecto.  
  
-   Importe los archivos de código fuente para Managed Package Framework.  
  
    1.  Descargar el proyecto SimpleProject \(en **el Explorador de soluciones**, seleccione el nodo del proyecto y en el menú contextual, haga clic en **descargar el proyecto**.\) y abra el archivo de proyecto en el editor XML.  
  
    2.  Agregue los siguientes bloques en el archivo de proyecto \(justo encima de los bloques \< Import \>\). Establezca ProjectBasePath en la ubicación del archivo ProjectBase.files en el código de Managed Package Framework que acaba de descargar. Es posible que deba agregar una barra diagonal inversa a la ruta de acceso. Si no lo hace, es posible que no encuentre el código Managed Package Framework el proyecto.  
  
        ```  
        <PropertyGroup>  
             <ProjectBasePath>your path here\</ProjectBasePath>  
             <RegisterWithCodebase>true</RegisterWithCodebase>  
          </PropertyGroup>  
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />  
        ```  
  
        > [!IMPORTANT]
        >  No olvide la barra diagonal inversa al final de la ruta de acceso.  
  
    3.  Vuelva a cargar el proyecto.  
  
    4.  Agregue referencias a los siguientes ensamblados:  
  
        -   Microsoft.VisualStudio.Designer.Interfaces \(en \< instalación VSSDK \> \\VisualStudioIntegration\\Common\\Assemblies\\v2.0\)  
  
        -   WindowsBase  
  
        -   Microsoft.Build.Tasks.v4.0  
  
#### Para inicializar el generador de proyecto  
  
1.  En el archivo SimpleProjectPackage.cs, agregue la siguiente `using` instrucción.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  Derivar la `SimpleProjectPackage` desde `Microsoft.VisualStudio.Package.ProjectPackage`.  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  Registrar el generador del proyecto. Agregue la siguiente línea a la `SimpleProjectPackage.Initialize` método, justo después `base.Initialize`.  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4.  Implementar la propiedad abstracta `ProductUserContext`:  
  
    ```c#  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5.  En SimpleProjectFactory.cs, agregue la siguiente `using` instrucción después del `using` instrucciones.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  Derivar la `SimpleProjectFactory` desde `ProjectFactory`.  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  Agregue el siguiente método ficticio para el `SimpleProjectFactory` clase. Este método se implementa en una sección posterior.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  Agregue el siguiente campo y el constructor para la `SimpleProjectFactory` clase. Esto `SimpleProjectPackage` referencia se almacena en caché en un campo privado para que se puede utilizar en la configuración de un sitio de proveedor de servicio.  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Recompile la solución y compruebe que se compila sin errores.  
  
## Probar la implementación de fábrica del proyecto  
 Si se llama al constructor para la implementación de fábrica del proyecto de prueba.  
  
#### Para probar la implementación del generador de proyecto  
  
1.  En el archivo SimpleProjectFactory.cs, establezca un punto de interrupción en la línea siguiente en el `SimpleProjectFactory` constructor.  
  
    ```  
    this.package = package;  
    ```  
  
2.  Presione F5 para iniciar una instancia experimental de Visual Studio.  
  
3.  En la instancia experimental, comience a crear un nuevo proyecto. En el **nuevo proyecto** cuadro de diálogo, seleccione el SimpleProject tipo de proyecto y, a continuación, haga clic en **Aceptar**. La ejecución se detiene en el punto de interrupción.  
  
4.  Desactive el punto de interrupción y detener la depuración. Puesto que aún no hemos creado un nodo de proyecto, el código de creación de proyecto aún produce excepciones.  
  
## Extender la clase de nodo de proyecto  
 Ahora puede implementar la `SimpleProjectNode` \(clase\), que se deriva de la `ProjectNode` clase. La `ProjectNode` clase base controla las siguientes tareas de crear el proyecto:  
  
-   Copia el archivo de plantilla de proyecto, SimpleProject.myproj, a la nueva carpeta de proyecto. Se cambia el nombre de la copia según el nombre especificado en el **nuevo proyecto** cuadro de diálogo. El `ProjectGuid` el valor de propiedad se sustituye por un nuevo GUID.  
  
-   Recorre los elementos de MSBuild del archivo de plantilla del proyecto, SimpleProject.myproj y busca `Compile` elementos. Para cada `Compile` el archivo de destino, copia el archivo a la nueva carpeta de proyecto.  
  
 La derivada `SimpleProjectNode` clase controla estas tareas:  
  
-   Habilita los iconos de los nodos proyecto y archivo **el Explorador de soluciones** para crear o seleccionar.  
  
-   Permite las sustituciones de parámetros de plantilla de proyecto adicionales que se especifique.  
  
#### Para extender la clase de nodo de proyecto  
  
1.  
  
2.  Agregue una clase denominada `SimpleProjectNode.cs`.  
  
3.  Reemplace el código existente por el código siguiente.  
  
    ```  
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
                get { return SimpleProjectGuids.guidSimpleProjectFactory; }  
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
  
-   `ProjectGuid`, que devuelve el Generador GUID del proyecto.  
  
-   `ProjectType`, que devuelve el nombre localizado del tipo de proyecto.  
  
-   `AddFileFromTemplate`, que copia archivos seleccionados desde la carpeta de plantillas en el proyecto de destino. Además, este método se implementa en una sección posterior.  
  
 El `SimpleProjectNode` constructor, como el `SimpleProjectFactory` constructor, almacena en caché una `SimpleProjectPackage` referencia en un campo privado para su uso posterior.  
  
 Para conectar el `SimpleProjectFactory` clase a la `SimpleProjectNode` \(clase\), debe crear instancias de un nuevo `SimpleProjectNode` en la `SimpleProjectFactory.CreateProject` \(método\) y almacenarlo en caché en un campo privado para su uso posterior.  
  
#### Para conectarse a la clase de generador del proyecto y la clase de nodo  
  
1.  En el archivo SimpleProjectFactory.cs, agregue la siguiente `using` instrucción:  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2.  Reemplace el `SimpleProjectFactory.CreateProject` método utilizando el código siguiente.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3.  Recompile la solución y compruebe que se compila sin errores.  
  
## Probar la clase de nodo de proyecto  
 La fábrica de proyecto para ver si crea una jerarquía de proyectos de prueba.  
  
#### Para probar la clase de nodo de proyecto  
  
1.  Presione F5 para iniciar la depuración. En la instancia experimental, cree un nuevo SimpleProject.  
  
2.  Visual Studio debe llamar a la fábrica de proyecto para crear un proyecto.  
  
3.  Cierre la instancia experimental de Visual Studio.  
  
## Agregar un icono de nodo de proyecto personalizadas  
 El icono de nodo de proyecto en la sección anterior es un icono predeterminado. Puede cambiarlo a un icono personalizado.  
  
#### Para agregar un icono de nodo de proyecto personalizadas  
  
1.  En el **recursos** carpeta, agregue un archivo de mapa de bits llamado SimpleProjectNode.bmp.  
  
2.  En el **propiedades** windows, reducir el mapa de bits de 16 por 16 píxeles. Hacer que el mapa de bits distintivo.  
  
     ![Comando de proyecto simple](~/docs/extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3.  En el **propiedades** ventana, cambiar la **acción de compilación** del mapa de bits para **recurso incrustado**.  
  
4.  En SimpleProjectNode.cs, agregue la siguiente `using` instrucciones:  
  
    ```  
    using System.Drawing;  
    using System.Windows.Forms;  
    ```  
  
5.  Agregue el siguiente campo estático y el constructor para la `SimpleProjectNode` clase.  
  
    ```  
    private static ImageList imageList;  
  
    static SimpleProjectNode()  
    {  
        imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
    }  
    ```  
  
6.  Agregue la siguiente propiedad al principio de la `SimpleProjectNode` clase.  
  
    ```  
    internal static int imageIndex;  
       public override int ImageIndex  
       {  
           get { return imageIndex; }  
       }  
    ```  
  
7.  Reemplace el constructor de instancia con el siguiente código.  
  
    ```  
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
  
 Durante la construcción estático, `SimpleProjectNode` recupera el mapa de bits de nodo de proyecto de los recursos de manifiesto de ensamblado y lo guarda en un campo privado para su uso posterior. Observe la sintaxis de la <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> ruta de acceso de imagen. Para ver los nombres de los recursos de manifiesto incrustados en un ensamblado, utilice la <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> método. Cuando este método se aplica a la `SimpleProject` ensamblado, los resultados deben ser como sigue:  
  
-   SimpleProject.Resources.resources  
  
-   VisualStudio.Project.resources  
  
-   SimpleProject.VSPackage.resources  
  
-   Resources.imagelis.bmp  
  
-   Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
-   Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
-   SimpleProject.Resources.SimpleProjectNode.bmp  
  
 Durante la construcción de la instancia, el `ProjectNode` Resources.imagelis.bmp, en el que son utilizadas 16 x 16 mapas de bits incrustados de Resources\\imagelis.bmp de carga de clase base. Esta lista de mapa de bits se hace disponible para `SimpleProjectNode` como ImageHandler.ImageList.`SimpleProjectNode` Anexa el mapa de bits de nodo de proyecto a la lista. El desplazamiento del mapa de bits de nodo de proyecto en la lista de imágenes se almacenan en caché para su uso posterior como el valor del público `ImageIndex` propiedad. Visual Studio utiliza esta propiedad para determinar qué mapa de bits para que aparezca como el icono de nodo de proyecto.  
  
## Probar el icono de nodo de proyecto personalizadas  
 Probar el generador de proyecto para ver si crea una jerarquía de proyecto que tiene el icono de nodo de proyecto personalizadas.  
  
#### Para probar el icono de nodo de proyecto personalizadas  
  
1.  Inicie la depuración y en la instancia experimental, cree un nuevo SimpleProject.  
  
2.  En el proyecto recién creado, observe que SimpleProjectNode.bmp se utiliza como el icono de nodo de proyecto.  
  
     ![Nodo Nuevo proyecto Proyecto simple](~/docs/extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3.  Abra Program.cs en el editor de código. Debería ver el código fuente que es similar al código siguiente.  
  
    ```  
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
  
## Sustitución de parámetros de plantilla  
 En una sección anterior, registrar la plantilla de proyecto con Visual Studio mediante el `ProvideProjectFactory` atributo. Registrar la ruta de acceso de una carpeta de plantilla de esta manera permite habilitar la substitución de parámetros de plantilla básica reemplazando y expandir el `ProjectNode.AddFileFromTemplate` clase. Para obtener más información, consulta [Nueva generación de proyecto: Bajo el capó, segunda parte](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Ahora agregue el código de reemplazo para el `AddFileFromTemplate` clase.  
  
#### Sustituir los parámetros de plantilla  
  
1.  En el archivo SimpleProjectNode.cs, agregue la siguiente `using` instrucción.  
  
    ```  
    using System.IO;  
    ```  
  
2.  Reemplace el `AddFileFromTemplate` método utilizando el código siguiente.  
  
    ```  
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
  
3.  Establece un punto de interrupción en el método, justo después de la `className` instrucción de asignación.  
  
 Las instrucciones de asignación determinan valores razonables para un espacio de nombres y un nuevo nombre de clase. Los dos `ProjectNode.FileTemplateProcessor.AddReplace` llamadas al método reemplazar los valores de parámetro de plantilla correspondiente mediante estos nuevos valores.  
  
## Probar la sustitución de parámetros de plantilla  
 Ahora puede probar la sustitución de parámetros de plantilla.  
  
#### Para probar la sustitución de parámetros de plantilla  
  
1.  Inicie la depuración y en la instancia experimental, cree un nuevo SimpleProject.  
  
2.  La ejecución se detiene en el punto de interrupción en la `AddFileFromTemplate` \(método\).  
  
3.  Examinar los valores para el `nameSpace` y `className` parámetros.  
  
    -   `nameSpace` se asigna el valor del elemento \< RootNamespace \> en el archivo de plantilla de proyecto \\Templates\\Projects\\SimpleProject\\SimpleProject.myproj. En este caso, el valor es "MyRootNamespace".  
  
    -   `className` se asigna el valor del nombre de archivo de código fuente de clase, sin la extensión de nombre de archivo. En este caso, el primer archivo copiarse a la carpeta de destino es AssemblyInfo.cs; por lo tanto, el valor de nombre de clase es "AssemblyInfo".  
  
4.  Quite el punto de interrupción y presione F5 para continuar la ejecución.  
  
     Debe finalizar la creación de un proyecto de Visual Studio.  
  
5.  Abra Program.cs en el editor de código. Debería ver el código fuente que es similar al código siguiente.  
  
    ```  
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
  
     Observe que el espacio de nombres es ahora "MyRootNamespace" y el nombre de clase es ahora "Program".  
  
6.  Empezar a depurar el proyecto. El nuevo proyecto debe compilar, ejecutar y mostrar "Hello VSX\!\!\!" en la ventana de consola.  
  
     ![Comando de proyecto simple](~/docs/extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
 ¡Enhorabuena\! Ha implementado un sistema de proyecto administrado básico.