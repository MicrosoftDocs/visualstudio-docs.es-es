---
title: Alerta de seguridad del servidor de origen | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f8b122deab5dbdc30b129bce221a804f8c53aa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699320"
---
# <a name="source-server-security-alert"></a>Alerta de seguridad del servidor de origen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si utiliza el servidor de origen, trabaje únicamente con archivos de símbolos procedentes de una ubicación conocida y de confianza.  
  
 Esta advertencia aparece cuando habilita la compatibilidad con el servidor de origen. Los comandos de servidor de origen se incrustan en archivos de símbolos de depuración (archivos PDB). Asegúrese de que sabe de dónde provienen los archivos PDB.  
  
> [!IMPORTANT]
> Al usar un servidor de origen, debe tener en cuenta estas posibles amenazas de seguridad: En el archivo PDB de la aplicación se pueden incrustar comandos arbitrarios, por lo que debe asegurarse de colocar únicamente los que quiera ejecutar en el archivo srcsrv.ini. Todo intento de ejecutar un comando no incluido en el archivo srcsvr.ini provocará la aparición de un cuadro de diálogo de confirmación. Para obtener más información, vea [Advertencia de seguridad: el depurador debe ejecutar un comando](../debugger/security-warning-debugger-must-execute-untrusted-command.md)que no es de confianza. No se realiza ninguna validación en los parámetros de comando, por lo que debe tener cuidado con los comandos de confianza. Por ejemplo, si confiara en cmd.exe, un usuario malintencionado podría especificar parámetros que harían que el comando fuera peligroso.  
  
## <a name="see-also"></a>Consulte también  
 [Especificar archivos de código fuente y símbolos (. pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Servidor de origen](https://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)
