---
title: Tarea SignFile | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 496017f386e731e553bfce237bd1d2eabea46f49
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976453"
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
|`SigningTarget`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica los archivos que se van a firmar con el certificado.|
|`TimestampUrl`|Parámetro `String` opcional.<br /><br /> Especifica la dirección URL del servidor con marca de tiempo.|
|`TargetFrameworkVersion`|La versión de .NET Framework la que se utiliza para el destino.|

## <a name="remarks"></a>Comentarios

 Además de los parámetros enumerados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [Task Base (Clase)](../msbuild/task-base-class.md).

## <a name="example"></a>Ejemplo

 En el ejemplo siguiente se utiliza la tarea `SignFile` para firmar los archivos especificados en la colección de elementos `FilesToSign` con el certificado definido por la propiedad `Certificate`.

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