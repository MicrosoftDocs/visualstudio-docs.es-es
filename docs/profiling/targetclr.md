---
title: TargetCLR | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f8ea5bd3f1ec16f6deeae8365cc90541bc8b958
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="targetclr"></a>TargetCLR
La opción **TargetCLR** especifica la versión de Common Language Runtime (CLR) para generar perfiles cuando se carga más de una versión del CRL en una aplicación.  
  
 De forma predeterminada, las Herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se dirigen a la primera versión del CLR cargada por la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```cmd  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>Parámetros  
 `ClrVersion`  
 Número de versión del CLR. Use el formato de versión **vN.N.NNNNN**.  
  
## <a name="required-options"></a>Opciones necesarias  
 La opción **TargetCLR** solo se puede usar con las opciones **Launch** o **Attach**.  
  
 **Launch:** `AppName`  
 Inicia la aplicación especificada y empieza a generar perfiles.  
  
 **Attach:** `PID`  
 Empieza a generar perfiles del proceso especificado.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, la opción TargetCLR se usa para asegurarse de que se genera el perfil de la versión 4.0.11003 de CLR.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```