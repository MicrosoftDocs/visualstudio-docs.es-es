---
title: "Crear un sistema básico del proyecto, parte 1 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bf0570dd6f58d6a6893be5babdcde530d3a57109
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2018
---
# <a name="creating-a-basic-project-system-part-1"></a>Crear un sistema básico del proyecto, parte 1
En Visual Studio, los proyectos son los contenedores que los desarrolladores usan para organizar los archivos de código fuente y otros activos. Proyectos aparecen como elementos secundarios de las soluciones en el **el Explorador de soluciones**. Los proyectos permiten organizar, compilar, depurar, implementar el código fuente y crear referencias a servicios Web, bases de datos y otros recursos.  
  
 Los proyectos se definen en archivos de proyecto, por ejemplo, un archivo .csproj para un proyecto de Visual C#. Puede crear su propio tipo de proyecto que tiene su propia extensión de nombre de archivo de proyecto. Para obtener más información acerca de los tipos de proyecto, vea [tipos de proyecto](../extensibility/internals/project-types.md).  
  
> [!NOTE]
>  Si necesita extender Visual Studio con un tipo de proyecto personalizado, se recomienda aprovechar la [sistema de proyectos de Visual Studio](https://github.com/Microsoft/VSProjectSystem) (vsp) que tiene una serie de ventajas con respecto a la creación de un sistema de proyectos desde el principio:  
>   
>  -  Incorporación más fácil.  Incluso en un sistema de proyectos básico requiere decenas de miles de líneas de código.  Aprovechamiento VSPS reduce el costo de incorporación a unos pocos clics antes de que esté listo para personalizarlo según sus necesidades.  
>  -  Mantenimiento más sencillo.  Mediante el aprovechamiento de VSPS, sólo necesitará mantener sus propios escenarios.  Que administramos de la conservación de toda la infraestructura del sistema de proyecto de.  
>   
>  Si necesita destinadas a versiones de Visual Studio anteriores a Visual Studio 2013, no podrá aprovechar VSPS en una extensión de Visual Studio.  Si es así, en este tutorial es un buen lugar para empezar a trabajar.  
  
 En este tutorial se muestra cómo crear un tipo de proyecto que tiene la .myproj de extensión de nombre de archivo de proyecto. En este tutorial toma prestado desde el sistema de proyecto de Visual C# existente.  
  
> [!NOTE]
>  Para obtener más ejemplos de proyectos de extensión, vea [muestras de VSSDK](http://aka.ms/vs2015sdksamples).  
  
 En este tutorial se enseña cómo realizar estas tareas:  
  
-   Crear un tipo básico del proyecto.  
  
-   Crear una plantilla de proyecto básico.  
  
-   Registre la plantilla de proyecto con Visual Studio.  
  
-   Crear una instancia del proyecto, abra el **nuevo proyecto** cuadro de diálogo y, a continuación, usar la plantilla.  
  
-   Crear un generador de proyectos para el sistema de proyectos.  
  
-   Crear un nodo de proyecto para el sistema de proyectos.  
  
-   Agregar iconos personalizados para el sistema del proyecto.  
  
-   Implementar la sustitución de parámetros de plantilla básica.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
 También debe descargar el código fuente de la [Managed Package Framework for Projects](http://mpfproj12.codeplex.com/). Extraiga el archivo en una ubicación que sea accesible a la solución que se va a crear.  
  
## <a name="creating-a-basic-project-type"></a>Crear un tipo de proyecto básico  
 Cree un proyecto de C# VSIX denominado **SimpleProject**. (**Archivo, nuevo, proyecto** y, a continuación, **proyecto VSIX en Visual C#, extensibilidad,**). Agregar una plantilla de elemento de proyecto de paquete de Visual Studio (en el Explorador de soluciones, haga clic en el nodo del proyecto y seleccione **Agregar / nuevo elemento**, a continuación, vaya a **extensibilidad / paquete de Visual Studio**). Asignar nombre al archivo **SimpleProjectPackage**.  
  
## <a name="creating-a-basic-project-template"></a>Crear una plantilla de proyecto básico  
 Ahora, puede modificar este básica de VSPackage para implementar el nuevo tipo de proyecto .myproj. Para crear un proyecto que se basa en el tipo de proyecto .myproj, Visual Studio debe saber qué archivos, recursos y referencias a agregar al nuevo proyecto. Para proporcionar esta información, coloque los archivos de proyecto en una carpeta de plantilla de proyecto. Cuando un usuario usa el proyecto .myproj para crear un proyecto, los archivos se copian en el nuevo proyecto.  
  
#### <a name="to-create-a-basic-project-template"></a>Para crear una plantilla de proyecto básico  
  
1.  Agregue tres carpetas al proyecto, uno en la otra: **Templates\Projects\SimpleProject**. (En **el Explorador de soluciones**, haga clic en el **SimpleProject** nodo de proyecto, seleccione **agregar**y, a continuación, haga clic en **nueva carpeta**. Asigne a la carpeta el nombre `Templates`. En el **plantillas** carpeta, agrega una carpeta denominada `Projects`. En el **proyectos** carpeta, agrega una carpeta denominada `SimpleProject`.)  
  
2.  En el **Templates\Projects\SimpleProject** carpeta, agregar un archivo de imagen de mapa de bits que se usará como el icono denominado `SimpleProject.ico`. Al hacer clic en **agregar**, se abrirá el editor de icono.  
  
3.  Hacer que el icono distintivo. Este icono se mostrará en el **nuevo proyecto** cuadro de diálogo más adelante en el tutorial.  
  
     ![Icono de proyecto simple](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4.  El icono Guardar y cerrar el editor de iconos.  
  
5.  En el **Templates\Projects\SimpleProject** carpeta, agregue un **clase** elemento denominado `Program.cs`.  
  
6.  Reemplace el código existente con las líneas siguientes.  
  
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
    >  Esto no es la forma final del código Program.cs; los parámetros de reemplazo se tratarán en un paso posterior. Es posible que vea errores de compilación, pero siempre que el archivo **BuildAction** es **contenido**, podrá compilar y ejecutar el proyecto como de costumbre.  
  
1.  Guarde el archivo.  
  
2.  Copie el archivo AssemblyInfo.cs de la **propiedades** carpeta a la **Projects\SimpleProject** carpeta.  
  
3.  En el **Projects\SimpleProject** carpeta agregar un archivo XML denominado `SimpleProject.myproj`.  
  
    > [!NOTE]
    >  La extensión de nombre de archivo para todos los proyectos de este tipo es .myproj. Si desea cambiarlo, debe cambiarlo everywhere se menciona en el tutorial.  
  
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
  
6.  En el **propiedades** ventana, establezca el **acción de compilación** de AssemblyInfo.cs, Program.cs, SimpleProject.ico y SimpleProject.myproj a **contenido**y establezca sus  **Incluir en VSIX** propiedades **True**.  
  
 Esta plantilla de proyecto describe un proyecto básico de Visual C# que tiene una configuración de depuración y una configuración de lanzamiento. El proyecto incluye archivos de origen de dos, AssemblyInfo.cs y Program.cs y ensamblado varias referencias. Cuando se crea un proyecto de la plantilla, el valor de ProjectGuid se sustituye automáticamente por un nuevo GUID.  
  
 En **el Explorador de soluciones**, el expandido **plantillas** carpeta debería aparecer como sigue:

```
Templates  
   Projects  
      SimpleProject  
         AssemblyInfo.cs  
         Program.cs  
         SimpleProject.ico  
         SimpleProject.myproj  
```

## <a name="creating-a-basic-project-factory"></a>Crear un generador del proyecto básico  
 Debe indicar a Visual Studio la ubicación de la carpeta de plantilla de proyecto. Para ello, agregue un atributo a la clase de VSPackage que implementa el generador de proyectos para que la ubicación de plantillas se escribe en el registro del sistema cuando se compila el VSPackage. Empiece por crear un generador de básico del proyecto que se identifica mediante un generador GUID de proyecto. Use la <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atributo para conectar el generador de proyectos a la clase SimpleProjectPackage.  
  
#### <a name="to-create-a-basic-project-factory"></a>Para crear un generador de básico del proyecto  
  
1.  Crear GUID para el generador de proyectos (en el **herramientas** menú, haga clic en **crear GUID**), o utilizar uno en el ejemplo siguiente. Agregue los GUID a la clase SimpleProjectPackage cerca de la sección con ya definido `PackageGuidString`. El GUID deben estar en formato GUID y forma de cadena. El código resultante debe parecerse al ejemplo siguiente.  
  
    ```csharp  
        public sealed class SimpleProjectPackage : Package
        {  
            ...
            public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
            public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
    
            public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);  
        }  
    ```  
  
3.  Agregar una clase a la parte superior **SimpleProject** carpeta denominada `SimpleProjectFactory.cs`.  
  
4.  Agregue las siguientes instrucciones using:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  Agregue un atributo de Guid para la clase SimpleProjectFactory. El valor del atributo es el nuevo generador GUID de proyecto.  
  
    ```csharp  
    [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]  
    class SimpleProjectFactory  
    {  
    }  
    ```  
  
 Ahora puede registrar la plantilla de proyecto.  
  
#### <a name="to-register-the-project-template"></a>Para registrar la plantilla de proyecto  
  
1.  En SimpleProjectPackage.cs, agregue un <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atributo a la clase SimpleProjectPackage, como se indica a continuación.  
  
    ```  
    [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
        @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
    [Guid(SimpleProjectPackage.PackageGuidString)]  
    public sealed class SimpleProjectPackage : Package  
    ```  
  
2.  Volver a generar la solución y compruebe que se compila sin errores.  
  
     Volver a generar, registra la plantilla de proyecto.  
  
 Los parámetros `defaultProjectExtension` y `possibleProjectExtensions` se establecen en la extensión de nombre de archivo de proyecto (.myproj). El `projectTemplatesDirectory` parámetro se establece en la ruta de acceso relativa de la carpeta de plantillas. Durante la compilación, se convierte a una compilación completa esta ruta de acceso y se agrega al registro para registrar el sistema del proyecto.  
  
## <a name="testing-the-template-registration"></a>Probar el registro de plantilla  
 Registro de plantilla indica a Visual Studio la ubicación de la carpeta de plantilla de proyecto para que Visual Studio puede mostrar el nombre de la plantilla y el icono en el **nuevo proyecto** cuadro de diálogo.  
  
#### <a name="to-test-the-template-registration"></a>Para probar el registro de plantilla  
  
1.  Presione F5 para iniciar la depuración de una instancia experimental de Visual Studio.  
  
2.  En la instancia experimental, cree un nuevo proyecto de su tipo de proyecto recién creado. En el **nuevo proyecto** cuadro de diálogo, debería ver **SimpleProject** en **plantillas instaladas**.  
  
 Ahora tiene un generador del proyecto que se ha registrado. Sin embargo, aún no puede crear un proyecto. El paquete del proyecto y el generador de proyecto funcionan conjuntamente para crear e inicializar un proyecto.  
  
## <a name="add-the-managed-package-framework-code"></a>Agregue el código de Managed Package Framework  
 Implementar la conexión entre el paquete del proyecto y el generador de proyectos.  
  
-   Importe los archivos de código fuente de Managed Package Framework.  
  
    1.  Descargue el proyecto SimpleProject (en **el Explorador de soluciones**, seleccione el nodo del proyecto y en el menú contextual, haga clic en **descargar el proyecto**.) y abra el archivo de proyecto en el editor XML.  
  
    2.  Agregue los siguientes bloques en el archivo de proyecto (justo encima del \<importación > bloques). Establezca ProjectBasePath en la ubicación del archivo ProjectBase.files en el código de Managed Package Framework que acaba de descargar. Es posible que deba agregar una barra diagonal inversa a la ruta de acceso. Si no lo hace, se puede producir un error en el proyecto se encuentra el código de Managed Package Framework.  
  
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
  
        -   Microsoft.VisualStudio.Designer.Interfaces (en \<instalación VSSDK > \VisualStudioIntegration\Common\Assemblies\v2.0)  
  
        -   WindowsBase  
  
        -   Microsoft.Build.Tasks.v4.0  
  
#### <a name="to-initialize-the-project-factory"></a>Para inicializar el generador de proyectos  
  
1.  En el archivo SimpleProjectPackage.cs, agregue las siguientes `using` instrucción.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  Derivar la `SimpleProjectPackage` clase `Microsoft.VisualStudio.Package.ProjectPackage`.  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  Registrar el generador de proyectos. Agregue la línea siguiente a la `SimpleProjectPackage.Initialize` método, justo después `base.Initialize`.  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4.  Implementa la propiedad abstracta `ProductUserContext`:  
  
    ```csharp  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5.  En SimpleProjectFactory.cs, agregue las siguientes `using` instrucción después existente `using` instrucciones.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  Derivar la `SimpleProjectFactory` clase `ProjectFactory`.  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  Agregue el siguiente método ficticio para el `SimpleProjectFactory` clase. Este método se implementará en una sección posterior.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  Agregue el siguiente campo y constructor para el `SimpleProjectFactory` clase. Esto `SimpleProjectPackage` referencia se almacena en caché en un campo privado para que se puede utilizar en la configuración de un sitio de proveedor de servicio.  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Volver a generar la solución y compruebe que se compila sin errores.  
  
## <a name="testing-the-project-factory-implementation"></a>Probar la implementación del generador de proyecto  
 Comprobar si se llama al constructor de la implementación del generador de proyectos.  
  
#### <a name="to-test-the-project-factory-implementation"></a>Para probar la implementación del generador de proyecto  
  
1.  En el archivo SimpleProjectFactory.cs, establezca un punto de interrupción en la línea siguiente en el `SimpleProjectFactory` constructor.  
  
    ```  
    this.package = package;  
    ```  
  
2.  Presione F5 para iniciar una instancia experimental de Visual Studio.  
  
3.  En la instancia experimental, comience a crear un nuevo proyecto. En el **nuevo proyecto** cuadro de diálogo, seleccione la SimpleProject tipo de proyecto y, a continuación, haga clic en **Aceptar**. La ejecución se detiene en el punto de interrupción.  
  
4.  Desactive el punto de interrupción y detener la depuración. Puesto que aún no hemos creado un nodo de proyecto, el código de creación del proyecto todavía produce excepciones.  
  
## <a name="extending-the-project-node-class"></a>Extender la clase de nodo de proyecto  
 Ahora puede implementar la `SimpleProjectNode` (clase), que se deriva de la `ProjectNode` clase. La `ProjectNode` clase base controla las siguientes tareas de creación del proyecto:  
  
-   Copia el archivo de plantilla de proyecto, SimpleProject.myproj, en la nueva carpeta de proyecto. Se cambia el nombre de la copia de acuerdo con el nombre especificado en el **nuevo proyecto** cuadro de diálogo. La `ProjectGuid` valor de propiedad se sustituye por un nuevo GUID.  
  
-   Recorre los elementos de MSBuild del archivo de plantilla del proyecto, SimpleProject.myproj y busca `Compile` elementos. Para cada `Compile` archivo de destino, copia el archivo a la nueva carpeta de proyecto.  
  
 La clase derivada `SimpleProjectNode` clase administra estas tareas:  
  
-   Habilita los iconos para los nodos de proyecto y el archivo en **el Explorador de soluciones** que deben crearse o seleccionado.  
  
-   Permite sustituciones de parámetros de plantilla de proyecto adicionales que se especifique.  
  
#### <a name="to-extend-the-project-node-class"></a>Para extender la clase de nodo de proyecto  
  
1.  
  
2.  Agregue una clase denominada `SimpleProjectNode.cs`.  
  
3.  Reemplace el código existente por el siguiente código.  
  
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
  
-   `ProjectGuid`, que devuelve el GUID del generador de proyectos.  
  
-   `ProjectType`, que devuelve el nombre localizado del tipo de proyecto.  
  
-   `AddFileFromTemplate`, que copia archivos seleccionados de la carpeta de plantillas para el proyecto de destino. Además, este método se implementa en una sección posterior.  
  
 El `SimpleProjectNode` constructor, como el `SimpleProjectFactory` almacena en memoria caché en el constructor, un `SimpleProjectPackage` referencia en un campo privado para su uso posterior.  
  
 Para conectar el `SimpleProjectFactory` clase a la `SimpleProjectNode` (clase), debe crear instancias de un nuevo `SimpleProjectNode` en el `SimpleProjectFactory.CreateProject` método y almacenarla en la caché en un campo privado para su uso posterior.  
  
#### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Para conectarse a la clase de generador de proyecto y la clase de nodo  
  
1.  En el archivo SimpleProjectFactory.cs, agregue las siguientes `using` instrucción:  
  
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
  
3.  Volver a generar la solución y compruebe que se compila sin errores.  
  
## <a name="testing-the-project-node-class"></a>Probar la clase de nodo de proyecto  
 Probar el generador de proyectos para ver si crea una jerarquía de proyectos.  
  
#### <a name="to-test-the-project-node-class"></a>Para probar la clase de nodo de proyecto  
  
1.  Presione F5 para iniciar la depuración. En la instancia experimental, cree un nuevo SimpleProject.  
  
2.  Visual Studio debe llamar a la fábrica de proyecto para crear un proyecto.  
  
3.  Cierre la instancia experimental de Visual Studio.  
  
## <a name="adding-a-custom-project-node-icon"></a>Agregar un icono de nodo de proyecto personalizadas  
 El icono de nodo de proyecto en la sección anterior es un icono predeterminado. Se puede cambiar a un icono personalizado.  
  
#### <a name="to-add-a-custom-project-node-icon"></a>Para agregar un icono de nodo de proyecto personalizadas  
  
1.  En el **recursos** carpeta, agregue un archivo de mapa de bits denominado SimpleProjectNode.bmp.  
  
2.  En el **propiedades** windows, reducir el mapa de bits a 16 por 16 píxeles. Hacer que el mapa de bits distintos.  
  
     ![Comando de proyecto simple](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3.  En el **propiedades** ventana, cambiar la **acción de compilación** del mapa de bits a **recurso incrustado**.  
  
4.  En SimpleProjectNode.cs, agregue las siguientes `using` instrucciones:  
  
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
  
7.  Reemplace el constructor de instancia con el código siguiente.  
  
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
  
 Durante la construcción estática, `SimpleProjectNode` recupera el mapa de bits de nodo de proyecto de los recursos de manifiesto de ensamblado y lo almacena en caché en un campo privado para su uso posterior. Observe la sintaxis de la <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> ruta de acceso de imagen. Para ver los nombres de los recursos de manifiesto incrustados en un ensamblado, utilice la <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> método. Cuando este método se aplica a la `SimpleProject` ensamblado, los resultados deben ser como sigue:  
  
-   SimpleProject.Resources.resources  
  
-   VisualStudio.Project.resources  
  
-   SimpleProject.VSPackage.resources  
  
-   Resources.imagelis.bmp  
  
-   Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
-   Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
-   SimpleProject.Resources.SimpleProjectNode.bmp  
  
 Durante la construcción de la instancia, el `ProjectNode` Resources.imagelis.bmp, en el que son utilizadas 16 x 16 mapas de bits incrustados de Resources\imagelis.bmp de carga de clase base. Esta lista de mapa de bits debe ponerse a disposición a `SimpleProjectNode` como ImageHandler.ImageList. `SimpleProjectNode` Anexa el mapa de bits de nodo de proyecto a la lista. El desplazamiento del mapa de bits de nodo de proyecto en la lista de imágenes se almacenan en caché para su uso posterior como el valor del público `ImageIndex` propiedad. Visual Studio usa esta propiedad para determinar qué mapa de bits para mostrar como el icono de nodo de proyecto.  
  
## <a name="testing-the-custom-project-node-icon"></a>Probar el icono de nodo de proyecto personalizadas  
 Probar el generador de proyectos para ver si crea una jerarquía de proyecto que tiene el icono de nodo de proyecto personalizado.  
  
#### <a name="to-test-the-custom-project-node-icon"></a>Para probar el icono de nodo de proyecto personalizadas  
  
1.  Iniciar la depuración y en la instancia experimental, cree un nuevo SimpleProject.  
  
2.  En el proyecto recién creado, tenga en cuenta que SimpleProjectNode.bmp se utiliza como el icono de nodo de proyecto.  
  
     ![Nodo de proyecto simple nuevo proyecto](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
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
  
     Tenga en cuenta que los parámetros de plantilla $nameSpace$ y $className$ no tiene nuevos valores. Obtendrá información sobre cómo implementar la sustitución de parámetros de plantilla en la sección siguiente.  
  
## <a name="substituting-template-parameters"></a>Sustitución de parámetros de plantilla  
 En una sección anterior, se registra la plantilla de proyecto con Visual Studio mediante el `ProvideProjectFactory` atributo. Registrar la ruta de acceso de una carpeta de plantilla de esta manera permite habilitar la sustitución de parámetros de plantilla básica reemplazando y expandir el `ProjectNode.AddFileFromTemplate` clase. Para obtener más información, consulte [nueva generación de proyecto: Under the Hood, parte dos](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Ahora agregue el código de reemplazo para el `AddFileFromTemplate` clase.  
  
#### <a name="to-substitute-template-parameters"></a>Para sustituir los parámetros de plantilla  
  
1.  En el archivo SimpleProjectNode.cs, agregue las siguientes `using` instrucción.  
  
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
  
3.  Establecer un punto de interrupción en el método, justo después de la `className` instrucción de asignación.  
  
 Las instrucciones de asignación determinan valores razonables para un espacio de nombres y un nuevo nombre de clase. Los dos `ProjectNode.FileTemplateProcessor.AddReplace` llamadas al método reemplace los valores de parámetro de plantilla correspondientes con estos nuevos valores.  
  
## <a name="testing-the-template-parameter-substitution"></a>Probar la sustitución de parámetros de plantilla  
 Ahora puede probar la sustitución de parámetros de plantilla.  
  
#### <a name="to-test-the-template-parameter-substitution"></a>Para probar la sustitución de parámetros de plantilla  
  
1.  Iniciar la depuración y en la instancia experimental, cree un nuevo SimpleProject.  
  
2.  La ejecución se detiene en el punto de interrupción en el `AddFileFromTemplate` método.  
  
3.  Examinar los valores para la `nameSpace` y `className` parámetros.  
  
    -   `nameSpace` se le asigna el valor de la \<RootNamespace > elemento en el archivo de plantilla de proyecto \Templates\Projects\SimpleProject\SimpleProject.myproj. En este caso, el valor es "MyRootNamespace".  
  
    -   `className` recibe el valor del nombre de archivo de origen de clase, sin la extensión de nombre de archivo. En este caso, el primer archivo se copien en la carpeta de destino es AssemblyInfo.cs; por lo tanto, el valor de className es "AssemblyInfo".  
  
4.  Quite el punto de interrupción y presione F5 para continuar la ejecución.  
  
     Visual Studio debe terminar de crear un proyecto.  
  
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
  
     Tenga en cuenta que el espacio de nombres es ahora "MyRootNamespace" y el nombre de clase es ahora "Program".  
  
6.  Empiece a depurar el proyecto. El nuevo proyecto debe compilar, ejecutar y mostrar "Hello VSX." en la ventana de la consola.  
  
     ![Comando de proyecto simple](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
 ¡Enhorabuena! Ha implementado un sistema administrado básico del proyecto.