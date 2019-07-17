---
title: 'DA0002: Falta VSPerfCorProf.dll | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5723506415a0ddbf816b896e23e93eaa706bf7e7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158726"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: Falta VSPerfCorProf.dll
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id. de regla | DA0002 |  
| Categoría | Uso de herramientas de generación de perfiles |  
| Métodos de generación de perfiles | Generación de perfiles mediante las herramientas de línea de comandos VSPerfCmd y VSPerfASPNETCmd |  
| Mensaje | Parece que el archivo se recopiló sin haber establecido correctamente las variables de entorno con VSPerfCLREnv.cmd. Es posible que los símbolos de archivos binarios administrados no se resuelvan.|  
| Tipo de regla | Información |  
  
## <a name="cause"></a>Causa  
 El generador de perfiles no ha podido encontrar VSPerfCorProf.dll durante la ejecución de generación de perfiles. Esta advertencia se produce cuando se usan herramientas de línea de comandos para la recopilación de datos del generador de perfiles sin utilizar la herramienta VSPerfCLREnv.cmd para inicializar las variables de entorno necesarias. La advertencia también se puede activar si se está ejecutando otro generador de perfiles al iniciar las Herramientas de generación de perfiles.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Deben establecerse variables de entorno específicas antes de una ejecución de generación de perfiles para que el generador de perfiles resuelva los símbolos de los archivos binarios de .NET Framework. Esta advertencia indica que la herramienta VSPerfCLREnv.cmd no se ha ejecutado antes de que se hayan recopilado los datos de generación de perfiles. Puede que no se resuelvan los símbolos de archivos binarios administrados. Para obtener más información sobre cómo usar las Herramientas de generación de perfiles desde la línea de comandos, consulte [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Cuando genere perfiles de aplicaciones administradas mediante el uso de las herramientas de línea de comandos de las Herramientas de generación de perfiles [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ejecute la herramienta de línea de comandos [VSPerfCLREnv](../profiling/vsperfclrenv.md) antes de comenzar a recopilar datos.
