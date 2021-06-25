---
title: Especificar controladores de archivos para extensiones de nombre de archivo | Microsoft Docs
description: Obtenga información sobre cómo determinar qué aplicación controla una extensión de archivo en Visual Studio SDK mediante OpenWithList y OpenWithProgids.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ab370b4be8c12ad0df0c4822bcc7b487fb4aa21
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899451"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Especificación de identificadores de archivo para extensiones de nombre de archivo
Hay varias maneras de determinar la aplicación que controla un archivo que tiene una extensión de archivo determinada. Los verbos OpenWithList y OpenWithProgids son dos maneras de especificar controladores de archivos en la entrada del Registro para la extensión de archivo.

## <a name="openwithlist-verb"></a>Verbo OpenWithList
 Al hacer clic con el botón derecho en un Explorador de Windows, verá el **comando** Abrir. Si hay más de un producto asociado a una extensión, verá un **submenú Abrir** con.

 Puede registrar diferentes aplicaciones para abrir una extensión estableciendo la clave OpenWithList para la extensión de archivo en HKEY_CLASSES_ROOT. Las aplicaciones enumeradas bajo esta clave para una extensión de archivo aparecen en el **encabezado Programas recomendados** del **cuadro de diálogo** Abrir con . En el ejemplo siguiente se muestran las aplicaciones registradas para abrir la extensión de archivo .vcproj.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> Las claves que especifican las aplicaciones son de la lista en HKEY_CLASSES_ROOT\Applications.

 Al agregar una clave OpenWithList, se declara que la aplicación admite una extensión de archivo incluso si otra aplicación toma posesión de la extensión. Podría ser una versión futura de la aplicación u otra aplicación.

## <a name="openwithprogids"></a>OpenWithProgIDs
 Los identificadores de programación (ProgID) son versiones fáciles de los ClassID que identifican una versión de una aplicación u objeto COM. Cada objeto que se puede crear de forma cogenerable debe tener su propio ProgID. Por ejemplo, VisualStudio.DTE.7.1 se inicia Visual Studio .NET 2003, mientras que VisualStudio.DTE.10.0 inicia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Como propietario de un tipo de proyecto o de un tipo de elemento de proyecto, debe crear un ProgID específico de la versión para la extensión de archivo. Estos ProgID pueden ser redundantes, ya que más de un ProgID puede iniciar la misma aplicación. Para obtener más información, [vea Registrar verbos para extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md).

 Use la siguiente convención de nomenclatura para los ProgID de archivos con versiones para evitar la duplicación con el registro de otros proveedores:

|Extensión de archivo|ProgID con versión|
|--------------------|----------------------|
|.extension|Productname. extension.versionMajor.versionMinor|

 Puede registrar diferentes aplicaciones que puedan abrir una extensión de archivo determinada agregando progID con versiones como valores a la clave \\ *\<extension>* HKEY_CLASSES_ROOT \OpenWithProgids. Esta clave del Registro contiene una lista de progID alternativos asociados a la extensión de archivo. Las aplicaciones asociadas a los ProgID enumerados aparecen en el **submenú Abrir con** nombre _de_ producto. Si se especifica la misma aplicación en las claves `OpenWithList` y , el sistema operativo combina los `OpenWithProgids` duplicados.

> [!NOTE]
> La `OpenWithProgids` clave solo se admite en Windows XP. Dado que otros sistemas operativos omiten esta clave, no la use como único registro para los controladores de archivos. Use esta clave para proporcionar una mejor experiencia de usuario en Windows XP.

 Agregue los ProgID deseados como valores del tipo REG_NONE. El código siguiente proporciona un ejemplo de registro de ProgID para una extensión de archivo (.*ext*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 El ProgID especificado como valor predeterminado para la extensión de archivo es el controlador de archivos predeterminado. Si modifica el ProgID de una extensión de archivo que se incluye con una versión anterior de o que otras aplicaciones pueden tomar el control, debe registrar la clave de la extensión de archivo y especificar el nuevo ProgID en la lista junto con los [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] `OpenWithProgids` progID antiguos que admita. Por ejemplo:

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 Si el ProgID anterior tiene verbos asociados, estos verbos también aparecerán en **Abrir** con nombre de producto *en* el menú contextual.

## <a name="see-also"></a>Consulta también
- [Acerca de las extensiones de nombre de archivo](../extensibility/about-file-name-extensions.md)
- [Registro de verbos para extensiones de nombre de archivo](../extensibility/registering-verbs-for-file-name-extensions.md)
