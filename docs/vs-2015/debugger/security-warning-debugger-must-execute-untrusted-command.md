---
title: 'Advertencia de seguridad: El depurador debe ejecutar un comando que no se confía | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa5678c56d07dd76e659f10435fb3b4f8cb1a3a3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215454"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Advertencia de seguridad: El depurador debe ejecutar un comando que no es de confianza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este cuadro de diálogo de advertencia aparece cuando utiliza un servidor de origen. Indica que el comando que el depurador debe ejecutar para obtener el código fuente no figura en la lista de comandos de confianza del servidor de origen incluida en el archivo srcsvr.ini. Si es un comando válido, se puede agregar al archivo srcsvr.ini. De lo contrario, no debe ejecutarse. Para obtener más información, consulte [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="message-text"></a>Texto del mensaje  
 **El depurador debe ejecutar el siguiente comando de confianza para obtener el código fuente desde el servidor de origen.**  
  
 **Si el archivo de símbolos de depuración (\*.pdb) es no de una fuente conocida y de confianza, este comando podría ser peligroso para ejecutar o no válido.**  
  
 **¿Desea ejecutar este comando?**  
  
## <a name="uielement-list"></a>Lista de UIElement  
 Cuadro de texto  
 Comando del archivo .pdb que se va a ejecutar.  
  
 Run  
 Permite que se ejecute el comando.  
  
 No ejecutar  
 Detiene la ejecución del comando y la descarga del archivo del servidor de origen.  
  
## <a name="see-also"></a>Vea también  
 [Especificar símbolos (.pdb) y los archivos de origen](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Servidor de origen](http://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)



