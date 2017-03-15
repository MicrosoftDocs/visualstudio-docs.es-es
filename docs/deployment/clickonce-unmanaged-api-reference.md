---
title: "Referencia de la API no administrada de ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "CleanOnlineAppCache [aplicación ClickOnce no administrada]"
  - "CleanOnlineAppCacheW (interfaz) [aplicación ClickOnce no administrada]"
  - "ClickOnce, API no administrada"
  - "GetDeploymentDataFromManifest [aplicación ClickOnce no administrada]"
  - "LaunchApplication [aplicación ClickOnce no administrada]"
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 6
---
# Referencia de la API no administrada de ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

API públicas no administradas de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] de dfshim.dll.  
  
## CleanOnlineAppCache  
 Limpia o desinstala todas las aplicaciones en línea de la memoria caché de aplicación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
### Valor devuelto  
 Si se ejecuta correctamente, devuelve S\_OK; en caso contrario, devuelve un HRESULT que representa el error.  Si se produce una excepción administrada, devuelve 0x80020009 \(DISP\_E\_EXCEPTION\).  
  
### Comentarios  
 Al llamar a CleanOnlineAppCache se iniciará el servicio [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] si aún no se está ejecutando.  
  
## GetDeploymentDataFromManifest  
 Recupera información de implementación del manifiesto y la dirección URL de activación.  
  
### Parámetros  
  
|Parámetro|Descripción|Tipo|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|Puntero a `ActivationURL`.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|Puntero a `PathToDeploymentManifest`.|LPCWSTR|  
|`pwzApplicationIdentity`|Puntero a un búfer para recibir una cadena terminada en NULL que especifica la identidad completa de la aplicación devuelta.|LPWSTR|  
|`pdwIdentityBufferLength`|Puntero a un DWORD que es la longitud del búfer de `pwzApplicationIdentity`, en número de WCHAR.  Se incluye el espacio del carácter de terminación NULL.|LPDWORD|  
|`pwzProcessorArchitecture`|Puntero a un búfer para recibir del manifiesto una cadena terminada en NULL que especifica la arquitectura de procesador de la implementación de aplicaciones.|LPWSTR|  
|`pdwArchitectureBufferLength`|Puntero a un DWORD que es la longitud del búfer de `pwzProcessorArchitecture`, en número de WCHAR.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Puntero a un búfer para recibir del manifiesto una cadena terminada en NULL que especifica el código base del manifiesto de aplicación.|LPWSTR|  
|`pdwCodebaseBufferLength`|Puntero a un DWORD que es la longitud del búfer de `pwzApplicationManifestCodebase`, en número de WCHAR.|LPDWORD|  
|`pwzDeploymentProvider`|Puntero a un búfer para recibir del manifiesto, si existe, una cadena terminada en NULL que especifica el proveedor de implementación.  Si no existe, se devuelve una cadena vacía.|LPWSTR|  
|`pdwProviderBufferLength`|Puntero a un DWORD que es la longitud de `pwzProviderBufferLength`.|LPDWORD|  
  
### Valor devuelto  
 Si se ejecuta correctamente, devuelve S\_OK; en caso contrario, devuelve un HRESULT que representa el error.  Devuelve HRESULTFROMWIN32 \(ERROR\_INSUFFICIENT\_BUFFER\) si un búfer es demasiado pequeño.  
  
### Comentarios  
 Los punteros no deben ser NULL.  `pcwzActivationUrl` y `pcwzPathToDeploymentManifest` no deben estar vacíos.  
  
 Es responsabilidad del llamador limpiar la dirección URL de activación.  Por ejemplo, puede agregar caracteres de escape donde sea necesario o quitar la cadena de consulta.  
  
 Es responsabilidad del llamador limitar la longitud de entrada.  Por ejemplo, la longitud máxima de la dirección URL es 2 KB.  
  
## LaunchApplication  
 Inicia o instala una aplicación utilizando una dirección URL de implementación.  
  
### Parámetros  
  
|Parámetro|Descripción|Tipo|  
|---------------|-----------------|----------|  
|`deploymentUrl`|Puntero a una cadena terminada en NULL que contiene la dirección URL del manifiesto de implementación.|LPCWSTR|  
|`data`|Reservado para un uso futuro.  Debe ser NULL.|LPVOID|  
|`flags`|Reservado para un uso futuro.  Debe ser 0.|DWORD|  
  
### Valor devuelto  
 Si se ejecuta correctamente, devuelve S\_OK; en caso contrario, devuelve un HRESULT que representa el error.  Si se produce una excepción administrada, devuelve 0x80020009 \(DISP\_E\_EXCEPTION\).  
  
## Vea también  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>