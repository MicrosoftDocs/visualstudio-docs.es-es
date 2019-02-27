---
title: 'Advertencia de seguridad: El depurador debe ejecutar un comando que no se confía | Microsoft Docs'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c4ab45feeae409a1951e1a57e964eaaa5963896
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690362"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Advertencia de seguridad: El depurador debe ejecutar un comando que no es de confianza
Este cuadro de diálogo de advertencia aparece cuando utiliza un servidor de origen. Indica que el comando que el depurador debe ejecutar para obtener el código fuente no figura en la lista de comandos de confianza del servidor de origen incluida en el archivo srcsvr.ini. Si es un comando válido, se puede agregar al archivo srcsvr.ini. De lo contrario, no debe ejecutarse. Para obtener más información, consulte [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="message-text"></a>Texto del mensaje
 **El depurador debe ejecutar el siguiente comando que no es de confianza para obtener el código fuente del servidor de origen.**

 **Si el archivo de símbolo de depuración (\*.pdb) no procede de una fuente conocida y de confianza, este comando puede no ser válido o su ejecución puede ser peligrosa.**

 **¿Quiere ejecutar este comando?**

## <a name="uielement-list"></a>Lista de UIElement
 Comando de cuadro de texto desde el archivo .pdb para ejecutar.

 Permitir ejecutar el comando se ejecute.

 No ejecute detener la ejecución del comando y la descarga del archivo del servidor de origen.

## <a name="see-also"></a>Vea también
- [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Seguridad del depurador](../debugger/debugger-security.md)
- [Servidor de origen](/windows/desktop/Debug/source-server-and-source-indexing)