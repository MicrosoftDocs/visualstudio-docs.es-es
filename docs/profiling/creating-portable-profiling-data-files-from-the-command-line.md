---
title: "Crear archivos de datos de generación de perfiles portátiles desde la línea de comandos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 95302666d8bd5c5738f93a2fb0a8ec698c5bb7d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="creating-portable-profiling-data-files-from-the-command-line"></a>Crear archivos de datos de generación de perfiles portátiles desde la línea de comandos
Para facilitar el uso compartido de los datos de generación de perfiles, puede usar la herramienta de línea de comandos [VSPerfReport](../profiling/vsperfreport.md) para incrustar los símbolos para una ejecución de generación de perfiles en el archivo .vsp.  
  
 También puede crear un archivo de datos de generación de perfiles preanalizado (.vsps), que es más pequeño y se carga más deprisa en el IDE.  
  
> [!NOTE]
>  Asegúrese de que los archivos de símbolos (.pdb) están disponibles para **VSPerfReport**. Para obtener más información, consulte [Cómo: Especificar ubicaciones del archivo de símbolos desde la línea de comandos](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
>  Para información sobre la ruta de acceso a **VSReport**, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Los datos de generación de perfiles de un archivo .vsps no se pueden filtrar.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Para incrustar los símbolos para una ejecución de generación de perfiles en un archivo de datos de generación de perfiles (.vsp)  
  
-   En una ventana del símbolo del sistema, escriba el siguiente comando:  
  
     \<RutaAcceso>**VSPerfReport \<**ArchivoVSP> **/PackSymbols**  
  
     De forma predeterminada, el archivo .vsps se denomina con el nombre base del archivo .vsp. Puede especificar otro nombre con la opción **Output**.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Para crear un archivo de datos de generación de perfiles de resumen  
  
-   En una ventana del símbolo del sistema, escriba el siguiente comando:  
  
     \<RutaAcceso>**VSPerfReport \<**ArchivoVSP> **/SummaryFile** [**/Output:**\<NombreArchivo>]  
  
     De forma predeterminada, el archivo .vsps se denomina con el nombre base del archivo .vsp. Puede especificar otro nombre con la opción **Output**.