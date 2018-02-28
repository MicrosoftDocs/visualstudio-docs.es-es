---
title: Especificar identificadores de archivos para las extensiones de nombre de archivo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d5db7a218a718e27f584abbf350b49907b56fb17
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Especificar identificadores de archivos para las extensiones de nombre de archivo
Hay varias maneras de determinar la aplicación que administra un archivo que tiene una extensión de archivo en particular. Los verbos OpenWithList y OpenWithProgids son dos formas de especificar identificadores de archivos en la entrada del registro para la extensión de archivo.  
  
## <a name="openwithlist-verb"></a>Verbo OpenWithList  
 Cuando hace clic en un archivo en el Explorador de Windows, consulte el **abiertos** comando. Si más de un producto está asociado a una extensión, verá un **abrir con** submenú.  
  
 Puede registrar diferentes aplicaciones para abrir una extensión estableciendo la clave de OpenWithList para la extensión de archivo en HKEY_CLASSES_ROOT. Las aplicaciones enumeradas en esta clave para una extensión de archivo aparecen bajo la **recomienda programas** encabezado en la **abrir con** cuadro de diálogo. El ejemplo siguiente muestra las aplicaciones registradas para abrir la extensión de archivo .vcproj.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  Las claves de especificar las aplicaciones están en la lista de HKEY_CLASSES_ROOT\Applications.  
  
 Al agregar una clave de OpenWithList, se declara que la aplicación admite una extensión de archivo incluso si otra aplicación toma posesión de la extensión. Podría tratarse de una versión futura de la aplicación u otra aplicación.  
  
## <a name="openwithprogids"></a>OpenWithProgIDs  
 Identificadores de programación (ProgID) son versiones descriptivas de ClassID que identifican una versión de una aplicación o un objeto COM. Cada objeto puede co-crear debe tener su propio ProgID. Por ejemplo, VisualStudio.DTE.7.1 inicia Visual Studio .NET 2003 mientras se inicia VisualStudio.DTE.10.0 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Como propietario de un tipo de proyecto o el tipo de elemento de proyecto, debe crear un ProgID específico de la versión para la extensión de archivo. Estos ProgID pueden ser redundantes, puesto que más de un ProgID puede iniciar la misma aplicación. Para obtener más información, consulte [registrar verbos de extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md).  
  
 Utilice la siguiente convención de nomenclatura para archivos con control de versiones ProgID para evitar la duplicación con el registro de otros proveedores:  
  
|Extensión de archivo|Con control de versiones ProgID|  
|--------------------|----------------------|  
|.Extension|ProductName. extension.versionMajor.versionMinor|  
  
 Puede registrar las aplicaciones diferentes que pueden abrir una extensión de archivo determinada mediante la adición de ProgID con control de versiones como valores a HKEY_CLASSES_ROOT\\*\<extensión >*\OpenWithProgids clave. Esta clave del registro contiene una lista de ProgID alternativos asociados a la extensión de archivo. Las aplicaciones asociadas con el ProgID enumerados aparecen en la **abrir con***Product Name* submenú. Si la misma aplicación se especifica tanto en el `OpenWithList` y `OpenWithProgids` claves, el sistema operativo combina los duplicados.  
  
> [!NOTE]
>  El `OpenWithProgids` clave solo se admite en Windows XP. Dado que otros sistemas operativos de pasar por alto esta clave, no usarlo como el registro solo para los controladores de archivo. Use esta clave para ofrecer una mejor experiencia de usuario en Windows XP.  
  
 Agregue los ProgID deseados como valores del tipo REG_NONE. El código siguiente proporciona un ejemplo de registro de ProgID para una extensión de archivo (. *ext*).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 El ProgID especificado como el valor predeterminado para la extensión de archivo es el controlador de archivo predeterminado. Si modifica el ProgID de una extensión de archivo que se incluye con una versión anterior de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o que pueda hacerse cargo de otras aplicaciones, debe registrar el `OpenWithProgids` de clave para la extensión de archivo y especificar el nuevo ProgID de la lista junto con el ProgID anteriores que se admiten. Por ejemplo:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 Si la antigua ProgID tiene verbos asociados a él, estos verbos también aparecerá bajo **abrir con** *Product Name* en el menú contextual.  
  
## <a name="see-also"></a>Vea también  
 [Acerca de las extensiones de nombre de archivo](../extensibility/about-file-name-extensions.md)   
 [Registro de verbos para extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md)