---
title: Especificar la ruta de acceso a las herramientas de línea de comandos de las Herramientas de generación de perfiles | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 407ed292bea2b6b7b47e07a3a5e30183f411f991
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242910"
---
# <a name="specifying-the-path-to-profiling-tools-command-line-tools"></a>Especificar la ruta de acceso a las herramientas de línea de comandos de Herramientas de generación de perfiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La ruta de acceso a las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] no se agrega a la variable de entorno PATH. En equipos de 32 bits, las herramientas se encuentran en un único directorio. En los equipos de 64 bits, están disponibles las versiones de 32 y 64 bits de las herramientas de generación de perfiles.  
  
## <a name="32-bit-computers"></a>Equipos de 32 bits  
 En equipos de 32 bits, el directorio de herramientas del generador de perfiles predeterminado es *Unidad*\Archivos de programa\Microsoft Visual Studio 11.0\Team Tools\Performance Tools.  
  
## <a name="64-bit-computers"></a>Equipos de 64 bits  
 En los equipos de 64 bits, especifique la ruta de acceso según la plataforma de destino de la aplicación para la que se genera el perfil.  
  
-   En las aplicaciones de 32 bits, el directorio de herramientas de generador de perfiles predeterminado es:  
  
     *Unidad*\Archivos de programa (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools  
  
-   En las aplicaciones de 64 bits, el directorio de herramientas de generador de perfiles predeterminado es:  
  
     *Unidad*\Archivos de programa (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\x64



