---
title: Crear archivos de datos de generación de perfiles portátiles desde la línea de comandos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: be919183f18efc29ea562b0e4cc60c84febe60c8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49841941"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Creación de archivos de datos de generación de perfiles portátiles desde la línea de comandos
Para facilitar el uso compartido de los datos de generación de perfiles, puede usar la herramienta de línea de comandos [VSPerfReport](../profiling/vsperfreport.md) para insertar los símbolos para una ejecución de generación de perfiles en el archivo .*vsp*.  
  
 También puede crear un archivo de datos de generación de perfiles preanalizado (.*vsps*), que es más pequeño y se carga más rápidamente en el IDE.  
  
> [!NOTE]
>  Asegúrese de que los archivos de símbolos (.*pdb*) están disponibles para **VSPerfReport**. Para más información, vea [Cómo: Especificar ubicaciones del archivo de símbolos desde la línea de comandos](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
>  Para obtener información sobre la ruta de acceso a **VSReport**, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Los datos de generación de perfiles de un archivo .*vsps* no se pueden filtrar.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Para insertar los símbolos para una ejecución de generación de perfiles en un archivo de datos de generación de perfiles (.*vsp*)  
  
- En una ventana del símbolo del sistema, escriba el siguiente comando:  
  
   \<RutaAcceso><strong>VSPerfReport \<</strong>ArchivoVSP> **/PackSymbols**  
  
   De forma predeterminada, el archivo .*vsps* se denomina con el nombre base del archivo .*vsp*. Puede especificar otro nombre con la opción **Output**.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Para crear un archivo de datos de generación de perfiles de resumen  
  
- En una ventana del símbolo del sistema, escriba el siguiente comando:  
  
   \<RutaAcceso><strong>VSPerfReport \<</strong>ArchivoVSP> **/SummaryFile** [**/Output:**\<NombreArchivo>]  
  
   De forma predeterminada, el archivo .*vsps* se denomina con el nombre base del archivo .*vsp*. Puede especificar otro nombre con la opción **Output**.