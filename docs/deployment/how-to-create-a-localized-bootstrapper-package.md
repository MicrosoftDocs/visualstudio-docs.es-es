---
title: 'Cómo: crear un paquete de arranque localizados | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: d9c7190e12190ac35ce906d8dc61f113ae01481c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Cómo: Crear un paquete de arranque localizado
Después de crear un paquete de arranque, puede crear versiones localizadas del paquete del programa previo mediante la creación de más de dos archivos para cada configuración regional: archivo (por ejemplo, un eula.rtf) y un manifiesto del paquete (package.xml) de los términos de una licencia de software.  
  
 De forma predeterminada, Visual Studio 2010 incluye paquetes de programa previo localizados solo para .NET Framework 4, .NET Framework 4 Client Profile, F# Runtime 2.0 y F# Runtime 4.0. Siga tres pasos para crear paquetes localizados para otros programas previos.  
  
1.  Cree una carpeta con el nombre de la configuración regional en \Program SDKs\Windows\v7.0A\Bootstrapper\Packages\\*Nombrepaqueteprogramaprevio*.  
  
2.  Cree un archivo que contenga los términos de licencia de software para el paquete de programa previo y colóquelo en la nueva carpeta.  
  
3.  Cree un manifiesto del paquete llamado package.xml, actualice las cadenas y la referencia cultural, y coloque el archivo en la nueva carpeta. Si ya ha creado un programa previo de Visual Studio en el idioma de destino, puede copiar el archivo package.xml de Visual Studio y modificarlo en este paso.  
  
> [!NOTE]
>  Si usas un proyecto de instalación para implementar aplicaciones, puede localizar la aplicación cambiando la **localización** propiedad.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-localized-bootstrapper-package"></a>Para crear un paquete de programa previo localizado  
  
1.  Cree una carpeta con el nombre de la configuración regional.  
  
     En equipos de 32 bits, cree la carpeta en la \Program SDKs\Windows\v7.0A\Bootstrapper\Packages\\*Nombrepaqueteprogramaprevio*\ carpeta.  
  
     En los equipos de 64 bits, cree la carpeta en la \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages programa (86) \Program\\*Nombrepaqueteprogramaprevio*\ carpeta.  
  
     La tabla siguiente muestra los nombres de carpeta que puede usar para cada configuración regional.  
  
    |Configuración regional|Nombre de carpeta|  
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
  
2.  Cree un archivo que contenga los términos de licencia de software para el paquete de programa previo y colóquelo en la nueva carpeta.  
  
3.  Cree un manifiesto del paquete con el nombre package.xml y colóquelo en la nueva carpeta. Para obtener más información, consulte [Cómo: crear un manifiesto del paquete](../deployment/how-to-create-a-package-manifest.md).  
  
4.  Actualice la sección `<Strings>` del manifiesto del paquete para que las cadenas estén en el idioma correcto de la configuración regional.  
  
5.  Cambie el valor de `<String Name="Culture">` para que coincida con el nombre de la carpeta.  
  
6.  Guarde el archivo package.xml.  
  
### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Para crear un paquete de programa previo para .NET Framework 3.5 Service Pack 1 localizado en francés  
  
1.  Cree una carpeta con el nombre fr. El nombre de la carpeta debe coincidir con el nombre de la configuración regional.  
  
     En equipos de 32 bits, cree la carpeta en la carpeta \Archivos de programa\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\.  
  
     En equipos de 64 bits, cree la carpeta en la carpeta \Archivos de programa (86)\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\.  
  
2.  Coloque una versión localizada de los términos de licencia de software en la carpeta fr.  
  
3.  Copie el archivo \Archivos de programa (x86)\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml en la carpeta fr y abra el archivo en el Diseñador XML.  
  
4.  Actualice la sección `<Strings>` del manifiesto del paquete para que las cadenas de error estén en francés.  
  
5.  Cambie el valor de `<String Name="Culture">` a fr.  
  
6.  Guarde el archivo package.xml.  
  
## <a name="see-also"></a>Vea también  
 [Crear paquetes de arranque](../deployment/creating-bootstrapper-packages.md)   
 [Requisitos previos para la implementación de aplicaciones](../deployment/application-deployment-prerequisites.md)   
 [Cómo: Crear un manifiesto de paquete](../deployment/how-to-create-a-package-manifest.md)