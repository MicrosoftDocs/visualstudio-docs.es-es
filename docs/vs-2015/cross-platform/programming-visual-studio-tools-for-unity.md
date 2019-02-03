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
ms.openlocfilehash: ccdc91643725e8799f587d14923ecf7620fc13b3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774379"
---
# <a name="programming-visual-studio-tools-for-unity"></a>Programación de Visual Studio Tools para Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
En esta sección encontrará ejemplos de uso de Visual Studio Tools para la API de Unity.  
  
## <a name="examples"></a>Ejemplos  
 Estos son algunos ejemplos que muestran cómo se puede utilizar la API de Visual Studio Tools para Unity.  
  
### <a name="customize-project-files-created-by-vstu"></a>Personalizar archivos de proyecto creados por VSTU  
 Visual Studio Tools para Unity ofrece una devolución de llamada al estilo de Unity durante la generación del archivo de proyecto. Para obtener más información sobre cómo modificar el archivo del proyecto cada vez que se regenere, vea [Ejemplo: generación de archivos de proyecto](../cross-platform/customize-project-files-created-by-vstu.md).  
  
### <a name="share-the-unity-log-callback-with-vstu"></a>Compartir la devolución de llamada de registro de Unity con VSTU  
 Visual Studio Tools para Unity registra una devolución de llamada de registro con Unity para poder transmitir su consola a Visual Studio. Si los scripts del editor también registran una devolución de llamada de registro con Unity, la devolución de llamada de VSTU puede interferir con la devolución de llamada. Para obtener más información sobre cómo compartir la devolución de llamada de registro de Unity con VSTU, vea [Ejemplo: devolución de llamada de registro](../cross-platform/share-the-unity-log-callback-with-vstu.md).
