---
title: "Crear archivos de datos de generaci&#243;n de perfiles port&#225;tiles desde la l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Crear archivos de datos de generaci&#243;n de perfiles port&#225;tiles desde la l&#237;nea de comandos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si desea facilitar el uso compartido de los datos de generación de perfiles, puede usar la herramienta de línea de comandos [VSPerfReport](../profiling/vsperfreport.md) para incrustar los símbolos de una ejecución de generación de perfiles en el archivo .vsp.  
  
 También puede crear un archivo de datos de generación de perfiles preanalizado \(.vsps\) que tiene menor tamaño y se carga con más rapidez en el entorno de desarrollo integrado \(IDE\).  
  
> [!NOTE]
>  Asegúrese de que los archivos de símbolos \(.pdb\) están disponibles para **VSPerfReport**.  Para obtener más información, vea [Cómo: Especificar ubicaciones del archivo de símbolos desde la línea de comandos](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
>  Para obtener información acerca de la ruta de acceso a **VSReport**, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Los datos de generación de perfiles de un archivo .vsps no se pueden filtrar.  
  
### Para incrustar los símbolos de una ejecución de generación de perfiles en un archivo de datos de generación de perfiles \(.vsp\)  
  
-   En una ventana del símbolo del sistema, escriba el siguiente comando:  
  
     \<Archivo\>\> **\/PackSymbols**de**VSPerfReport \<**VSP de ruta  
  
     De forma predeterminada, el nombre del archivo .vsps utiliza el nombre base del archivo .vsp.  Puede especificar un nombre alternativo con la opción **Output**.  
  
### Para crear un archivo de datos de generación de perfiles de resumen  
  
-   En una ventana del símbolo del sistema, escriba el siguiente comando:  
  
     \<Archivo\> **\/SummaryFile** \[nombre de archivo\>de**VSPerfReport \<**VSP de la ruta\<de**\/Output:**\>\]  
  
     De forma predeterminada, el nombre del archivo .vsps utiliza el nombre base del archivo .vsp.  Puede especificar un nombre alternativo con la opción **Output**.