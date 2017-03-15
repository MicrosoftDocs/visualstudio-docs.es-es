---
title: "DA0002: Falta VSPerfCorProf.dll | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0002"
  - "vs.performance.2"
  - "vs.performance.rules.DAVsPerfCorProfMissing"
  - "vs.performance.rules.DA0002"
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0002: Falta VSPerfCorProf.dll
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0002|  
|Categoría|Uso de Herramientas de generación de perfiles|  
|Métodos de generación de perfiles|Perfilar mediante las herramientas de línea de comandos VSPerfASPNETCmd y VSPerfCmd|  
|Mensaje|Parece que el archivo se recopiló sin haber establecido correctamente las variables de entorno con VSPerfCLREnv.cmd.  Puede que no se resuelvan los símbolos de archivos binarios administrados.|  
|Tipo de regla|Información|  
  
## Motivo  
 El generador de perfiles no pudo encontrar VSPerfCorProf.dll durante la generación de perfiles.  Esta advertencia aparece cuando las herramientas de línea de comandos para la recopilación de datos del generador de perfiles se emplean sin la herramienta VSPerfCLREnv.cmd para inicializar las variables de entorno necesarias.  La advertencia también puede producirse si otro generador de perfiles se está ejecutando cuando se inician las herramientas de generación de perfiles.  
  
## Descripción de la regla  
 Para que el generador de perfiles resuelva los símbolos de los archivos binarios de .NET Framework, se deben establecer variables de entorno concretas antes de una ejecución de generación de perfiles.  Esta advertencia sugiere que no se ejecutó la herramienta VSPerfCLREnv.cmd antes de recopilar los datos de generación de perfiles.  Es posible que no se resuelvan los símbolos de los archivos binarios administrados.  Para obtener más información acerca del uso de las herramientas de generación de perfiles desde la línea de comandos, vea [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md).  
  
## Cómo corregir infracciones  
 Si genera perfiles de aplicaciones administradas mediante herramientas de línea de comandos en Herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ejecute la herramienta de línea de comandos [VSPerfCLREnv](../profiling/vsperfclrenv.md) antes de iniciar la recopilación de datos.