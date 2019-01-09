---
title: TargetCLR | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed0891715f6c9a0f4f89249a6ca5ac6415bad038
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967127"
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