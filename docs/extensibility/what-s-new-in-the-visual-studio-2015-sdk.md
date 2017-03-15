---
title: Novedades en el SDK Visual Studio 2015 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: 8d77fce54b12b90f6a2632fd1c1741990be42a08
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Novedades en el SDK Visual Studio 2015
El SDK de Visual Studio tiene las siguientes características nuevas y actualizadas para Visual Studio 2015, Visual Studio 2015 actualizado y 2017 de Visual Studio.  
  
## <a name="vs-2015-sdk-update-1"></a>Actualización del SDK de VS 2015 1  
 Actualización 1 incluye herramientas para ayudar a su extensión funciona bien con temas de color y el servicio de imágenes de Visual Studio.  
  
 Estos temas están bajo el [VSSDK utilidades](../extensibility/internals/vssdk-utilities.md) sección:  
  
-   El [herramientas de creación de temas de Color](../extensibility/internals/color-theming-tools.md) le ayudarán a crear y editar los colores personalizados para Visual Studio.  
  
-   El [herramientas de servicio de imágenes](../extensibility/internals/image-service-tools.md) le permiten trabajar con archivos de manifiesto de imágenes de Visual Studio.  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nueva manera de agregar el SDK de Visual Studio a Visual Studio  
 A partir de Visual Studio 2015, no necesitará descargar el SDK de Visual Studio por separado. En su lugar, puede instalarlo como parte del proceso de instalación normal, o bien puede instalarlo más adelante. Al abrir o crear una solución VSIX, Visual Studio le pedirá que instale las herramientas de extensibilidad de Visual Studio. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="new-ways-of-creating-extensions"></a>Nuevas formas de crear extensiones  
 A partir de los SDK de Visual Studio 2015, tienen diferentes opciones para crear extensiones, dependiendo del lenguaje de programación que está utilizando.  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# y Visual Basic  
 Para C# y Visual Basic, hay una amplia gama de plantillas de elemento de proyecto que le permiten crear VSPackages, comandos de menú, ventanas de herramientas, editor de clasificadores, elementos gráficos del editor y extensiones de editor de margen. Puede agregar cualquier o todos ellos al proyecto VSIX estándar. Para obtener más información, consulte:  
  
-   [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [Crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [Crear una extensión con una plantilla de elemento de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [Crear una extensión con un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     El Asistente de VSPackage ya no crea extensiones en C# o Visual Basic.  
  
### <a name="c"></a>C++  
 Para C++, el Asistente de VSPackage admite comandos de menú, ventanas de herramientas y editores personalizados. Busque en el **nuevo proyecto** cuadro de diálogo de **Visual C++ / extensibilidad**.  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Ensamblados de referencia SDK de VS mediante NuGet  
 Para una mayor movilidad y uso compartido de proyectos de extensibilidad, puede usar las versiones de los ensamblados de referencia de SDK de VS de NuGet.  Están disponibles en [nuget.org](http://www.nuget.org) publicado por [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) y se pueden agregar fácilmente a su proyecto o solución a través de Visual Studio **hace referencia / administrar paquetes de NuGet** cuadro de diálogo. Puede agregar referencias individuales a los ensamblados de extensibilidad específicas o agregue el SDK de VS hace referencia a ensamblados a la vez mediante el SDK de VS [paquete Meta](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Para obtener más información sobre NuGet, consulte [descripción general de NuGet](http://docs.nuget.org/) y [administrar paquetes de NuGet mediante el cuadro de diálogo](http://docs.nuget.org/Consume/Package-Manager-Dialog).  
  
 Cuando utiliza las versiones de los ensamblados de referencia de SDK de VS de NuGet, otro usuario no necesita instalar el SDK de VS para abrir y generar el proyecto.  Los ensamblados de referencia de NuGet y herramientas de compilación del SDK de VS se instalará automáticamente en su equipo para ese proyecto.  
  
 Las plantillas de elementos de SDK de VS usar NuGet para sus referencias y herramientas de compilación para obtener las ventajas de NuGet de forma predeterminada.  
  
> [!NOTE]
>  Se puede seguir utilizando los ensamblados de referencia de SDK de VS instalado con los proyectos (ubicado en \<ubicación de instalación de Visual Studio > \ VSSDK\VisualStudioIntegration\Common\Assemblies) y proyectos de extensibilidad existentes no necesitan actualizarse para utilizar paquetes de NuGet.  El proyecto **hace referencia / Agregar referencia** diálogo sigue utilizando los ensamblados de referencia de SDK de VS instalado.  
>   
>  Si desea modificar los proyectos existentes para usar NuGet, consulte [Cómo: migrar VSPackages a Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) que tiene una sección acerca de cómo actualizar los proyectos de extensibilidad para paquetes de NuGet.  
  
## <a name="light-bulbs"></a>Las bombillas  
 Una de las formas nuevas más interesantes de escribir el código de extensión se proporciona por el proyecto Roslyn. Para obtener más información, consulte [Roslyn](https://github.com/dotnet/Roslyn).  
  
 Las bombillas son una nueva característica que se incluye con la VSSDK. Son los iconos que se usa en el editor de Visual Studio que se expanden para mostrar un conjunto de acciones de refactorización de código o soluciona los problemas identificados por los analizadores de código integrados. Para obtener más información, consulte [Tutorial: Mostrar sugerencias de bombilla](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
## <a name="updated-user-experience-guidelines"></a>Instrucciones para la experiencia de usuario actualizada  
 ¿Diseñar nuevas extensiones o características de Visual Studio? Consulte actualizada y ampliada [instrucciones para la experiencia del usuario de Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Encontrará el [color tokens](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [tamaños de fuente](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [especificaciones de diseño del cuadro de diálogo](../extensibility/ux-guidelines/layout-for-visual-studio.md)y otras instrucciones que necesita integrar perfectamente la nueva interfaz de usuario con Visual Studio.
