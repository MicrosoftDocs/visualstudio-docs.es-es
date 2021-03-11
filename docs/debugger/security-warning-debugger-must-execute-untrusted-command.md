---
description: Este cuadro de diálogo de advertencia aparece cuando utiliza un servidor de origen.
title: 'Advertencia de seguridad: El depurador debe ejecutar un comando que no es de confianza | Microsoft Docs'
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1ca71db31fc976a2bc3c652929fd9215f2f3123f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166663"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Advertencia de seguridad: El depurador debe ejecutar un comando que no es de confianza
Este cuadro de diálogo de advertencia aparece cuando utiliza un servidor de origen. Indica que el comando que el depurador debe ejecutar para obtener el código fuente no figura en la lista de comandos de confianza del servidor de origen incluida en el archivo srcsvr.ini. Si es un comando válido, se puede agregar al archivo srcsvr.ini. De lo contrario, no debe ejecutarse. Para obtener más información, consulte [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="message-text"></a>Texto del mensaje
 **El depurador debe ejecutar el siguiente comando que no es de confianza para obtener el código fuente del servidor de origen.**

 **Si el archivo de símbolo de depuración (\*.pdb) no procede de una fuente conocida y de confianza, este comando puede no ser válido o su ejecución puede ser peligrosa.**

 **¿Quiere ejecutar este comando?**

## <a name="uielement-list"></a>Lista de UIElement
 Comando de cuadro de texto del archivo .pdb que se va a ejecutar.

 Ejecutar: permite que se ejecute el comando.

 No ejecutar: detiene la ejecución del comando y la descarga del archivo del servidor de origen.

## <a name="see-also"></a>Vea también
- [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Seguridad del depurador](../debugger/debugger-security.md)
- [Servidor de origen](/windows/desktop/Debug/source-server-and-source-indexing)
