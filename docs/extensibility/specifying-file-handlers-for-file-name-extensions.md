---
title: Especificación de los controladores de archivos para las extensiones de nombre de archivo ( File Name Extensions) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699751"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Especificación de identificadores de archivo para extensiones de nombre de archivo
Hay varias maneras de determinar la aplicación que maneja un archivo que tiene una extensión de archivo determinada. Los verbos OpenWithList y OpenWithProgids son dos formas de especificar controladores de archivos en la entrada del Registro para la extensión de archivo.

## <a name="openwithlist-verb"></a>OpenWithList Verbo
 Al hacer clic con el botón derecho en un archivo en el Explorador de Windows, verá el comando **Abrir.** Si hay más de un producto asociado a una extensión, verá un submenú **Abrir con.**

 Puede registrar diferentes aplicaciones para abrir una extensión estableciendo la clave OpenWithList para la extensión de archivo en HKEY_CLASSES_ROOT. Las aplicaciones enumeradas bajo esta clave para una extensión de archivo aparecen bajo el encabezado **Programas recomendados** en el cuadro de diálogo **Abrir con.** En el ejemplo siguiente se muestran las aplicaciones registradas para abrir la extensión de archivo .vcproj.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Las claves que especifican las aplicaciones proceden de la lista de HKEY_CLASSES_ROOT.Aplicaciones.

 Al agregar una clave OpenWithList, declara que la aplicación admite una extensión de archivo incluso si otra aplicación toma posesión de la extensión. Podría ser una versión futura de la aplicación u otra aplicación.

## <a name="openwithprogids"></a>OpenWithProgIDs
 Los identificadores de programación (ProgID) son versiones descriptuigénitas de ClassID que identifican una versión de una aplicación u objeto COM. Cada objeto co-creable debe tener su propio ProgID. Por ejemplo, VisualStudio.DTE.7.1 inicia Visual Studio .NET 2003 mientras se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]inicia VisualStudio.DTE.10.0 . Como propietario de un tipo de proyecto o de elemento de proyecto, debe crear un ProgID específico de la versión para la extensión de archivo. Estos ProgID pueden ser redundantes en el que más de un ProgID puede iniciar la misma aplicación. Para obtener más información, consulte [Registro de verbos para extensiones](../extensibility/registering-verbs-for-file-name-extensions.md)de nombre de archivo .

 Utilice la siguiente convención de nomenclatura para los ProgID de archivos versionados para evitar la duplicación con el registro de otros proveedores:

|Extensión de archivo|ProgID versionado|
|--------------------|----------------------|
|.extensión|Productname. extension.versionMajor.versionMinor|

 Puede registrar diferentes aplicaciones que son capaces de abrir una extensión de archivo en\\particular mediante la adición de ProgIDs versionados como valores a la extensión de HKEY_CLASSES_ROOT*\<>* clave OpenWithProgids. Esta clave del Registro contiene una lista de ProgID alternativos asociados con la extensión de archivo. Las aplicaciones asociadas con los ProgID enumerados aparecen en el submenú **Abrir con**nombre_de producto._ Si se especifica la misma `OpenWithList` aplicación `OpenWithProgids` en las claves y, el sistema operativo combina los duplicados.

> [!NOTE]
> La `OpenWithProgids` clave solo se admite en Windows XP. Dado que otros sistemas operativos ignoran esta clave, no la use como el único registro para los controladores de archivos. Utilice esta clave para proporcionar una mejor experiencia de usuario en Windows XP.

 Agregue los ProgIDs deseados como valores del tipo REG_NONE. El código siguiente proporciona un ejemplo de registro de ProgIDs para una extensión de archivo (.* ext*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 El ProgID especificado como valor predeterminado para la extensión de archivo es el controlador de archivos predeterminado. Si modifica el ProgID para una extensión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] archivo que se incluye con una versión `OpenWithProgids` anterior de o que puede ser asumido por otras aplicaciones, debe registrar la clave para la extensión de archivo y especificar el nuevo ProgID en la lista junto con los ProgID antiguos que admite. Por ejemplo:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Si el antiguo ProgID tiene verbos asociados, estos verbos también aparecerán en **Abrir con** nombre *de producto* en el menú contextual.

## <a name="see-also"></a>Vea también
- [Acerca de las extensiones de nombre de archivo](../extensibility/about-file-name-extensions.md)
- [Registro de verbos para extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md)
