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
ms.openlocfilehash: d47e40a5c38eeb7898aa179282fa55bbe17ef1d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917329"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Novedades de&#39;s en el SDK de Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El SDK de Visual Studio tiene las siguientes características nuevas y actualizadas para Visual Studio 2015, Visual Studio 2015 actualizado y Visual Studio 2017.

## <a name="visual-studio-2017"></a>Visual Studio 2017

A partir de Visual Studio 2017, ya no se comprobará si hay plantillas de proyecto y de elemento personalizadas. En su lugar, la extensión debe proporcionar archivos de manifiesto de plantilla que describan la ubicación de instalación de estas plantillas. Puede usar Visual Studio 2017 para actualizar las extensiones VSIX. Si implementa la extensión mediante un archivo MSI, debe generar los archivos de manifiesto de plantilla manualmente. Para obtener más información, consulte [actualización del plantillas de proyecto y elemento para Visual Studio personalizado 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). El esquema de manifiesto de plantilla se documenta en la [referencia de esquema de manifiesto de plantilla de Visual Studio](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK Update 1
 Update 1 incluye herramientas que ayudan a que la extensión funcione bien con los temas de color y el servicio de imágenes de Visual Studio.

 Estos temas se encuentran en la sección [utilidades de VSSDK](../extensibility/internals/vssdk-utilities.md) :

- Las [herramientas](../extensibility/internals/color-theming-tools.md) de creación de colores de color ayudan a crear y editar colores personalizados para Visual Studio.

- Las [herramientas de servicio de imágenes](../extensibility/internals/image-service-tools.md) permiten trabajar con archivos de manifiesto de imagen de Visual Studio.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nueva manera de agregar el SDK de Visual Studio a Visual Studio
 A partir de Visual Studio 2015, no es necesario descargar el SDK de Visual Studio por separado. En su lugar, puede instalarlo como parte del proceso de instalación normal, o puede optar por instalarlo más adelante. Al abrir o crear una solución VSIX, Visual Studio le pedirá que instale el Herramientas de extensibilidad de Visual Studio. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="new-ways-of-creating-extensions"></a>Nuevas formas de crear extensiones
 A partir del SDK de Visual Studio 2015, tiene distintas opciones para crear extensiones, dependiendo del lenguaje de programación que esté usando.

### <a name="visual-c-and-visual-basic"></a>Visual C# y Visual Basic
 Para C# y Visual Basic, hay una gama completa de plantillas de elementos de proyecto que le permiten crear VSPackages, comandos de menú, ventanas de herramientas, clasificadores de editor, elementos gráficos del editor y extensiones de margen del editor. Puede agregar cualquiera de ellos al Proyecto VSIX estándar. Para obtener más información, vea:

- [Creación de una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)

- [Creación de una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md)

- [Creación de una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- [Creación de una extensión con un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

     El Asistente para VSPackage ya no crea extensiones en C# ni en Visual Basic.

### <a name="c"></a>C++
 En el caso de C++, el Asistente para VSPackage admite comandos de menú, ventanas de herramientas y editores personalizados. Búsquelo en el cuadro de diálogo **nuevo proyecto** en **Visual C++/extensibilidad**.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>VS SDK referencia a ensamblados a través de NuGet
 Para aumentar la portabilidad y el uso compartido de proyectos de extensibilidad, puede usar las versiones de NuGet de los ensamblados de referencia del SDK de VS.  Están disponibles en [Nuget.org](https://www.nuget.org/) publicados por [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) y se pueden agregar fácilmente a su proyecto o solución a través del cuadro de diálogo referencias de Visual Studio **/administrar paquetes Nuget** . Puede Agregar referencias individuales a ensamblados de extensibilidad específicos o agregar a la vez todos los ensamblados de referencias del SDK de VS mediante el [metapaquete](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)del SDK de vs. Para más información sobre NuGet, consulte [información general de Nuget](/nuget/) y [Administración de paquetes NuGet mediante el cuadro de diálogo](/nuget/consume-packages/install-use-packages-visual-studio).

 Cuando se usan las versiones de NuGet de los ensamblados de referencia del SDK de VS, no es necesario que otro usuario instale el SDK de VS para abrir y compilar el proyecto.  Los ensamblados de referencia de NuGet y las herramientas de compilación del SDK de VS se instalarán automáticamente en su equipo para ese proyecto.

 Las plantillas de elementos del SDK de VS usan NuGet para sus referencias y herramientas de compilación, de modo que se obtienen las ventajas de NuGet de forma predeterminada.

> [!NOTE]
> Puede seguir usando los ensamblados de referencia instalados de VS SDK con sus proyectos (ubicados en \<Visual Studio Install Location> \ VSSDK\VisualStudioIntegration\Common\Assemblies) y no es necesario actualizar los proyectos de extensibilidad existentes para usar paquetes de NuGet.  El cuadro de diálogo referencias del proyecto **/Agregar referencia** sigue usando los ensamblados de referencia instalados del SDK de vs.
>
> Si desea modificar los proyectos existentes para usar NuGet, consulte [How to: Migrate VSPackages to Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) , que tiene una sección sobre la actualización de proyectos de extensibilidad a paquetes de NuGet.

## <a name="light-bulbs"></a>Bombillas
 El proyecto Roslyn proporciona una de las nuevas formas más emocionantes de escribir código de extensión. Para obtener más información, vea [Roslyn](https://github.com/dotnet/Roslyn).

 Las bombillas son una nueva característica que se suministra con el VSSDK. Son iconos utilizados en el editor de Visual Studio que se expanden para mostrar un conjunto de acciones o correcciones de refactorización de código para los problemas identificados por los analizadores de código integrados. Para obtener más información, vea [Tutorial: Mostrar sugerencias de bombillas](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).

## <a name="updated-user-experience-guidelines"></a>Instrucciones de experiencia del usuario actualizadas
 ¿Cómo diseñar nuevas características o extensiones para Visual Studio? Consulte las directrices de experiencia de [usuario de Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)actualizadas y expandidas.  Encontrará los [tokens de color](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [tamaños de fuente](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [Especificaciones de diseño de cuadros de diálogo](../extensibility/ux-guidelines/layout-for-visual-studio.md)y otras instrucciones que necesita para integrar sin problemas la nueva interfaz de usuario con Visual Studio.
