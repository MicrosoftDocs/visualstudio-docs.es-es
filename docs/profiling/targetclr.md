---
title: TargetCLR | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 479f7e1cbd85c0421497020ae1fc108154ca639a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596313"
---
# <a name="targetclr"></a>TargetCLR
La opción **TargetCLR** especifica la versión de Common Language Runtime (CLR) para generar perfiles cuando se carga más de una versión del CRL en una aplicación.

 De forma predeterminada, las Herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se dirigen a la primera versión del CLR cargada por la aplicación.

## <a name="syntax"></a>Sintaxis

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]
```

#### <a name="parameters"></a>Parámetros
 `ClrVersion` Número de versión del CLR. Use el formato de versión **vN.N.NNNNN**.

## <a name="required-options"></a>Opciones necesarias
 La opción **TargetCLR** solo se puede usar con las opciones **Launch** o **Attach**.

 **Launch:** `AppName` Inicia la aplicación especificada y empieza a generar perfiles.

 **Attach:** `PID` Empieza a generar perfiles del proceso especificado.

## <a name="example"></a>Ejemplo
 En este ejemplo, la opción TargetCLR se usa para asegurarse de que se genera el perfil de la versión 4.0.11003 de CLR.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003
```