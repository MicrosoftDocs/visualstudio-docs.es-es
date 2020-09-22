---
title: Crear archivos de datos de generación de perfiles portátiles desde la línea de comandos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5d343392c9e554c5e51325964949cd3ea13237b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842527"
---
# <a name="creating-portable-profiling-data-files-from-the-command-line"></a>Crear archivos de datos de generación de perfiles portátiles desde la línea de comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para facilitar el uso compartido de los datos de generación de perfiles, puede usar la herramienta de línea de comandos [VSPerfReport](../profiling/vsperfreport.md) para incrustar los símbolos para una generación de perfiles en el archivo. VSP.  
  
 También puede crear un archivo de datos de generación de perfiles preanalizado (.vsps), que es más pequeño y se carga más deprisa en el IDE.  
  
> [!NOTE]
> Asegúrese de que los archivos de símbolos (. pdb) están disponibles para **VSPerfReport**. Para obtener más información, vea [Cómo: especificar ubicaciones de archivos de símbolos desde la línea de comandos](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
> Para información sobre la ruta de acceso a **VSReport**, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
> Los datos de generación de perfiles de un archivo .vsps no se pueden filtrar.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Para incrustar los símbolos para una ejecución de generación de perfiles en un archivo de datos de generación de perfiles (.vsp)  
  
- En una ventana del símbolo del sistema, escriba el siguiente comando:  
  
   \<Path><strong>VSPerfReport \<</strong>Archivo VSP> **/PackSymbols**  
  
   De forma predeterminada, el archivo .vsps se denomina con el nombre base del archivo .vsp. Puede especificar otro nombre con la opción **Output**.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Para crear un archivo de datos de generación de perfiles de resumen  
  
- En una ventana del símbolo del sistema, escriba el siguiente comando:  
  
   \<Path><strong>VSPerfReport \<</strong>Archivo VSP> **/SummaryFile** [ **/Salida:** \<File Name>]  
  
   De forma predeterminada, el archivo .vsps se denomina con el nombre base del archivo .vsp. Puede especificar otro nombre con la opción **Output**.
