---
title: TargetCLR | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 517cf1eccd296716b0105539f6ae81cbc3519fd0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759303"
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
  
 **Launch:** `AppName`  
 Inicia la aplicación especificada y empieza a generar perfiles.  
  
 **Attach:** `PID`  
 Empieza a generar perfiles del proceso especificado.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, la opción TargetCLR se usa para asegurarse de que se genera el perfil de la versión 4.0.11003 de CLR.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```



