---
title: Especificar la ruta de acceso a las herramientas de línea de comandos de las Herramientas de generación de perfiles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1afb0b00a7e121c611dedbc235684a67cc9cec53
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814500"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Especificar la ruta de acceso a las herramientas de línea de comandos de las Herramientas de generación de perfiles
La ruta de acceso a las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no se agrega a la variable de entorno PATH. En equipos de 32 bits, las herramientas se encuentran en un único directorio. En los equipos de 64 bits, están disponibles las versiones de 32 y 64 bits de las herramientas de generación de perfiles.  
  
## <a name="32-bit-computers"></a>Equipos de 32 bits  
 En equipos de 32 bits, el directorio de herramientas del generador de perfiles predeterminado es *unidad\Archivos de programa\Microsoft Visual Studio 11.0\Team Tools\Performance Tools*.  
  
## <a name="64-bit-computers"></a>Equipos de 64 bits  
 En los equipos de 64 bits, especifique la ruta de acceso según la plataforma de destino de la aplicación para la que se genera el perfil.  
  
-   En las aplicaciones de 32 bits, el directorio de herramientas de generador de perfiles predeterminado es:  
  
     *unidad\Archivos de programa (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools*  
  
-   En las aplicaciones de 64 bits, el directorio de herramientas de generador de perfiles predeterminado es:  
  
     *unidad\Archivos de programa (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\x64*