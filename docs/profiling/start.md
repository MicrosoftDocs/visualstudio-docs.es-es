---
title: "Iniciar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Iniciar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La opción **Start** es una opción de VSPerfCmd.exe que inicializa el generador de perfiles al método de generación de perfiles especificado.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### Parámetros  
 `Method`  
 Debe ser una de las siguientes palabras clave:  
  
-   **TRACE**: especifica el método de instrumentación.  
  
-   **SAMPLE**: especifica el método de muestreo.  
  
-   **COVERAGE**: especifica la cobertura de código.  
  
-   **CONCURRENCY** \- Especifica el método de contención de recursos.  
  
## Opciones necesarias  
 La opción **Output** se debe especificar cuando se especifica **Start** en la línea de comandos.  
  
 **Output:** `filename`  
 Especifica el nombre del archivo de salida.  
  
## Opciones exclusivas  
 Las opciones siguientes solo se pueden utilizar con la opción **Start** en una línea de comandos.  
  
 **CrossSession**&#124;**CS**  
 Habilita la generación de perfiles entre procesos.  Los nombres de opción **CrossSession** y **CS** están ambos admitidos.  
  
 **User:**\[`domain\`\]`username`  
 Habilita el acceso de cliente al monitor de rendimiento desde la cuenta especificada.  
  
 **WinCounter:** `Path` \[**Automark**:`n`\]  
 **WinCounter** especifica un evento de contador de rendimiento de Windows para incluirlo como una marca en el archivo de datos de generación de perfiles.  **AutoMark** especifica el intervalo en milisegundos entre las colecciones del archivo de datos.  
  
## Opciones no válidas  
 Las opciones siguientes no se pueden utilizar con la opción **Start** en una línea de comandos.  
  
 **Status**  
 **Status** se aplica a los procesos cuyos perfiles se generan.  Muestra los procesos y subprocesos, así como su estado de generación de perfiles actual \(on\/off\).  Por ejemplo, si un proceso se detiene, **Status** no lo indicará en el informe.  **Status** mostrará si se han generado perfiles para el proceso o no.  
  
 **Shutdown**\[**:**`Timeout`\]  
 Desactiva el generador de perfiles.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo usar la opción **Start** de VSPerfCmd.exe para inicializar el generador de perfiles.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)