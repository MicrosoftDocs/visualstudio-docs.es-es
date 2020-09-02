---
title: Programación de Visual Studio Tools para Unity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
caps.latest.revision: 5
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: 469478f05546a32bb890f759d3d00cb447b54d2b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145893"
---
# <a name="programming-visual-studio-tools-for-unity"></a>Programación de Visual Studio Tools para Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En esta sección encontrará ejemplos de uso de la API de Visual Studio Tools para Unity.  
  
## <a name="examples"></a>Ejemplos  
 Estos son algunos ejemplos que muestran cómo se puede utilizar la API de Visual Studio Tools para Unity.  
  
### <a name="customize-project-files-created-by-vstu"></a>Personalizar archivos de proyecto creados por VSTU  
 Visual Studio Tools para Unity ofrece una devolución de llamada al estilo de Unity durante la generación del archivo de proyecto. Para más información sobre cómo modificar el archivo del proyecto cada vez que se regenere, vea [Personalizar archivos de proyecto creados por VSTU](../cross-platform/customize-project-files-created-by-vstu.md).  
  
### <a name="share-the-unity-log-callback-with-vstu"></a>Compartir la devolución de llamada de registro de Unity con VSTU  
 Visual Studio Tools para Unity registra una devolución de llamada de registro con Unity para poder transmitir su consola a Visual Studio. Si los scripts del editor también registran una devolución de llamada de registro con Unity, la devolución de llamada de VSTU puede interferir con la devolución de llamada. Para más información sobre cómo compartir la devolución de llamada de registro de Unity con VSTU, vea [Compartir la devolución de llamada de registro de Unity con VSTU](../cross-platform/share-the-unity-log-callback-with-vstu.md).
