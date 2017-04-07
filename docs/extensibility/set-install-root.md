---
title: "Instalación fuera de la carpeta de extensiones con VSIX v3 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
caps.latest.revision: 1
author: gregvanl
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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 6d87c86d0a7793f661c6a3b28e95340f3a28c616
ms.lasthandoff: 03/07/2017

---
# <a name="installing-outside-the-extensions-folder"></a>Instalación fuera de la carpeta de extensiones

A partir de Visual Studio de 2017 y VSIX v3 (versión 3), ahora existe compatibilidad para la instalación de los activos de extensión fuera de la carpeta de extensiones. Actualmente, se habilitan las siguientes ubicaciones como ubicaciones de instalación válida (donde [installdir] está asignada al directorio de instalación de la instancia de Visual Studio):

* \Common7\IDE\PublicAssemblies [installdir]
* \Common7\IDE\ReferenceAssemblies [installdir]
* \MSBuild [installdir]
* \Schemas [installdir]
* \Licenses [installdir]
* \RemoteDebugger [installdir]
* \VSTargets [installdir]

>**Nota:** el formato VSIX no permiten instalar fuera de la estructura de carpeta de instalación de VS.

Para admitir la instalación de estos directorios, la extensión VSIX debe instalarse "por instancia por equipo". Esto se puede habilitar activando la casilla "todos los usuarios" en el diseñador extension.vsixmanifest:

![Compruebe todos los usuarios](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Cómo establecer el InstallRoot

Para establecer los directorios de instalación, puede usar el **propiedades** ventana de Visual Studio. Por ejemplo, puede establecer el `InstallRoot` propiedad de una referencia de proyecto a una de las ubicaciones anteriores:

![propiedades de la raíz de instalación](media/install-root-properties.png)

Esto agregará algunos metadatos correspondiente `ProjectReference` propiedad dentro de archivo .csproj del proyecto VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**Nota:** puede editar el archivo .csproj directamente, si lo prefiere.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Cómo establecer una subruta de acceso bajo el InstallRoot

Si desea instalar en una subruta de acceso bajo el `InstallRoot`, puede hacerlo estableciendo la `VsixSubPath` propiedad igual que el `InstallRoot` propiedad. Por ejemplo, digamos que queremos salida de nuestra referencia proyecto para instalar en ' [installdir]\MSBuild\MyCompany\MySDK\1.0'. Podemos hacer esto fácilmente con el Diseñador de la propiedad:

![subruta de conjunto](media/set-subpath.png)

Los cambios correspondientes de .csproj tendrá este aspecto:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Información adicional

Aplicarán los cambios de propiedad diseñador a algo más que las referencias de proyecto; puede establecer el `InstallRoot` metadatos para los elementos dentro de su proyecto (con los mismos métodos que se ha descrito anteriormente).

