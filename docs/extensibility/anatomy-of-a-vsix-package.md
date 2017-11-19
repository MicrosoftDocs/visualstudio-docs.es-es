---
title: "Anatomía de un paquete VSIX | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 519993c8527b0cd64c283416cd60eb48112e6886
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomía de un paquete VSIX
Un paquete VSIX es un archivo .vsix que contiene una o varias extensiones de Visual Studio, junto con los metadatos que Visual Studio usa para clasificar e instalar las extensiones. Que los metadatos se incluye en el manifiesto de VSIX y el archivo [Content_Types] .xml. Un paquete VSIX también puede contener uno o más archivos Extension.vsixlangpack para proporcionar el texto localizado el programa de instalación y puede contener paquetes VSIX adicionales para instalar las dependencias.  
  
 El formato de paquete VSIX sigue el estándar Open Packaging Conventions (OPC). El paquete contiene los archivos binarios y los archivos auxiliares, junto con un archivo [Content_Types] .xml y un .vsix archivo de manifiesto. Un paquete VSIX puede contener la salida de varios proyectos, o incluso varios paquetes que tienen sus propios manifiestos.  
  
> [!NOTE]
>  Los nombres de los archivos incluidos en los paquetes VSIX no deben incluir espacios ni caracteres que están reservados en identificadores de recursos uniformes (URI), como se definen en [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>El manifiesto de VSIX  
 El manifiesto de VSIX contiene información acerca de la extensión para instalarse y sigue el esquema VSX. Para obtener más información, consulte [referencia de 1.0 de esquema de extensión VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Para un ejemplo de manifiesto VSIX, vea [elemento PackageManifest (elemento Root, esquema VSX)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 El manifiesto de VSIX debe denominarse `extension.vsixmanifest` cuando está incluido en un archivo. vsix.  
  
## <a name="the-content"></a>El contenido  
 Un paquete VSIX puede contener plantillas, elementos de cuadro de herramientas, VSPackages o cualquier otro tipo de extensión que es compatible con Visual Studio.  
  
## <a name="language-packs"></a>Paquetes de idioma  
 Un paquete VSIX puede contener uno o más archivos Extension.vsixlangpack para proporcionar el texto traducido durante la instalación. Para obtener más información, consulte [adaptar paquetes VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Dependencias y referencias  
 Un paquete VSIX puede contener otros paquetes VSIX como referencias. Cada uno de estos otros paquetes debe incluir su propio manifiesto VSIX.  
  
 Si un usuario intenta instalar una extensión que tiene dependencias, el instalador comprueba que los ensamblados necesarios están instalados en el sistema del usuario. Si no se encuentran los ensamblados necesarios, **extensiones y actualizaciones** muestra una lista de los ensamblados que faltan.  
  
 Si el manifiesto de la extensión incluye uno o más [referencia](http://msdn.microsoft.com/en-us/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) elementos, **extensiones y actualizaciones** compara el manifiesto de todas las referencias a las extensiones que están instalados en el sistema e instala el extensión que se hace referencia, si aún no está instalado. Si está instalada una versión anterior de una extensión que se hace referencia, lo reemplaza la versión más reciente.  
  
 Si un proyecto en una solución de varios proyecto incluye una referencia a otro proyecto en la misma solución, el paquete VSIX incluye las dependencias de ese proyecto. Puede invalidar este comportamiento haciendo clic en la referencia del proyecto interno y, a continuación, en la **propiedades** ventana, establecer el **salida grupos incluidos en VSIX** propiedad `BuiltProjectOutputGroup`.  
  
 Para incluir archivos DLL satélite de los ensamblados que se hace referencia en el paquete VSIX, agregue `SatelliteDllsProjectOutputGroup` a la **salida grupos incluidos en VSIX** propiedad.  
  
## <a name="installation-location"></a>Ubicación de instalación  
 Durante la instalación, **extensiones y actualizaciones** busca el contenido del paquete VSIX en una carpeta en % LocalAppData%\Microsoft\VisualStudio\14.0\Extensions.  
  
 De forma predeterminada, la instalación se aplica solo al usuario actual, porque % LocalAppData % es un directorio específico del usuario. Sin embargo, si establece la [AllUsers](http://msdn.microsoft.com/en-us/ac817f50-3276-4ddb-b467-8bbb1432455b) elemento del manifiesto para `True`, se instalará la extensión en... \\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions y estará disponible para todos los usuarios del equipo.  
  
## <a name="contenttypesxml"></a>[Content_Types] .xml  
 El archivo [Content_Types] .xml identifica los tipos de archivo en el archivo .vsix expandido. Visual Studio utiliza este archivo durante la instalación del paquete, pero no instala el propio archivo. Para obtener más información acerca de este archivo, consulte [la estructura de los archivos de [Content_types] .xml](the-structure-of-the-content-types-dot-xml-file.md).  
  
 Un archivo [Content_Types] .xml es necesario por el Open Packaging Conventions (OPC) estándar. Para obtener más información sobre OPC, vea [OPC: nuevo estándar para empaquetar sus datos](http://go.microsoft.com/fwlink/?LinkID=148207) en el sitio Web de MSDN.