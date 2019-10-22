---
title: 'Advertencia de seguridad: El depurador debe ejecutar un comando que no se confía | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a29ba026f9b3c2b8839d474c2d0833eb79f7ffd
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683298"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Advertencia de seguridad: El depurador debe ejecutar un comando que no es de confianza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este cuadro de diálogo de advertencia aparece cuando utiliza un servidor de origen. Indica que el comando que el depurador debe ejecutar para obtener el código fuente no figura en la lista de comandos de confianza del servidor de origen incluida en el archivo srcsvr.ini. Si es un comando válido, se puede agregar al archivo srcsvr.ini. De lo contrario, no debe ejecutarse. Para obtener más información, consulte [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="message-text"></a>Texto del mensaje  
 **El depurador debe ejecutar el siguiente comando que no es de confianza para obtener el código fuente del servidor de origen.**  
  
 **Si el archivo de símbolo de depuración (\*.pdb) no procede de una fuente conocida y de confianza, este comando puede no ser válido o su ejecución puede ser peligrosa.**  
  
 **¿Quiere ejecutar este comando?**  
  
## <a name="uielement-list"></a>Lista de UIElement  
 Cuadro de texto  
 Comando del archivo .pdb que se va a ejecutar.  
  
 Run  
 Permite que se ejecute el comando.  
  
 No ejecutar  
 Detiene la ejecución del comando y la descarga del archivo del servidor de origen.  
  
## <a name="see-also"></a>Vea también  
 [Especificación de archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Servidor de origen](https://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)
