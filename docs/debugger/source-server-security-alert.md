---
title: Alerta de seguridad de servidor de origen | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.sourceserver.enablewarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1bce9b20e6787ae6234ba308c29f512ba47986d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="source-server-security-alert"></a>Alerta de seguridad del servidor de origen
Si utiliza el servidor de origen, trabaje únicamente con archivos de símbolos procedentes de una ubicación conocida y de confianza.  
  
 Esta advertencia aparece cuando habilita la compatibilidad con el servidor de origen. Comandos de servidor de origen se incrustan en archivos de símbolos de depuración (***.pdb** archivos). Asegúrese de que sabe de dónde provienen los archivos PDB.  
  
> [!IMPORTANT]
>  Se deben tener en cuenta las siguientes amenazas potenciales para la seguridad al utilizar el servidor de origen: puede haber comandos arbitrarios incrustados en el archivo PDB de la aplicación, por lo que es necesario asegurarse de poner únicamente los que se desean ejecutar en el archivo srcsrv.ini. Todo intento de ejecutar un comando no incluido en el archivo srcsvr.ini provocará la aparición de un cuadro de diálogo de confirmación. Para obtener más información, consulta [Security Warning: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md). No se realiza ninguna validación de los parámetros de comando, por lo que debe tener cuidado con los comandos de confianza. Por ejemplo, si confiara en cmd.exe, un usuario malintencionado podría especificar parámetros que harían que el comando fuera peligroso.  
  
## <a name="see-also"></a>Vea también  
 [Especificar los símbolos (.pdb) y archivos de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Servidor de origen](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)
