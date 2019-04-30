---
title: Solucionar problemas de herramientas de rendimiento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: troubleshooting
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 575f17c641eb057dc01fb3302098bd9f8b47f9c5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431609"
---
# <a name="troubleshooting-performance-tools-issues"></a>Solucionar problemas de herramientas de rendimiento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede experimentar uno de los siguientes problemas al utilizar las herramientas de generación de perfiles:  
  
- [No se recopilan datos con las herramientas de generación de perfiles](#NoDataCollected)  
  
- [Las vistas de rendimiento y los informes muestran números para los nombres de función](#NoSymbols)  
  
## <a name="NoDataCollected"></a> No se recopilan datos con las herramientas de generación de perfiles  
 Después de generar perfiles de una aplicación, no se crea un archivo de datos de generación de perfiles (.vsp) y recibe la siguiente advertencia en la ventana de salida o en la ventana Comandos:  
  
 PRF0025: No se ha recopilado ningún dato.  
  
 Este problema puede tener varias causas:  
  
- Un proceso cuyo perfil se generó usando el método de muestreo o de memoria de .NET inicia un proceso secundario que se convierte en el proceso que realiza el trabajo de la aplicación. Por ejemplo, algunas aplicaciones leen la línea de comandos para determinar si se han iniciado como una aplicación de Windows o como una aplicación de línea de comandos. Si se solicitó una aplicación Windows, el proceso original inicia un nuevo proceso configurado como una aplicación de Windows y después se cierra el proceso original. Dado que las herramientas de generación de perfiles no recopilan automáticamente datos de procesos secundarios, no se recopilan datos.  
  
     Para recopilar datos de generación de perfiles en esta situación, adjunte el generador de perfiles al proceso secundario en lugar de iniciar la aplicación con el generador de perfiles. Para obtener más información, vea [Cómo: Adjuntar y separar herramientas de rendimiento de los procesos en ejecución](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) y [adjuntar (VSPerfCmd)](../profiling/attach.md)  
  
## <a name="NoSymbols"></a> Las vistas de rendimiento y los informes muestran números para los nombres de función  
 Después de generar perfiles de una aplicación, se muestran números en lugar de los nombres de función en las vistas e informes.  
  
 La causa de este problema es que el motor de análisis de las herramientas de generación de perfiles no puede encontrar los archivos .pdb que contienen la información de símbolos que asigna la información de código fuente, como los nombres de función y los números de línea del archivo compilado. De forma predeterminada, el compilador crea el archivo .pdb cuando se compila el archivo de aplicación. Se almacena una referencia al directorio local del archivo .pdb en la aplicación compilada. El motor de análisis busca el archivo .pdb en el directorio al que se hace referencia y después en el archivo que contiene actualmente el archivo de aplicación. Si no se encuentra el archivo .pdb, el motor de análisis usa los desplazamientos de función en lugar de los nombres de función.  
  
 Puede corregir el problema de dos maneras:  
  
- Busque los archivos .pdb y colóquelos en el mismo directorio que los archivos de aplicación.  
  
- Incruste la información de símbolos en el archivo de datos de generación de perfiles (.vsp). Para obtener más información, consulte [Guardar información de símbolos con archivos de datos de rendimiento](../profiling/saving-symbol-information-with-performance-data-files.md).  
  
> [!NOTE]
> El motor de análisis requiere que el archivo .pdb tenga la misma versión que el archivo de la aplicación compilada. Un archivo .pdb de una compilación anterior o posterior del archivo de la aplicación no funcionará.
