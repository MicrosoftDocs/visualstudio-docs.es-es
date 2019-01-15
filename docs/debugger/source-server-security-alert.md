---
title: Alerta de seguridad del servidor de origen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e01f9c06ec989829a27c58b7dae9b128512911e9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909923"
---
# <a name="source-server-security-alert"></a>Alerta de seguridad del servidor de origen
Si utiliza el servidor de origen, trabaje únicamente con archivos de símbolos procedentes de una ubicación conocida y de confianza.  
  
 Esta advertencia aparece cuando habilita la compatibilidad con el servidor de origen. Los comandos de servidor de origen se incrustan en archivos de símbolos de depuración (archivos **\*.pdb**). Asegúrese de que sabe de dónde provienen los archivos PDB.  
  
> [!IMPORTANT]
>  Debe tener en cuenta las posibles amenazas de seguridad cuando use un servidor de origen: En el archivo PDB de la aplicación se pueden incrustar comandos arbitrarios, por lo que debe asegurarse de colocar únicamente los que desee ejecutar en el archivo srcsrv.ini. Todo intento de ejecutar un comando no incluido en el archivo srcsvr.ini provocará la aparición de un cuadro de diálogo de confirmación. Para obtener más información, consulte [advertencia de seguridad: El depurador debe ejecutar un comando que no es de confianza](../debugger/security-warning-debugger-must-execute-untrusted-command.md) No se realiza ninguna validación de los parámetros de comando, por lo que debe tener cuidado con los comandos de confianza. Por ejemplo, si confiara en cmd.exe, un usuario malintencionado podría especificar parámetros que harían que el comando fuera peligroso.  
  
## <a name="see-also"></a>Vea también  
 [Especificación de archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Servidor de origen](/windows/desktop/Debug/source-server-and-source-indexing)
