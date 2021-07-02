---
title: 'Tutorial: Creación de un SDK mediante C++ | Microsoft Docs'
description: Obtenga información sobre cómo crear un SDK nativo de biblioteca matemática de C++, empaquetar el SDK como una extensión Visual Studio y, a continuación, usarlo para crear una aplicación mediante este tutorial.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a52322e575dc201a6bf1648af93d813828e0b17
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2021
ms.locfileid: "113223012"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Tutorial: Creación de un SDK con C++
En este tutorial se muestra cómo crear un SDK nativo de biblioteca matemática de C++, empaquetar el SDK como una extensión Visual Studio (VSIX) y, a continuación, usarlo para crear una aplicación. El tutorial se divide en estos pasos:

- [Para crear las bibliotecas nativas y Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Para crear el proyecto de extensión NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Para crear una aplicación de ejemplo que usa la biblioteca de clases](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Prerrequisitos
 Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, [consulte Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>Para crear las bibliotecas nativas y Windows Runtime

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

2. En la lista de plantillas, expanda **Visual C++** Windows Universal y, a continuación, seleccione la plantilla  >   **DLL (Windows aplicaciones universales).** En el **cuadro** Nombre, especifique `NativeMath` y, a continuación, elija **el botón** Aceptar.

3. Actualice *NativeMath.h para* que coincida con el código siguiente.

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h" id="Snippet1":::

4. Actualice *NativeMath.cpp para* que coincida con este código:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp" id="Snippet2":::

5. En Explorador de soluciones , abra el menú contextual de la solución **"NativeMath"** y, a continuación, elija **Agregar** nuevo   >  **Project**.

6. En la lista de plantillas, expanda **Visual C++** y, a continuación, seleccione la **Windows Componente en tiempo de** ejecución. En el **cuadro** Nombre, especifique `NativeMathWRT` y, a continuación, elija **el botón** Aceptar.

7. Actualice *Class1.h para* que coincida con este código:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h" id="Snippet3":::

8. Actualice *Class1.cpp para* que coincida con este código:

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp" id="Snippet4":::

9. En la barra de menús, elija **Compilar** > **Compilar solución**.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> Para crear el proyecto de extensión NativeMathVSIX

1. En Explorador de soluciones , abra el menú contextual de la solución **"NativeMath"** y, a continuación, elija **Agregar** nuevo   >  **Project**.

2. En la lista de plantillas, expanda Extensibilidad de **Visual C#** y, a  >  continuación, **seleccione VSIX Project**. En el **cuadro** Nombre, especifique **NativeMathVSIX** y, a continuación, elija el **botón** Aceptar.

3. En **Explorador de soluciones**, abra el menú contextual **de source.extension.vsixmanifest** y, a continuación, elija **Ver código**.

4. Use el siguiente código XML para reemplazar el XML existente.

    ```xml
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
      <Metadata>
        <Identity Id="NativeMathVSIX..c6b3cae1-e7e2-4e71-90f6-21017ea0dff7" Version="1.0" Language="en-US" Publisher="MyName" />
        <DisplayName>Native Math SDK</DisplayName>
        <Description>Native Math Library w/ Windows Runtime Additions</Description>
      </Metadata>
      <Installation Scope="Global" AllUsers="true">
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="NativeMathSDK" SdkVersion="1.0" />
      </Installation>
      <Dependencies>
      </Dependencies>
      <Assets>
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
      </Assets>
    </PackageManifest>
    ```

5. En **Explorador de soluciones**, abra el menú contextual del proyecto **NativeMathVSIX** y, a continuación, **elija Agregar nuevo**  >  **elemento**.

6. En la lista de elementos **de Visual C#,** expanda **Datos** y, a continuación, seleccione **Archivo XML**. En el **cuadro** Nombre, especifique `SDKManifest.xml` y, a continuación, elija **el botón** Aceptar.

7. Use este XML para reemplazar el contenido del archivo:

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml" id="Snippet5":::

8. En **Explorador de soluciones**, en el **proyecto NativeMathVSIX,** cree esta estructura de carpetas:

    ```xml
    \DesignTime
          \CommonConfiguration
                \Neutral
                      \Include
          \Debug
                \x86
    \Redist
          \Debug
                \x86
    \References
          \CommonConfiguration
                \Neutral
    ```

9. En **Explorador de soluciones**, abra el menú contextual de la solución **"NativeMath"** y, a continuación, elija Abrir carpeta **en Explorador de archivos**.

10. En **Explorador de archivos**, copie *$SolutionRoot$\NativeMath\NativeMath.h* y, a continuación, en **Explorador de soluciones**, en el proyecto **NativeMathVSIX,** péguelo en la *carpeta $SolutionRoot$\NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include. \\*

     Copie *$SolutionRoot$\Debug\NativeMath\NativeMath.lib* y péguelo en la carpeta *\\ $SolutionRoot$\NativeMathVSIX\DesignTime\Debug\x86.*

     Copie *$SolutionRoot$\Debug\NativeMath\NativeMath.dll* y péguelo en la *carpeta $SolutionRoot$\NativeMathVSIX\Redist\Debug\x86. \\*

     Copie *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll* y péguelo en la *carpeta $SolutionRoot$\NativeMathVSIX\Redist\Debug\x86.*
     Copie *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd* y péguelo en la *carpeta $SolutionRoot$\NativeMathVSIX\References\CommonConfiguration\Neutral.*

     Copie *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri* y péguelo en la carpeta *$SolutionRoot$\NativeMathVSIX\References\CommonConfiguration\Neutral.*

11. En la *carpeta $SolutionRoot$\NativeMathVSIX\DesignTime\Debug\x86, \\* cree un archivo de texto denominado *NativeMathSDK.props* y pegue en él el siguiente contenido:
   
    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <NativeMathSDKPath>$(FrameworkSDKRoot)\..\..\UAP\v0.8.0.0\ExtensionSDKs\NativeMathSDK\1.0\</NativeMathSDKPath>
        <IncludePath>$(NativeMathSDKPath)DesignTime\CommonConfiguration\Neutral\Include;$(IncludePath)</IncludePath>
        <LibraryPath>$(NativeMathSDKPath)DesignTime\Debug\x86;$(LibraryPath)</LibraryPath>
      </PropertyGroup>
      <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
         <Link>
           <AdditionalDependencies>NativeMath.lib;%(AdditionalDependencies)</AdditionalDependencies>
         </Link>
      </ItemDefinitionGroup>
    </Project>
    ```

12. En la barra de menús, elija **Ver**  >  **otras Windows**  >  **propiedades** (teclado: elija la tecla **F4).**

13. En **Explorador de soluciones**, seleccione el **archivo NativeMathWRT.winmd.** En la **ventana Propiedades,** cambie la propiedad **Acción** de compilación a **Contenido** y, a continuación, cambie la propiedad Incluir en **VSIX** a **True.**

     Repita este proceso para el **archivo NativeMath.h.**

     Repita este proceso para el **archivo NativeMathWRT.pri.**

     Repita este proceso para el **archivo NativeMath.Lib.**

     Repita este proceso para el **archivo NativeMathSDK.props.**

14. En **Explorador de soluciones**, seleccione el **archivo NativeMath.h.** En la **ventana** Propiedades, cambie la **propiedad Incluir en VSIX** a **True.**

     Repita este proceso para el **NativeMath.dll** archivo.

     Repita este proceso para el **NativeMathWRT.dll** archivo.

     Repita este proceso para el **SDKManifest.xml** archivo.

15. En la barra de menús, elija **Compilar** > **Compilar solución**.

16. En **Explorador de soluciones**, abra el menú contextual del proyecto **NativeMathVSIX** y, a continuación, elija Abrir carpeta **en Explorador de archivos**.

17. En **Explorador de archivos**, vaya a la carpeta *$SolutionRoot$\NativeMathVSIX\bin\Debug* y ejecute *NativeMathVSIX.vsix* para comenzar la instalación.

18. Elija el **botón** Instalar, espere a que finalice la instalación y, a continuación, abra Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Para crear una aplicación de ejemplo que usa la biblioteca de clases

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

2. En la lista de plantillas, expanda **Visual C++** Windows  >  **Universal** y, a continuación, seleccione Aplicación **en blanco.** En el **cuadro** Nombre, especifique **NativeMathSDKSample** y, a continuación, elija el **botón** Aceptar.

3. En **Explorador de soluciones**, abra el menú contextual del **proyecto NativeMathSDKSample** y elija **Agregar**  >  **referencia.**

4. En el **cuadro de diálogo** Agregar referencia , en la lista de tipos de referencia, expanda Universal **Windows** y, a continuación, **seleccione Extensiones**. Por último, active la **casilla SDK de Matemáticas** nativas y, a continuación, elija **el botón** Aceptar.

5. Muestra las propiedades del proyecto para NativeMathSDKSample.

    Las propiedades que definió en *NativeMathSDK.props* se aplicaron al agregar la referencia. Para comprobar que se aplicaron las propiedades, examine la propiedad **VC++ Directories** de las propiedades de configuración **del proyecto**.

6. En **Explorador de soluciones**, abra **MainPage.xaml** y, a continuación, use el código XAML siguiente para reemplazar su contenido:

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml" id="Snippet1":::

7. Actualice *Mainpage.xaml.h para* que coincida con este código:

    :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h" id="Snippet2":::

8. Actualice *MainPage.xaml.cpp para* que coincida con este código:

    :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp" id="Snippet3":::

9. Elija la **tecla F5** para ejecutar la aplicación.

10. En la aplicación, escriba dos números cualquiera, seleccione una operación y, a continuación, elija el **=** botón.

     Aparece el resultado correcto.

    En este tutorial se ha mostrado cómo crear y usar un SDK de extensión para llamar a una [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteca y a una biblioteca que no es de [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] .

## <a name="next-steps"></a>Pasos siguientes

## <a name="see-also"></a>Consulte también
- [Tutorial: Creación de un SDK mediante C# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Creación de un kit de desarrollo de software](../extensibility/creating-a-software-development-kit.md)
