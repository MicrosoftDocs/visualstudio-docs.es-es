---
title: 'DA0002: Falta VSPerfCorProf.dll | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 86f4738d72cc386e6285dfa96a7f42e906a9a5cd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242494"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: Falta VSPerfCorProf.dll
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id. de regla | DA0002 |  
| Categoría | Uso de herramientas de generación de perfiles |  
| Métodos de generación de perfiles | Generación de perfiles mediante las herramientas de línea de comandos VSPerfCmd y VSPerfASPNETCmd |  
| Mensaje | Parece que el archivo se recopiló sin haber establecido correctamente las variables de entorno con VSPerfCLREnv.cmd. Es posible que no se resuelvan los símbolos para los binarios administrados. |  
| Tipo de regla | Información |  
  
## <a name="cause"></a>Motivo  
 El generador de perfiles no ha podido encontrar VSPerfCorProf.dll durante la ejecución de generación de perfiles. Esta advertencia se produce cuando se usan herramientas de línea de comandos para la recopilación de datos del generador de perfiles sin utilizar la herramienta VSPerfCLREnv.cmd para inicializar las variables de entorno necesarias. La advertencia también se puede activar si se está ejecutando otro generador de perfiles al iniciar las Herramientas de generación de perfiles.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Deben establecerse variables de entorno específicas antes de una ejecución de generación de perfiles para que el generador de perfiles resuelva los símbolos de los archivos binarios de .NET Framework. Esta advertencia indica que la herramienta VSPerfCLREnv.cmd no se ha ejecutado antes de que se hayan recopilado los datos de generación de perfiles. Puede que no se resuelvan los símbolos de archivos binarios administrados. Para obtener más información sobre cómo usar las Herramientas de generación de perfiles desde la línea de comandos, consulte [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md)  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Cuando genere perfiles de aplicaciones administradas mediante el uso de las herramientas de línea de comandos de las Herramientas de generación de perfiles [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ejecute la herramienta de línea de comandos [VSPerfCLREnv](../profiling/vsperfclrenv.md) antes de comenzar a recopilar datos.



