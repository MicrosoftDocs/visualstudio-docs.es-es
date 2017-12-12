---
title: "Programación de Visual Studio Tools para Unity | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
caps.latest.revision: "3"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 0bae39888104fb194b0ac178ae2c1be316d06585
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="programming-visual-studio-tools-for-unity"></a>Programación de Visual Studio Tools para Unity
En esta sección encontrará ejemplos de uso de Visual Studio Tools para la API de Unity.  
  
## <a name="examples"></a>Ejemplos  
 Estos son algunos ejemplos que muestran cómo se puede utilizar la API de Visual Studio Tools para Unity.  
  
### <a name="customize-project-files-created-by-vstu"></a>Personalizar archivos de proyecto creados por VSTU  
 Visual Studio Tools para Unity ofrece una devolución de llamada al estilo de Unity durante la generación del archivo de proyecto. Para más información sobre cómo modificar el archivo del proyecto cada vez que se regenere, vea [Personalizar archivos de proyecto creados por VSTU](../cross-platform/customize-project-files-created-by-vstu.md).  
  
### <a name="share-the-unity-log-callback-with-vstu"></a>Compartir la devolución de llamada de registro de Unity con VSTU  
 Visual Studio Tools para Unity registra una devolución de llamada de registro con Unity para poder transmitir su consola a Visual Studio. Si los scripts del editor también registran una devolución de llamada de registro con Unity, la devolución de llamada de VSTU puede interferir con la devolución de llamada. Para más información sobre cómo compartir la devolución de llamada de registro de Unity con VSTU, vea [Compartir la devolución de llamada de registro de Unity con VSTU](../cross-platform/share-the-unity-log-callback-with-vstu.md).