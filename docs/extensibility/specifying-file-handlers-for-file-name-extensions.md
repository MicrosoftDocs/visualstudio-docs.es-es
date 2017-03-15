---
title: "Especificar los controladores de archivo para las extensiones de nombre de archivo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "extensiones de archivo, especificar controladores de archivo"
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Especificar los controladores de archivo para las extensiones de nombre de archivo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Hay varias maneras de determinar la aplicación que administra un archivo que tiene una extensión de archivo en particular. Los verbos OpenWithList y OpenWithProgids son dos formas de especificar controladores de archivo en la entrada del registro para la extensión de archivo.  
  
## Verbo OpenWithList  
 Cuando hace clic en un archivo en el Explorador de Windows, verá el **abiertos** comando. Si más de un producto está asociado a una extensión, verá un **Abrir con** submenú.  
  
 Puede registrar las aplicaciones diferentes para abrir una extensión estableciendo la clave de OpenWithList para la extensión de archivo en HKEY\_CLASSES\_ROOT. Las aplicaciones enumeradas en esta clave para una extensión de archivo aparecen en el **recomienda programas** encabezado en el **Abrir con** cuadro de diálogo. El ejemplo siguiente muestra las aplicaciones registradas para abrir la extensión de archivo .vcproj.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  Las claves de la especificación de las aplicaciones están en la lista HKEY\_CLASSES\_ROOT\\Applications.  
  
 Al agregar una clave de OpenWithList, declare que la aplicación admite una extensión de archivo, incluso si otra aplicación toma posesión de la extensión. Podría tratarse de una versión futura de la aplicación u otra aplicación.  
  
## OpenWithProgIDs  
 Identificadores de programación \(ProgID\) son versiones descriptivas de ClassID que identifica una versión de una aplicación o un objeto COM. Cada objeto de conjunto que se puede crear debe tener su propio ProgID. Por ejemplo, VisualStudio.DTE.7.1 inicia Visual Studio .NET 2003 mientras se inicia VisualStudio.DTE.10.0 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Como propietario de un tipo de proyecto o el tipo de elemento de proyecto, debe crear un ProgID específico de la versión para la extensión de archivo. Estos identificadores de programa pueden ser redundantes en que más de un ProgID puede iniciar la misma aplicación. Para obtener más información, consulta [Registrar los verbos de extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md).  
  
 Utilice la siguiente convención de nomenclatura para archivo versión ProgID para evitar la duplicación con el registro de otros proveedores:  
  
|Extensión de archivo|Con versiones ProgID|  
|--------------------------|--------------------------|  
|.Extension|ProductName. extension.versionMajor.versionMinor|  
  
 Puede registrar aplicaciones diferentes que pueden abrir una extensión de archivo determinada mediante la adición de ProgID con versiones como valores para el HKEY\_CLASSES\_ROOT\\*\< extensión \>*\\OpenWithProgids clave. Esta clave del registro contiene una lista de ProgID alternativos asociados a la extensión de archivo. Las aplicaciones asociadas con la lista ProgID aparecen en la **Abrir con***Product Name* submenú. Si se especifica la misma aplicación tanto en el `OpenWithList` y `OpenWithProgids` las claves, el sistema operativo combina los duplicados.  
  
> [!NOTE]
>  El `OpenWithProgids` clave solo se admite en Windows XP. Dado que otros sistemas operativos omitir esta clave, no usarlo como el registro sólo para controladores de archivo. Use esta clave para ofrecer una mejor experiencia de usuario en Windows XP.  
  
 Agregue los ProgID deseados como valores de tipo REG\_NONE. El código siguiente proporciona un ejemplo del registro ProgID para una extensión de archivo \(.*ext*\).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 El ProgID especificado como el valor predeterminado para la extensión de archivo es el controlador de archivo predeterminado. Si modifica el ProgID para una extensión de archivo que se incluye con una versión anterior de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o que pueda hacerse cargo de otras aplicaciones, debe registrar el `OpenWithProgids` de clave para la extensión de archivo y especifique el nuevo ProgID en la lista junto con los ProgID antiguas que admite. Por ejemplo:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 Si la antigua ProgID tiene verbos asociados, estos verbos también aparecerá bajo **Abrir con** *Product Name* en el menú contextual.  
  
## Vea también  
 [Acerca de las extensiones de nombre de archivo](../extensibility/about-file-name-extensions.md)   
 [Registrar los verbos de extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md)