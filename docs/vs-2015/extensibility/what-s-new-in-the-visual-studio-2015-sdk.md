---
title: Novedades de Visual Studio 2015 SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d51474f2e242f764a84edaa9f2712418c859460
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408708"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>¿Qué&#39;s en el SDK Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El SDK de Visual Studio tiene las siguientes características nuevas y actualizadas para Visual Studio 2015, actualizado de Visual Studio 2015 y Visual Studio 2017.

## <a name="visual-studio-2017"></a>Visual Studio 2017

A partir de Visual Studio 2017, análisis de proyecto personalizado y las plantillas de elemento ya no se realizará. En su lugar, la extensión debe proporcionar los archivos de manifiesto de plantilla que describen la ubicación de instalación de estas plantillas. Puede usar Visual Studio 2017 para actualizar las extensiones VSIX. Si implementa la extensión con un archivo MSI, debe generar manualmente los archivos de manifiesto de plantilla. Para obtener más información, consulte [actualización del proyecto personalizado y las plantillas de elemento para Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). El esquema del manifiesto de plantilla está documentado en [referencia de esquema de manifiesto de Visual Studio plantilla](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="vs-2015-sdk-update-1"></a>SDK de VS 2015 Update 1
 Actualización 1 incluye herramientas para ayudar a su extensión funciona bien con los temas de color y el servicio de imágenes de Visual Studio.

 Estos temas están bajo el [utilidades VSSDK](../extensibility/internals/vssdk-utilities.md) sección:

- El [herramientas de creación de temas de Color](../extensibility/internals/color-theming-tools.md) le ayudarán a crear y editar los colores personalizados para Visual Studio.

- El [herramientas de servicio de imágenes](../extensibility/internals/image-service-tools.md) le permiten trabajar con archivos de manifiesto de imagen de Visual Studio.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nueva forma de agregar el SDK de Visual Studio a Visual Studio
 A partir de Visual Studio 2015, no es necesario descargar el SDK de Visual Studio por separado. En su lugar, puede instalarlo como parte del proceso de instalación normal, o puede elegir instalarla más adelante. Al abrir o crear una solución VSIX, Visual Studio le pedirá que instale las herramientas de extensibilidad de Visual Studio. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="new-ways-of-creating-extensions"></a>Nuevas formas de crear extensiones
 A partir de Visual Studio 2015 SDK, tienen diferentes opciones para crear extensiones, dependiendo del lenguaje de programación que usa.

### <a name="visual-c-and-visual-basic"></a>Visual C# y Visual Basic
 Para C# y Visual Basic, hay una gama completa de plantillas de elemento de proyecto que le permiten crear paquetes VSPackage, comandos de menú, ventanas de herramientas, clasificadores de editor, elementos gráficos del editor y extensiones de editor de margen. Puede agregar alguno o todos ellos al proyecto VSIX estándar. Para obtener más información, consulte:

- [Creación de una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)

- [Creación de una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md)

- [Creación de una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- [Creación de una extensión con un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

     El Asistente de VSPackage ya no crea las extensiones en C# o Visual Basic.

### <a name="c"></a>C++
 Para C++, el Asistente de VSPackage admite comandos de menú, ventanas de herramientas y editores personalizados. Busque en el **nuevo proyecto** cuadro de diálogo de **Visual C++ / extensibilidad**.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Ensamblados de referencia SDK de VS a través de NuGet
 Para una mayor movilidad y uso compartido de los proyectos de extensibilidad, puede usar las versiones de NuGet de los ensamblados de referencia de SDK de VS.  Están disponibles en [nuget.org](http://www.nuget.org) publicados por [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) y pueden agregarse fácilmente a su proyecto o solución a través de Visual Studio **hace referencia a y la administración de NuGet Paquetes** cuadro de diálogo. Puede agregar referencias individuales a los ensamblados de extensibilidad específicos o agregar todo el SDK de VS hace referencia a ensamblados a la vez mediante el SDK de VS [paquete Meta](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Para obtener más información sobre NuGet, consulte [información general sobre NuGet](http://docs.nuget.org/) y [administrar paquetes de NuGet mediante el cuadro de diálogo](http://docs.nuget.org/Consume/Package-Manager-Dialog).

 Cuando usa las versiones de NuGet de los ensamblados de referencia de SDK de VS, otro usuario no necesita instalar el SDK de VS para abrir y compilar el proyecto.  Los ensamblados de referencia de NuGet y herramientas de compilación del SDK de VS se instalarán automáticamente en su equipo para ese proyecto.

 Las plantillas de elementos de SDK de VS usar NuGet para sus referencias y herramientas de compilación para obtener las ventajas de NuGet de forma predeterminada.

> [!NOTE]
> Aún puede usar los ensamblados de referencia de SDK de VS instalados con sus proyectos (ubicado en \<ubicación de instalación de Visual Studio > \ VSSDK\VisualStudioIntegration\Common\Assemblies) y los proyectos de extensibilidad existentes no necesitan ser actualizado para usar paquetes de NuGet.  El proyecto **hace referencia a / para agregar una referencia** diálogo sigue usando los ensamblados de referencia de SDK de VS instalados.
>
> Si desea modificar los proyectos existentes para usar NuGet, vea [Cómo: Migrar VSPackages a Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) que tiene una sección sobre la actualización de proyectos de extensibilidad a los paquetes de NuGet.

## <a name="light-bulbs"></a>Bombillas
 Una de las nuevas formas más interesantes de escribir código de extensión se proporciona el proyecto Roslyn. Para obtener más información, consulte [Roslyn](https://github.com/dotnet/Roslyn).

 Las bombillas son una característica nueva que se incluye con el VSSDK. Son iconos que se usan en el editor de Visual Studio que se expanden para mostrar un conjunto de acciones de refactorización de código o soluciona los problemas identificados por los analizadores de código integrados. Para obtener más información, vea [Tutorial: Mostrar sugerencias de bombilla](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).

## <a name="updated-user-experience-guidelines"></a>Instrucciones para la experiencia de usuario actualizada
 ¿Diseñar nuevas extensiones o características para Visual Studio? Consulte el valor actualizado y ampliado [directrices de experiencia de usuario de Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Encontrará el [tokens de color](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [tamaños de fuente](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [especificaciones de diseño del cuadro de diálogo](../extensibility/ux-guidelines/layout-for-visual-studio.md)y otra orientación que necesita para integrar sin problemas la nueva interfaz de usuario con Visual Studio.
