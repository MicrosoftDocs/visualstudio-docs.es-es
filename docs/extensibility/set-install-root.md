---
title: Instalar fuera de la carpeta de extensiones con VSIX v3 | Documentos de Microsoft
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1b604a70c44b6fd25888ee5419efbb95f95a0a4a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="installing-outside-the-extensions-folder"></a>Instalar fuera de la carpeta de extensiones

A partir de Visual Studio de 2017 y VSIX v3 (versión 3), ahora existe compatibilidad para la instalación de activos de extensión fuera de la carpeta de extensiones. Actualmente, se habilitan las siguientes ubicaciones como ubicaciones de instalación válida (donde [INSTALLDIR] se asigna al directorio de instalación de la instancia de Visual Studio):

* \MSBuild [INSTALLDIR]
* \Xml\Schemas [INSTALLDIR]
* \Common7\IDE\PublicAssemblies [INSTALLDIR]
* \Licenses [INSTALLDIR]
* \Common7\IDE\ReferenceAssemblies [INSTALLDIR]
* \Common7\IDE\RemoteDebugger [INSTALLDIR]
* \Common7\IDE\VC\VCTargets [INSTALLDIR]

>**Nota:** el formato VSIX no permiten instalar fuera de la estructura de carpetas de instalación de VS.

Para admitir la instalación de estos directorios, la extensión VSIX debe instalarse "por instancia por equipo". Esto se puede habilitar activando la casilla de verificación "todos los usuarios" en el diseñador extension.vsixmanifest:

![Compruebe todos los usuarios](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Cómo establecer la InstallRoot

Para establecer los directorios de instalación, puede usar el **propiedades** ventana de Visual Studio. Por ejemplo, puede establecer el `InstallRoot` propiedad de una referencia de proyecto a una de las ubicaciones anteriores:

![instalar propiedades raíz](media/install-root-properties.png)

Esto agregará algunos metadatos a los correspondientes `ProjectReference` propiedad dentro del archivo .csproj del proyecto VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**Nota:** se puede editar el archivo .csproj directamente, si lo prefiere.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Cómo establecer una subruta de acceso bajo el InstallRoot

Si desea instalar a una subruta de acceso bajo la `InstallRoot`, puede hacerlo estableciendo la `VsixSubPath` al igual que la propiedad la `InstallRoot` propiedad. Por ejemplo, supongamos que queremos salida de la referencia de nuestro proyecto para instalar en ' [INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0'. Podemos hacerlo fácilmente con el Diseñador de la propiedad:

![subruta de conjunto](media/set-subpath.png)

Los cambios correspondientes de .csproj tendrá un aspecto similar al siguiente:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Información adicional

Los cambios de diseñador de propiedad se aplican a algo más que las referencias de proyecto; puede establecer el `InstallRoot` metadatos para los elementos dentro de su proyecto (con los mismos métodos que se ha descrito anteriormente).
