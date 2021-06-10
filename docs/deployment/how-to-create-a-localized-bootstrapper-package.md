---
title: Crear un paquete de programa previo localizado | Microsoft Docs
description: Aprenda a crear versiones localizadas del paquete de programa previo en ClickOnce mediante la creación de dos archivos más para cada configuración regional.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2a9d1fc91dcb385a9250dde3adb47c0d9553147f
ms.sourcegitcommit: 6aa55db5e1fe19d4d17886e0bfe140dbd186f8ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2021
ms.locfileid: "111877720"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Cómo: Crear un paquete de arranque localizado
Después de crear un paquete de programa previo, puede crear versiones localizadas del paquete de programa previo mediante la creación de dos archivos más para cada configuración regional: un archivo de términos de licencia de software (como *eula.rtf)* y un manifiesto de paquete *(package.xml*).

 De forma predeterminada, Visual Studio 2010 incluye paquetes de programa previo localizados solo para .NET Framework 4, .NET Framework 4 Client Profile, F# Runtime 2.0 y F# Runtime 4.0. Siga tres pasos para crear paquetes localizados para otros programas previos.

1. Cree una carpeta con el nombre de la configuración regional en \Archivos de *programa (x86)\Microsoft SDKs\ClickOnce Bootstrapper\Packages \\ \<BootstrapperPackageName>*.

2. Cree un archivo que contenga los términos de licencia de software para el paquete de programa previo y colóquelo en la nueva carpeta.

3. Cree un manifiesto de paquete con el nombre *package.xml*, actualice las cadenas y la referencia cultural, y coloque el archivo en la carpeta nueva. Si ya ha creado un programa previo de Visual Studio en el idioma de destino, puede copiar el archivo *package.xml* de Visual Studio y modificarlo en este paso.

> [!NOTE]
> Si usa un proyecto de instalación para implementar aplicaciones, puede localizar la aplicación cambiando la propiedad **Localización**.

 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-localized-bootstrapper-package"></a>Para crear un paquete de programa previo localizado

1. Cree una carpeta con el nombre de la configuración regional.

     En equipos de 32 bits, cree la carpeta en la carpeta *\Archivos \\ \<BootstrapperPackageName> \\ de programa\Microsoft SDKs\ClickOnce Bootstrapper\Packages.*

     En equipos de 64 bits, cree la carpeta en la carpeta \Archivos de programa *(x86)\Microsoft SDKs\ClickOnce Bootstrapper\Packages. \\ \<BootstrapperPackageName> \\*

     La tabla siguiente muestra los nombres de carpeta que puede usar para cada configuración regional.

    |Locale|Nombre de carpeta|
    |------------|-----------------|
    |Chino (simplificado)|zh-Hans|
    |Chino (tradicional)|zh-Hant|
    |Checo|cs|
    |Alemán|de|
    |Inglés|en|
    |Español|es|
    |Francés|fr|
    |Italiano|it|
    |Coreano|ko|
    |Japonés|ja|
    |Polaco|pl|
    |Portugués (Brasil)|pt-BR|
    |Ruso|ru|
    |Turco|tr|

2. Cree un archivo que contenga los términos de licencia de software para el paquete de programa previo y colóquelo en la nueva carpeta.

3. Cree un manifiesto del paquete con el nombre *package.xml* y colóquelo en la nueva carpeta. Para obtener más información, [vea Cómo: Crear un manifiesto de paquete.](../deployment/how-to-create-a-package-manifest.md)

4. Actualice la sección `<Strings>` del manifiesto del paquete para que las cadenas estén en el idioma correcto de la configuración regional.

5. Cambie el valor de `<String Name="Culture">` para que coincida con el nombre de la carpeta.

6. Guarde el archivo *package.xml*.

### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Para crear un paquete de programa previo para .NET Framework 3.5 Service Pack 1 localizado en francés

1. Cree una carpeta denominada *fr*. El nombre de la carpeta debe coincidir con el nombre de la configuración regional.

     En equipos de 32 bits, cree la carpeta en la carpeta \Archivos de *programa\Microsoft \\ SDKs\ClickOnce Bootstrapper\Packages\DotNetFX35SP1.*

     En equipos de 64 bits, cree la carpeta en la carpeta \Archivos de programa *(x86)\Microsoft SDKs\ClickOnce Bootstrapper\Packages\DotNetFX35SP1. \\*

2. Coloque una versión localizada de los términos de licencia de software en la carpeta *fr*.

3. Copie el archivo \Archivos de *programa (x86)\Microsoft SDKs\ClickOnce Bootstrapper\Packages\DotNetFX35SP1\en\package.xml* en la carpeta *fr* y abra el archivo en el Diseñador XML.

4. Actualice la sección `<Strings>` del manifiesto del paquete para que las cadenas de error estén en francés.

5. Cambie el valor de `<String Name="Culture">` a *fr*.

6. Guarde el archivo *package.xml*.

>[!NOTE]
> A partir de Visual Studio paquetes de arranque de la versión update 7 de 2019 también se detectarán en la ruta de acceso *<VS Install Path> \MSBuild\Microsoft\VisualStudio\BootstrapperPackages*.

## <a name="see-also"></a>Vea también
- [Creación de paquetes de programa previo](../deployment/creating-bootstrapper-packages.md)
- [Requisitos previos para la implementación de aplicaciones](../deployment/application-deployment-prerequisites.md)
- [Cómo: Crear un manifiesto de paquete](../deployment/how-to-create-a-package-manifest.md)