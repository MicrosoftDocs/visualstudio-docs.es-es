---
title: Referencia de la API no administrada de ClickOnce | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "6"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: cplusplus
ms.openlocfilehash: 392ada2288adcc229834f617c2f6284bb2e7ed0f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="clickonce-unmanaged-api-reference"></a>Referencia de la API no administrada de ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]API públicas no administradas de dfshim.dll.  
  
## <a name="cleanonlineappcache"></a>CleanOnlineAppCache  
 Limpia o desinstala todas las aplicaciones en línea desde el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] caché de la aplicación.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un HRESULT que representa el error. Si se produce una excepción administrada, devuelve 0 x 80020009 (DISP_E_EXCEPTION).  
  
### <a name="remarks"></a>Comentarios  
 Al llamar a CleanOnlineAppCache se iniciará el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] servicio si no se está ejecutando.  
  
## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest aplicación  
 Recupera información sobre la implementación de la dirección URL del manifiesto y la activación.  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|Tipo|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|Un puntero a la `ActivationURL`.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|Un puntero a la `PathToDeploymentManifest`.|LPCWSTR|  
|`pwzApplicationIdentity`|Un puntero a un búfer para recibir una cadena terminada en NULL que especifica la identidad de aplicación completo devuelve.|LPWSTR|  
|`pdwIdentityBufferLength`|Un puntero a un DWORD que es la longitud de la `pwzApplicationIdentity` búfer, en número de WCHAR. Esto incluye el espacio para el carácter nulo de terminación.|LPDWORD|  
|`pwzProcessorArchitecture`|Un puntero a un búfer para recibir una cadena terminada en NULL que especifica la arquitectura del procesador de la implementación de aplicaciones, desde el manifiesto.|LPWSTR|  
|`pdwArchitectureBufferLength`|Un puntero a un DWORD que es la longitud de la `pwzProcessorArchitecture` búfer, en número de WCHAR.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Un puntero a un búfer para recibir una cadena terminada en NULL que especifica el código base del manifiesto de aplicación, en el manifiesto.|LPWSTR|  
|`pdwCodebaseBufferLength`|Un puntero a un DWORD que es la longitud de la `pwzApplicationManifestCodebase` búfer, en número de WCHAR.|LPDWORD|  
|`pwzDeploymentProvider`|Un puntero a un búfer para recibir una cadena terminada en NULL que especifica el proveedor de implementación del manifiesto, si está presente. En caso contrario, se devuelve una cadena vacía.|LPWSTR|  
|`pdwProviderBufferLength`|Un puntero a un DWORD que es la longitud de la `pwzProviderBufferLength`.|LPDWORD|  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un HRESULT que representa el error. Devuelve HRESULTFROMWIN32 (ERROR_INSUFFICIENT_BUFFER) si un búfer es demasiado pequeño.  
  
### <a name="remarks"></a>Comentarios  
 Punteros no deben ser nulos. `pcwzActivationUrl`y `pcwzPathToDeploymentManifest` no debe estar vacío.  
  
 Es responsabilidad del llamador para limpiar la URL de activación. Por ejemplo, la adición de escape caracteres donde se necesitan o quitar la cadena de consulta.  
  
 Es responsabilidad del llamador para limitar la longitud de entrada. Por ejemplo, la longitud máxima de dirección URL es 2KB.  
  
## <a name="launchapplication"></a>LaunchApplication  
 Inicia o instala una aplicación mediante una dirección URL de la implementación.  
  
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