---
title: TargetCLR | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e4ca52f631b3e2de9c01daab7e6268c42f20268
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145621"
---
# <a name="targetclr"></a>TargetCLR
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La opción **TargetCLR** especifica la versión de Common Language Runtime (CLR) para generar perfiles cuando se carga más de una versión del CRL en una aplicación.  
  
 De forma predeterminada, las Herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se dirigen a la primera versión del CLR cargada por la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>Parámetros  
 `ClrVersion`  
 Número de versión del CLR. Use el formato de versión **vN.N.NNNNN**.  
  
## <a name="required-options"></a>Opciones necesarias  
 La opción **TargetCLR** solo se puede usar con las opciones **Launch** o **Attach**.  
  
 **Iniciar:**`AppName`  
 Inicia la aplicación especificada y empieza a generar perfiles.  
  
 **Asociar:**`PID`  
 Empieza a generar perfiles del proceso especificado.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, la opción TargetCLR se usa para asegurarse de que se genera el perfil de la versión 4.0.11003 de CLR.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```
