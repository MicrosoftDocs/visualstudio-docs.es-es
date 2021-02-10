---
title: Serializar la información de símbolos | Microsoft Docs
description: Obtenga información sobre cómo serializar símbolos que debe tener para analizar la aplicación y cómo la serialización de símbolos agrega símbolos al archivo .vsp.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bb9e965fb1b863d7e5837fe45a5d832fadcbc5c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907046"
---
# <a name="how-to-serialize-symbol-information"></a>Procedimiento Serializar la información de símbolos
Puede serializar símbolos que debe tener para analizar la aplicación. La serialización de símbolos agrega símbolos al archivo .*vsp*. Al agregar información de símbolos al archivo .*vsp*, otros usuarios pueden analizar un informe de rendimiento sin tener acceso a los símbolos originales. Si no se serializan los símbolos, debe tener archivos .*exe* y .*pdb* originales instrumentados para analizar el archivo .*vsp*.

### <a name="to-automatically-serialize-symbol-information"></a>Para serializar información de símbolos automáticamente

1. En el menú **Herramientas** , haga clic en **Opciones**.

     Se mostrará el cuadro de diálogo **Opciones**.

2. Haga clic en **Herramientas de rendimiento**.

3. En **Configuración general**, seleccione **Serializar información de símbolos automáticamente**.

## <a name="see-also"></a>Vea también
- [Configuración de sesiones de rendimiento](../profiling/configuring-performance-sessions.md)
- [Cómo: Hacer referencia a información de símbolos de Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [Cómo: Guardar archivos del informe analizado](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))
