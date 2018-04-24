---
title: 'Advertencia de seguridad: El depurador debe ejecutar un comando que no se confía | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 77554795772a5a9e2ce5d9bbe9f620923bc20184
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Advertencia de seguridad: El depurador debe ejecutar un comando que no es de confianza
Este cuadro de diálogo de advertencia aparece cuando utiliza un servidor de origen. Indica que el comando que el depurador debe ejecutar para obtener el código fuente no figura en la lista de comandos de confianza del servidor de origen incluida en el archivo srcsvr.ini. Si es un comando válido, se puede agregar al archivo srcsvr.ini. De lo contrario, no debe ejecutarse. Para obtener más información, consulte [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="message-text"></a>Texto del mensaje  
 **El depurador debe ejecutar el siguiente comando no es de confianza para obtener el código fuente del servidor de origen.**  
  
 **Si el archivo de símbolos de depuración (\*.pdb) es no de una fuente conocida y de confianza, este comando podría ser peligrosa su ejecución o no válido.**  
  
 **¿Desea ejecutar este comando?**  
  
## <a name="uielement-list"></a>Lista de UIElement  
 Cuadro de texto  
 Comando del archivo .pdb que se va a ejecutar.  
  
 Run  
 Permite que se ejecute el comando.  
  
 No ejecutar  
 Detiene la ejecución del comando y la descarga del archivo del servidor de origen.  
  
## <a name="see-also"></a>Vea también  
 [Especificar los símbolos (.pdb) y archivos de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Servidor de origen](http://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)