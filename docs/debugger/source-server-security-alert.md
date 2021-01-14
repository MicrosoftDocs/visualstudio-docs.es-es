---
title: Alerta de seguridad del servidor de origen | Microsoft Docs
description: Obtenga información sobre la advertencia de la alerta de seguridad del servidor de origen del depurador de Visual Studio. Tenga en cuenta las amenazas de seguridad que pueden existir al usar el servidor de origen.
ms.custom: SEO-VS-2020
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf62abb91411048f46bfe7240074bd86c119bcd4
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149123"
---
# <a name="source-server-security-alert"></a>Alerta de seguridad del servidor de origen
Si utiliza el servidor de origen, trabaje únicamente con archivos de símbolos procedentes de una ubicación conocida y de confianza.

 Esta advertencia aparece cuando habilita la compatibilidad con el servidor de origen. Los comandos de servidor de origen se incrustan en archivos de símbolos de depuración (archivos **\*.pdb**). Asegúrese de que sabe de dónde provienen los archivos PDB.

> [!IMPORTANT]
> Al usar un servidor de origen, debe tener en cuenta estas posibles amenazas de seguridad: En el archivo PDB de la aplicación se pueden incrustar comandos arbitrarios, por lo que debe asegurarse de colocar únicamente los que quiera ejecutar en el archivo srcsrv.ini. Todo intento de ejecutar un comando no incluido en el archivo srcsvr.ini provocará la aparición de un cuadro de diálogo de confirmación. Para obtener más información, vea [Advertencia de seguridad: El depurador debe ejecutar un comando que no es de confianza](../debugger/security-warning-debugger-must-execute-untrusted-command.md). No se realiza ninguna validación de los parámetros de comando, por lo que debe tener cuidado con los comandos de confianza. Por ejemplo, si confiara en cmd.exe, un usuario malintencionado podría especificar parámetros que harían que el comando fuera peligroso.

## <a name="see-also"></a>Vea también
- [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Seguridad del depurador](../debugger/debugger-security.md)
- [Servidor de origen](/windows/desktop/Debug/source-server-and-source-indexing)
