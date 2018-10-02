---
title: Alerta de seguridad del servidor de origen | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b971a05f9cd8873a1dbac3cafe6865ffce238868
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574836"
---
# <a name="source-server-security-alert"></a>Alerta de seguridad del servidor de origen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [alerta de seguridad del servidor de origen](https://docs.microsoft.com/visualstudio/debugger/source-server-security-alert).  
  
Si utiliza el servidor de origen, trabaje únicamente con archivos de símbolos procedentes de una ubicación conocida y de confianza.  
  
 Esta advertencia aparece cuando habilita la compatibilidad con el servidor de origen. Los comandos de servidor de origen se incrustan en archivos de símbolos de depuración (archivos PDB). Asegúrese de que sabe de dónde provienen los archivos PDB.  
  
> [!IMPORTANT]
>  Se deben tener en cuenta las siguientes amenazas potenciales para la seguridad al utilizar el servidor de origen: puede haber comandos arbitrarios incrustados en el archivo PDB de la aplicación, por lo que es necesario asegurarse de poner únicamente los que se desean ejecutar en el archivo srcsrv.ini. Todo intento de ejecutar un comando no incluido en el archivo srcsvr.ini provocará la aparición de un cuadro de diálogo de confirmación. Para obtener más información, consulte [advertencia de seguridad: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Se realiza ninguna validación en los parámetros del comando, por lo que debe tener cuidado con los comandos de confianza. Por ejemplo, si confiara en cmd.exe, un usuario malintencionado podría especificar parámetros que harían que el comando fuera peligroso.  
  
## <a name="see-also"></a>Vea también  
 [Especificar símbolos (.pdb) y los archivos de origen](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Servidor de origen](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)



