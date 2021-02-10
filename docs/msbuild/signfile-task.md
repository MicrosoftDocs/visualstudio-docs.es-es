---
title: Tarea SignFile | Microsoft Docs
description: Obtenga información sobre cómo MSBuild usa la tarea SignFile para firmar el archivo especificado con el certificado especificado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SignFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, SignFile task
- SignFile task [MSBuild]
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9eef76a3757d9a2ff8ece5da5c18968097bd7618
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878167"
---
# <a name="signfile-task"></a>SignFile (tarea)

Firma un archivo determinado con el certificado especificado.

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea `SignFile` .

 Tenga en cuenta que los certificados SHA-256 solo están permitidos en equipos que tienen .NET 4.5 y versiones posteriores.

> [!WARNING]
> A partir de Visual Studio 2013 Update 3, esta tarea tiene una signatura nueva que le permite especificar la versión del marco de trabajo de destino para el archivo. Le recomendamos utilizar la nueva firma, siempre que sea posible, ya que el proceso de MSBuild solo utiliza hashes SHA-256 cuando el marco de trabajo de destino es .NET 4.5 o una versión posterior. Si el marco de trabajo destino es .NET 4.0 o una versión anterior, no se utilizará el hash SHA-256.

|Parámetro|Descripción|
|---------------|-----------------|
|`CertificateThumbprint`|Parámetro `String` requerido.<br /><br /> Especifica el certificado que se va a usar en la signatura. Este certificado debe estar ubicado en el almacén personal del usuario actual.|
|`SigningTarget`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica los archivos (de tipo .exe o .dll) que se van a firmar con el certificado.|
|`TimestampUrl`|Parámetro `String` opcional.<br /><br /> Especifica la dirección URL del servidor con marca de tiempo.|
|`TargetFrameworkVersion`|La versión de .NET Framework la que se utiliza para el destino.|

## <a name="remarks"></a>Comentarios

 Además de los parámetros enumerados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [Task Base (Clase)](../msbuild/task-base-class.md).

## <a name="example"></a>Ejemplo

 En el ejemplo siguiente se utiliza la tarea `SignFile` para firmar los archivos especificados en la colección de elementos `FilesToSign` con el certificado definido por la propiedad `CertificateThumbprint`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <FileToSign Include="File.exe" />
    </ItemGroup>
    <PropertyGroup>
        <Certificate>Cert.cer</Certificate>
    </PropertyGroup>
    <Target Name="Sign">
        <SignFile
            CertificateThumbprint="$(CertificateThumbprint)"
            SigningTarget="@(FileToSign)"
            TargetFrameworkVersion="v4.5" />
    </Target>
</Project>
```

> [!NOTE]
> La huella digital del certificado es el hash SHA-1 del certificado. Para más información, consulte [Obtain the SHA-1 hash of a trusted root CA certificate](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc733076\(v\=ws.10\)) (Obtener el hash SHA-1 de un certificado de entidad de certificación raíz de confianza). Si copia y pega la huella digital de los detalles del certificado, asegúrese de que no incluye los caracteres invisibles (3F) adicionales, ya que esto puede impedir que `SignFile` encuentre el certificado.

## <a name="see-also"></a>Vea también

- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
- [Tareas](../msbuild/msbuild-tasks.md)