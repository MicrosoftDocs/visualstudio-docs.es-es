---
title: ¿Qué&#39;s nuevos en el SDK de Visual Studio 2015 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6488f28f2963e17c716c2e9d395ddf77f270e7b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144712"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>¿Qué&#39;s nuevos en el SDK de Visual Studio 2015
El SDK de Visual Studio tiene las siguientes características nuevas y actualizadas de Visual Studio 2015, actualizado de Visual Studio 2015 y Visual Studio de 2017.  
  
## <a name="vs-2015-sdk-update-1"></a>SDK de VS 2015 Update 1  
 Actualización 1 incluye herramientas que ayudan a la extensión se funcionen bien con temas de color y el servicio de imágenes de Visual Studio.  
  
 Estos temas están bajo el [VSSDK utilidades](../extensibility/internals/vssdk-utilities.md) sección:  
  
-   El [herramientas de creación de temas de Color](../extensibility/internals/color-theming-tools.md) le ayudarán a crear y editar los colores personalizados de Visual Studio.  
  
-   El [herramientas de servicios de imagen](../extensibility/internals/image-service-tools.md) permiten trabajar con archivos de manifiesto de imagen de Visual Studio.  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nueva manera de agregar el SDK de Visual Studio a Visual Studio  
 A partir de Visual Studio 2015, no es necesario descargar el SDK de Visual Studio por separado. En su lugar, puede instalarlo como parte del proceso de instalación normal, o puede elegir instalarlo más adelante. Al abrir o crear una solución VSIX, Visual Studio le solicitará que instale las herramientas de extensibilidad de Visual Studio. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="new-ways-of-creating-extensions"></a>Nuevas formas de crear extensiones  
 A partir de Visual Studio 2015 SDK, tienen diferentes opciones para crear extensiones, según el lenguaje de programación que está usando.  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# y Visual Basic  
 Para C# y Visual Basic, hay una amplia gama de plantillas de elemento de proyecto que permiten crear paquetes VSPackage, comandos de menú, ventanas de herramientas, editor clasificadores, elementos gráficos del editor y extensiones de editor de margen. Puede agregar cualquier o todos ellos al proyecto VSIX estándar. Para obtener más información, consulte:  
  
-   [Creación de una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [Creación de una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [Creación de una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [Creación de una extensión con un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     El Asistente de VSPackage ya no crea las extensiones en C# o Visual Basic.  
  
### <a name="c"></a>C++  
 En C++, el Asistente de VSPackage admite comandos de menú, ventanas de herramientas y editores personalizados. Busque en el **nuevo proyecto** cuadro de diálogo de **Visual C++ / extensibilidad**.  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Ensamblados de referencia SDK de VS a través de NuGet  
 Para obtener una mayor portabilidad y uso compartido de los proyectos de extensibilidad, puede usar las versiones de NuGet de los ensamblados de referencia de SDK de VS.  Están disponibles en [nuget.org](http://www.nuget.org) publicados por [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) y se puede agregar fácilmente a su proyecto o solución a través de Visual Studio **hace referencia a / administrar NuGet Paquetes** cuadro de diálogo. Puede agregar referencias individuales a los ensamblados de extensibilidad específicas o agregue el SDK de VS hace referencia a ensamblados a la vez mediante el SDK de VS [paquete Meta](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Para obtener más información sobre NuGet, consulte el [documentación de NuGet](/NuGet) y [UI del Administrador de paquetes](/NuGet/Tools/Package-Manager-UI) temas.  
  
 Cuando se usan las versiones de NuGet de los ensamblados de referencia de SDK de VS, otro usuario no tiene que instalar el SDK de VS para abrir y compilar el proyecto.  Los ensamblados de referencia de NuGet y herramientas de compilación del SDK de VS se instalará automáticamente en su equipo para ese proyecto.  
  
 Las plantillas de elementos de SDK de VS usar NuGet para sus referencias y herramientas de compilación para que aprovechen las ventajas de NuGet de forma predeterminada.  
  
> [!NOTE]
>  Aún puede usar los ensamblados de referencia de SDK de VS que se instala con los proyectos (ubicado en \<ubicación de instalación de Visual Studio > \ VSSDK\VisualStudioIntegration\Common\Assemblies) y no es necesario ser existentes de los proyectos de extensibilidad Actualizar para utilizar paquetes de NuGet.  El proyecto **hace referencia a / agregar referencia** diálogo sigue usando los ensamblados de referencia de SDK de VS instalado.  
>   
>  Si desea modificar los proyectos existentes para usar NuGet, consulte [Cómo: migrar VSPackages a Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) que tiene una sección acerca de cómo actualizar proyectos de extensibilidad de paquetes de NuGet.  
  
## <a name="light-bulbs"></a>Las bombillas  
 Una de las nuevas formas más interesantes de la escritura de código de la extensión se proporciona el proyecto Roslyn. Para obtener más información, consulte [Roslyn](https://github.com/dotnet/Roslyn).  
  
 Las bombillas son una característica nueva que se suministra con el VSSDK. Son iconos que se utilizan en el editor de Visual Studio y que se expanden para mostrar un conjunto de acciones de refactorización de código o soluciona los problemas identificados por los analizadores de código integrados. Para obtener más información, consulte [Tutorial: Mostrar sugerencias de bombilla](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
## <a name="updated-user-experience-guidelines"></a>Instrucciones para la experiencia de usuario actualizada  
 ¿Diseñar nuevas extensiones o características de Visual Studio? Desproteger actualizada y expandido [instrucciones para la experiencia del usuario de Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Encontrará el [tokens de color](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [tamaños de fuente](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [especificaciones de diseño del cuadro de diálogo](../extensibility/ux-guidelines/layout-for-visual-studio.md)y otras instrucciones necesarias para integrar fácilmente la nueva interfaz de usuario con Visual Studio.