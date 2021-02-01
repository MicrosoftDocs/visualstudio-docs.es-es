---
title: 'Línea de comandos de generación de perfiles: creación de archivos de datos portátiles'
description: Para facilitar el uso compartido de los datos de generación de perfiles, use la herramienta de línea de comandos VSPerfReport.exe para insertar los símbolos para una ejecución de generación de perfiles en el archivo .vsp.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5df9f14fecce23eb72d08dcba87dee360269e078
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718972"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Creación de archivos de datos de generación de perfiles portátiles desde la línea de comandos
Para facilitar el uso compartido de los datos de generación de perfiles, puede usar la herramienta de línea de comandos [VSPerfReport](../profiling/vsperfreport.md) para insertar los símbolos para una ejecución de generación de perfiles en el archivo .*vsp*.

 También puede crear un archivo de datos de generación de perfiles preanalizado (.*vsps*), que es más pequeño y se carga más rápidamente en el IDE.

> [!NOTE]
> Asegúrese de que los archivos de símbolos (.*pdb*) están disponibles para **VSPerfReport**. Para obtener más información, vea [Cómo: Especificar ubicaciones del archivo de símbolos desde la línea de comandos](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).
>
> Para obtener información sobre la ruta de acceso a **VSReport**, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).
>
> Los datos de generación de perfiles de un archivo .*vsps* no se pueden filtrar.

### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Para insertar los símbolos para una ejecución de generación de perfiles en un archivo de datos de generación de perfiles (.*vsp*)

- En una ventana del símbolo del sistema, escriba el siguiente comando:

   \<Path><strong>VSPerfReport \<</strong>Archivo VSP> **/PackSymbols**

   De forma predeterminada, el archivo .*vsps* se denomina con el nombre base del archivo .*vsp*. Puede especificar otro nombre con la opción **Output**.

### <a name="to-create-a-summary-profiling-data-file"></a>Para crear un archivo de datos de generación de perfiles de resumen

- En una ventana del símbolo del sistema, escriba el siguiente comando:

   \<Path><strong>VSPerfReport \<</strong>Archivo VSP> **/SummaryFile** [ **/Salida:** \<File Name>]

   De forma predeterminada, el archivo .*vsps* se denomina con el nombre base del archivo .*vsp*. Puede especificar otro nombre con la opción **Output**.
