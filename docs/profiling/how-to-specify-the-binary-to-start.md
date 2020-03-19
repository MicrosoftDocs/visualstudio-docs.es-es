---
title: 'Cómo: Especificar el binario de inicio | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fd3379b9769cfd6bfe1335b12545e635a9bde782
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778692"
---
# <a name="how-to-specify-the-binary-to-start"></a>Cómo: Especificar el binario de inicio

Para generar perfiles de binarios, como los archivos DLL, debe escribir información en el cuadro de diálogo **\<Destino > Páginas de propiedades**. Esta información indica dónde puede encontrar el proyecto DLL la aplicación que realiza la llamada.

1. En el **Explorador de rendimiento**, haga clic con el botón derecho en el binario de destino y después haga clic en **Propiedades**.

2. En el cuadro de diálogo **Páginas de propiedades**, haga clic en las propiedades **Iniciar**.

3. Seleccione la casilla **Invalidar propiedades del proyecto**.

4. En el cuadro de texto **Ejecutable para iniciar**, especifique la ubicación del archivo.

5. En el cuadro de texto **Argumentos**, especifique los argumentos necesarios para iniciar la aplicación.

6. En el cuadro de texto **Directorio de trabajo**, especifique la ubicación del directorio.

7. Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también

[Configuración de sesiones de rendimiento](../profiling/configuring-performance-sessions.md)
