---
title: Especificar controladores de archivos para las extensiones de nombre de archivo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af195aea09c91696843c6be42c20053bb8c095a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699751"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Especificación de identificadores de archivo para extensiones de nombre de archivo
Hay varias maneras de determinar la aplicación que controla un archivo que tiene una extensión de archivo determinada. Los verbos OpenWithList y OpenWithProgids son dos maneras de especificar controladores de archivo en la entrada del registro para la extensión de archivo.

## <a name="openwithlist-verb"></a>OpenWithList verbo)
 Al hacer clic con el botón secundario en un archivo en el explorador de Windows, verá el comando **abrir** . Si hay más de un producto asociado a una extensión, verá un submenú **abrir con** .

 Puede registrar distintas aplicaciones para abrir una extensión mediante el establecimiento de la clave OpenWithList para la extensión de archivo en HKEY_CLASSES_ROOT. Las aplicaciones que aparecen bajo esta clave para una extensión de archivo aparecen en el encabezado **Programas recomendados** del cuadro de diálogo **abrir con** . En el ejemplo siguiente se muestran las aplicaciones registradas para abrir la extensión de archivo. vcproj.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Las claves que especifican aplicaciones son de la lista en HKEY_CLASSES_ROOT \Applications.

 Al agregar una clave OpenWithList, se declara que la aplicación admite una extensión de archivo incluso si otra aplicación toma posesión de la extensión. Puede tratarse de una versión futura de la aplicación o de otra aplicación.

## <a name="openwithprogids"></a>OpenWithProgIDs
 Los identificadores de programación (ProgID) son versiones descriptivas de ClassID que identifican una versión de una aplicación o un objeto COM. Cada objeto cocreatable debe tener su propio ProgID. Por ejemplo, VisualStudio. DTE. 7.1 inicia Visual Studio .NET 2003 mientras que se inicia VisualStudio. DTE. 10.0 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Como propietario de un tipo de proyecto o de un tipo de elemento de proyecto, debe crear un ProgID específico de la versión para la extensión de archivo. Estos ProgID pueden ser redundantes en que más de un ProgID puede iniciar la misma aplicación. Para obtener más información, vea [registrar verbos para las extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md).

 Utilice la siguiente Convención de nomenclatura para los identificadores de archivo con versión para evitar la duplicación con el registro de otros proveedores:

|Extensión de archivo|ProgID con versión|
|--------------------|----------------------|
|. Extension|NombreDeProducto. extensión. propiedad versionmajor. versionMinor|

 Puede registrar diferentes aplicaciones que pueden abrir una extensión de archivo determinada agregando los ProgID con versión como valores a la \\ *\<extension>* clave HKEY_CLASSES_ROOT \OpenWithProgids. Esta clave del registro contiene una lista de ProgID alternativos asociados a la extensión de archivo. Las aplicaciones asociadas a los ProgID enumerados aparecen en el submenú **abrir con**el_nombre del producto_ . Si se especifica la misma aplicación en las `OpenWithList` claves y `OpenWithProgids` , el sistema operativo combina los duplicados.

> [!NOTE]
> La `OpenWithProgids` clave solo se admite en Windows XP. Dado que otros sistemas operativos omiten esta clave, no la use como único registro para los controladores de archivos. Use esta clave para proporcionar una mejor experiencia de usuario en Windows XP.

 Agregue los ProgID deseados como valores del tipo REG_NONE. El código siguiente proporciona un ejemplo de registro de los ProgID para una extensión de archivo (.* EXT*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 El identificador de programa (ProgID) especificado como valor predeterminado para la extensión de archivo es el controlador de archivos predeterminado. Si modifica el ID. de programa de una extensión de archivo que se incluye con una versión anterior de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o que otras aplicaciones pueden tomar, debe registrar la `OpenWithProgids` clave de la extensión de archivo y especificar el nuevo ProgID en la lista junto con los identificadores de programa antiguos que admita. Por ejemplo:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Si el ProgID antiguo tiene verbos asociados, estos verbos también aparecerán en **abrir con** el *nombre del producto* en el menú contextual.

## <a name="see-also"></a>Vea también
- [Acerca de las extensiones de nombre de archivo](../extensibility/about-file-name-extensions.md)
- [Registro de verbos para extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md)
