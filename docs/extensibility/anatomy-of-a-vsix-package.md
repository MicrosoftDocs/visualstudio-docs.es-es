---
title: Anatomía de un paquete VSIX | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5c60e0b812cd0557b266d3e34dae62cb22cc57d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281762"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomía de un paquete VSIX
Un paquete VSIX no es un *.vsix* archivo que contiene una o varias extensiones de Visual Studio, junto con los metadatos de Visual Studio usa para clasificar e instalar las extensiones. Los metadatos se encuentran en el manifiesto VSIX y la *[Content_Types] .xml* archivo. Un paquete VSIX también puede contener uno o varios *Extension.vsixlangpack* archivos para proporcionar texto de programa de instalación localizado y puede contener paquetes VSIX adicionales para instalar las dependencias.  
  
 El formato de paquete VSIX sigue el estándar Open Packaging Conventions (OPC). El paquete contiene archivos binarios y archivos auxiliares, junto con un *[Content_Types] .xml* archivo y un *.vsix* archivo de manifiesto. Un paquete VSIX puede contener la salida de varios proyectos, o incluso varios paquetes que tienen sus propios manifiestos.  
  
> [!NOTE]
>  Los nombres de los archivos incluidos en paquetes VSIX no puede contener espacios ni caracteres reservados en identificadores de recursos uniforme (URI), como se definen en [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>El manifiesto de VSIX  
 El manifiesto de VSIX contiene información acerca de la extensión para instalarse y sigue el esquema VSX. Para obtener más información, consulte [referencia de esquema 1.0 de extensión VSIX](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Para un ejemplo de manifiesto VSIX, vea [elemento PackageManifest (elemento root, esquema VSX)](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 El manifiesto de VSIX se debe denominar `extension.vsixmanifest` cuando está incluido en un ^ archivo de VSIX.  
  
## <a name="the-content"></a>El contenido  
 Un paquete VSIX puede contener plantillas, elementos de cuadro de herramientas, los paquetes VSPackage o cualquier otro tipo de extensión que es compatible con Visual Studio.  
  
## <a name="language-packs"></a>Paquetes de idioma  
 Un paquete VSIX puede contener uno o más *Extension.vsixlangpack* archivos para proporcionar el texto localizado durante la instalación. Para obtener más información, consulte [paquetes VSIX localizar](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Dependencias y referencias  
 Un paquete VSIX puede contener otros paquetes VSIX como referencias. Cada uno de estos otros paquetes debe incluir su propio manifiesto VSIX.  
  
 Si un usuario intenta instalar una extensión que tiene dependencias, el instalador comprueba que los ensamblados necesarios están instalados en el sistema del usuario. Si no se encuentran los ensamblados necesarios, **extensiones y actualizaciones** muestra una lista de los ensamblados que faltan.  
  
 Si el manifiesto de la extensión incluye uno o varios [referencia](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) elementos, **extensiones y actualizaciones** compara el manifiesto de todas las referencias a las extensiones que están instalados en el sistema e instala el extensión que se hace referencia si no está ya instalado. Si está instalada una versión anterior de una extensión que se hace referencia, lo reemplaza la versión más reciente.  
  
 Si un proyecto en una solución multiproyecto incluye una referencia a otro proyecto en la misma solución, el paquete VSIX incluye las dependencias de ese proyecto. Puede invalidar este comportamiento, haga clic en la referencia del proyecto interno y, a continuación, en el **propiedades** ventana, establecer el **salida grupos incluidos en VSIX** propiedad `BuiltProjectOutputGroup`.  
  
 Para incluir archivos DLL satélite de los ensamblados que se hace referencia en el paquete VSIX, agregue `SatelliteDllsProjectOutputGroup` a la **salida grupos incluidos en VSIX** propiedad.  
  
## <a name="installation-location"></a>Ubicación de instalación  
 Durante la instalación, **extensiones y actualizaciones** busca el contenido del paquete VSIX en una carpeta bajo *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions*.  
  
 De forma predeterminada, la instalación sólo se aplica al usuario actual, porque *% LocalAppData %* es un directorio específico del usuario. Sin embargo, si establece la [AllUsers](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b) elemento del manifiesto para `True`, la extensión se instalará en *... \\* VisualStudioInstallationFolder*\Common7\IDE\Extensions* y estará disponible para todos los usuarios del equipo.  
  
## <a name="contenttypesxml"></a>[Content_Types] .xml  
 El *[Content_Types] .xml* archivo identifica los tipos de archivo en el modo expandido *.vsix* archivo. Visual Studio usa este archivo durante la instalación del paquete, pero no instala el propio archivo. Para obtener más información acerca de este archivo, consulte [la estructura del archivo [Content_types] .xml](the-structure-of-the-content-types-dot-xml-file.md).  
  
 Un *[Content_Types] .xml* archivo es requerido por el estándar Open Packaging Conventions (OPC). Para obtener más información sobre OPC, vea [OPC: un nuevo estándar para empaquetar sus datos](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/) en el sitio Web de MSDN.