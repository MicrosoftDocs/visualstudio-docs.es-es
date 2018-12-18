---
title: Referencia de API no administrada de ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
api_name:
- CleanOnlineAppCache
- GetDeploymentDataFromManifest
- LaunchApplication
api_location:
- dfshim.dll
api_type:
- COM
topic_type:
- apiref
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- LaunchApplication [ClickOnce unmanaged]
- ClickOnce, unmanaged APIs
- CleanOnlineAppCache [ClickOnce unmanaged]
- CleanOnlineAppCacheW interface [ClickOnce unmanaged]
- GetDeploymentDataFromManifest [ClickOnce unmanaged]
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 121b9b3be3c7f942f3ed1d5f7f2600f24d684e2d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39082151"
---
# <a name="clickonce-unmanaged-api-reference"></a>Referencia de API no administrada de ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API públicas no administradas de dfshim.dll.  
  
## <a name="cleanonlineappcache"></a>CleanOnlineAppCache  
 Limpia o desinstala todas las aplicaciones en línea desde el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] caché de la aplicación.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un HRESULT que representa el error. Si se produce una excepción administrada, devuelve 0 x 80020009 (DISP_E_EXCEPTION).  
  
### <a name="remarks"></a>Comentarios  
 Al llamar a CleanOnlineAppCache se iniciará el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] del servicio si aún no se está ejecutando.  
  
## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest  
 Recupera información sobre la implementación de la dirección URL del manifiesto y la activación.  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|Tipo|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|Un puntero a la `ActivationURL`.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|Un puntero a la `PathToDeploymentManifest`.|LPCWSTR|  
|`pwzApplicationIdentity`|Un puntero a un búfer para recibir una cadena terminada en NULL que especifica la identidad de aplicación completo devolver.|LPWSTR|  
|`pdwIdentityBufferLength`|Un puntero a un DWORD que es la longitud de la `pwzApplicationIdentity` búfer, en número de WCHAR. Esto incluye el espacio para el carácter nulo de terminación.|LPDWORD|  
|`pwzProcessorArchitecture`|Un puntero a un búfer para recibir una cadena terminada en NULL que especifica la arquitectura del procesador de la implementación de aplicación, en el manifiesto.|LPWSTR|  
|`pdwArchitectureBufferLength`|Un puntero a un DWORD que es la longitud de la `pwzProcessorArchitecture` búfer, en número de WCHAR.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Un puntero a un búfer para recibir una cadena terminada en NULL que especifica el código base del manifiesto de aplicación, desde el manifiesto.|LPWSTR|  
|`pdwCodebaseBufferLength`|Un puntero a un DWORD que es la longitud de la `pwzApplicationManifestCodebase` búfer, en número de WCHAR.|LPDWORD|  
|`pwzDeploymentProvider`|Un puntero a un búfer para recibir una cadena terminada en NULL que especifica el proveedor de implementación del manifiesto, si está presente. En caso contrario, se devuelve una cadena vacía.|LPWSTR|  
|`pdwProviderBufferLength`|Un puntero a un DWORD que es la longitud de la `pwzProviderBufferLength`.|LPDWORD|  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un HRESULT que representa el error. Devuelve HRESULTFROMWIN32 (ERROR_INSUFFICIENT_BUFFER) si un búfer es demasiado pequeño.  
  
### <a name="remarks"></a>Comentarios  
 Punteros no deben ser nulos. `pcwzActivationUrl` y `pcwzPathToDeploymentManifest` no debe estar vacío.  
  
 Es responsabilidad del llamador para limpiar la URL de activación. Por ejemplo, agregar el escape de caracteres donde son necesarios o eliminación de la cadena de consulta.  
  
 Es responsabilidad del llamador para limitar la longitud de entrada. Por ejemplo, la longitud máxima de dirección URL es 2KB.  
  
## <a name="launchapplication"></a>LaunchApplication  
 Inicia o se instala una aplicación con una dirección URL de la implementación.  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|Tipo|  
|---------------|-----------------|----------|  
|`deploymentUrl`|Un puntero a una cadena terminada en NULL que contiene la dirección URL del manifiesto de implementación.|LPCWSTR|  
|`data`|Reservado para un uso futuro. Debe ser NULL.|LPVOID|  
|`flags`|Reservado para un uso futuro. Debe ser 0.|DWORD|  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un HRESULT que representa el error. Si se produce una excepción administrada, devuelve 0 x 80020009 (DISP_E_EXCEPTION).  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>