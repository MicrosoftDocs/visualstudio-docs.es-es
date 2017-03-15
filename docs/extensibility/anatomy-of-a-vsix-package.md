---
title: "Anatomía de un paquete VSIX | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 15
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
ms.sourcegitcommit: 7278fb37984b92a6a07823c552db5c59a446d0d2
ms.openlocfilehash: 633db03670180ac83c5c936f66953fb38d4ebd67
ms.lasthandoff: 02/22/2017

---
# <a name="anatomy-of-a-vsix-package"></a>Anatomía de un paquete VSIX
Un paquete VSIX es un archivo .vsix que contiene una o más extensiones de Visual Studio, junto con los metadatos de que Visual Studio utiliza para clasificar e instalar las extensiones. Ese metadatos se encuentran en el manifiesto de VSIX y el archivo .xml [Content_Types]. Un paquete VSIX también puede contener uno o más archivos Extension.vsixlangpack para proporcionar el texto de instalación localizada y puede contener paquetes VSIX adicionales para instalar las dependencias.  
  
 El formato de paquete VSIX sigue el estándar Open Packaging Conventions (OPC). El paquete contiene archivos binarios y los archivos auxiliares, junto con un archivo [Content_Types] .xml y un .vsix archivo de manifiesto. Un paquete VSIX puede contener la salida de varios proyectos o incluso varios paquetes que tienen sus propios manifiestos.  
  
> [!NOTE]
>  Los nombres de los archivos incluidos en los paquetes VSIX no deben incluir espacios ni caracteres reservados en identificadores de recursos uniformes (URI), como se definen en [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>El manifiesto de VSIX  
 El manifiesto de VSIX contiene información acerca de la extensión para instalarse y sigue el esquema VSX. Para obtener más información, consulte [referencia de 1.0 de esquema de extensión VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Para un manifiesto VSIX de ejemplo, vea [PackageManifest elemento (elemento Root, esquema VSX)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 El manifiesto de VSIX se debe denominar `extension.vsixmanifest` cuando está incluido en un archivo. vsix.  
  
## <a name="the-content"></a>El contenido  
 Un paquete VSIX puede contener plantillas, elementos de cuadro de herramientas, VSPackages o cualquier otro tipo de extensión admitida por Visual Studio.  
  
## <a name="language-packs"></a>Paquetes de idioma  
 Un paquete VSIX puede contener uno o más archivos Extension.vsixlangpack para proporcionar el texto traducido durante la instalación. Para obtener más información, consulte [localizar los paquetes VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Referencias y dependencias  
 Un paquete VSIX puede contener otros paquetes VSIX como referencias. Cada uno de estos otros paquetes debe incluir su propio manifiesto VSIX.  
  
 Si un usuario intenta instalar una extensión que tiene dependencias, el instalador comprueba que los ensamblados necesarios están instalados en el sistema del usuario. Si no se encuentran los ensamblados necesarios, **extensiones y actualizaciones** muestra una lista de los ensamblados que faltan.  
  
 Si el manifiesto de la extensión incluye uno o más [referencia](http://msdn.microsoft.com/en-us/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) elementos **extensiones y actualizaciones** compara el manifiesto de cada referencia a las extensiones que están instalados en el sistema e instala la extensión que se hace referencia si no está ya instalado. Si está instalada una versión anterior de una extensión que se hace referencia, lo reemplaza la versión más reciente.  
  
 Si un proyecto en una solución de varios proyectos, incluye una referencia a otro proyecto en la misma solución, el paquete VSIX incluye las dependencias del proyecto. Puede invalidar este comportamiento haciendo clic en la referencia del proyecto interno y, a continuación, en la **propiedades** ventana, establecer el **salida grupos incluidos en VSIX** propiedad `BuiltProjectOutputGroup`.  
  
 Para incluir los archivos DLL satélite de los ensamblados que se hace referencia en el paquete VSIX, agregue `SatelliteDllsProjectOutputGroup` a la **salida grupos incluidos en VSIX** propiedad.  
  
## <a name="installation-location"></a>Ubicación de instalación  
 Durante la instalación, **extensiones y actualizaciones** busca el contenido del paquete VSIX en una carpeta en % LocalAppData%\Microsoft\VisualStudio\14.0\Extensions.  
  
 De forma predeterminada, la instalación se aplica sólo al usuario actual, porque % LocalAppData % es un directorio específico del usuario. Sin embargo, si establece la [AllUsers](http://msdn.microsoft.com/en-us/ac817f50-3276-4ddb-b467-8bbb1432455b) elemento del manifiesto para `True`, la extensión se instalarán en... \\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions y estará disponible para todos los usuarios del equipo.  
  
## <a name="contenttypesxml"></a>[Content_Types] .xml  
 El archivo [Content_Types] .xml identifica los tipos de archivo en el archivo .vsix expandido. Visual Studio utiliza este archivo durante la instalación del paquete pero no instala el propio archivo. Para obtener más información acerca de este archivo, consulte [estructura del archivo [Content_types] .xml](the-structure-of-the-content-types-dot-xml-file.md).  
  
 Un archivo [Content_Types] .xml se requiere por la Open Packaging Conventions (OPC) estándar. Para obtener más información sobre OPC, vea [OPC: nuevo estándar para empaquetar sus datos](http://go.microsoft.com/fwlink/?LinkID=148207) en el sitio Web de MSDN.
