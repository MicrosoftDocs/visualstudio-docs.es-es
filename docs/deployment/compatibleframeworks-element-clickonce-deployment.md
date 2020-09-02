---
title: '&lt;&gt;elemento compatibleFrameworks (implementación ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99db3d51414197df469aaa2eabe97e0967c31b05
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "66746040"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;&gt;elemento compatibleFrameworks (implementación ClickOnce)
Identifica las versiones de .NET Framework en las que se puede instalar y ejecutar esta aplicación.

> [!NOTE]
> [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) no admite el `compatibleFrameworks` elemento cuando se guarda un manifiesto de aplicación que ya se ha firmado con un certificado mediante [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). En su lugar, debe usar [*Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="syntax"></a>Sintaxis

```xml
<compatibleFrameworks
      SupportUrl> 
   <framework
      targetVersion
      profile
      supportedRuntime
   /> 
</ compatibleFrameworks>
```

## <a name="elements-and-attributes"></a>Elementos y atributos
 El `compatibleFrameworks` elemento es necesario para los manifiestos de implementación que tienen como destino el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tiempo de ejecución proporcionado por .NET Framework 4 o una versión posterior. El `compatibleFrameworks` elemento contiene uno o más `framework` elementos que especifican las versiones .NET Framework en las que se puede ejecutar esta aplicación. El [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tiempo de ejecución ejecutará la aplicación en la primera disponible `framework` en esta lista.

 En la tabla siguiente se muestra el atributo que el `compatibleFrameworks` elemento admite.

|Atributo|Descripción|
|---------------|-----------------|
|`S` `upportUrl`|Opcional. Especifica una dirección URL en la que se puede descargar la versión de .NET Framework compatible preferida.|

## <a name="framework"></a>marco de trabajo
 Necesario. En la tabla siguiente se enumeran los atributos que `framework` admite el elemento.

|Atributo|Descripción|
|---------------|-----------------|
|`targetVersion`|Necesario. Especifica el número de versión del .NET Framework de destino.|
|`profile`|Necesario. Especifica el perfil de la .NET Framework de destino.|
|`supportedRuntime`|Necesario. Especifica el número de versión del tiempo de ejecución asociado a la .NET Framework de destino.|

## <a name="remarks"></a>Observaciones

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra un `compatibleFrameworks` elemento en un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de implementación. Esta implementación se puede ejecutar en el [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] . También se puede ejecutar en el .NET Framework 4 porque es un superconjunto de [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] .

```xml
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
  <framework
      targetVersion="4.0"
      profile="Client"
      supportedRuntime="4.0.30319" />
</compatibleFrameworks>
```

## <a name="see-also"></a>Consulte también
- [Manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md)