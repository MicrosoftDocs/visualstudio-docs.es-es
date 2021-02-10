---
title: Recopilación del seguimiento de ETL con PerfView
ms.date: 09/27/2019
ms.topic: how-to
helpviewer_keywords:
- perfview
- ETL Trace
author: corob-msft
ms.author: corob
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: 6f0696a24f04d2cba52994c86a3475f56d3e7947
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970717"
---
# <a name="collect-an-etl-trace-with-perfview"></a>Recopilación del seguimiento de ETL con PerfView

PerfView es una herramienta que crea archivos ETL (registro de seguimiento de eventos) basados en el [Seguimiento de eventos para Windows](/windows/desktop/ETW/event-tracing-portal) que pueden resultar útiles para solucionar diferentes tipos de problemas con Visual Studio. Ocasionalmente, cuando informa un problema, el equipo del producto puede solicitarle que ejecute PerfView para recopilar información adicional.

## <a name="install-perfview"></a>Instalación de PerfView

Descargue PerfView de [GitHub](https://github.com/Microsoft/perfview/blob/master/documentation/Downloading.md).

## <a name="run-perfview"></a>Ejecución de PerfView

1. Haga clic derecho en **PerfView.exe** en el Explorador de Windows y elija **Ejecutar como administrador** como administrador.
1. En el menú Collect (Recopilar), elija **Collect** (Recopilar).
1. Active **Zip** (Comprimir), **Merge** (Combinar), and **ThreadTime** (Tiempo de subproceso).
1. Aumente **Circular MB** (MB circular) a 1000.
1. Cambie **Current Dir** (Dir actual) para guardar los seguimientos de ETL en una carpeta especificada y el archivo de datos si va a recopilar más de una vez.
1. Para iniciar el registro de los datos, seleccione el botón **Start Collection** (Iniciar la recopilación).
1. Para detener el registro de los datos, seleccione el botón **Stop Collection** (Detener la recopilación). El archivo PrefView.etl.zip se guardará en el directorio especificado.

PerfView puede almacenar solo los datos más recientes que quepan en su búfer. Por lo tanto, intente detener la recolección en cuanto perciba que Visual Studio empieza a bloquearse o ralentizarse. No recopile durante más de 30 segundos después de encontrar un problema.

Para obtener más información, vea el [tutorial de PerfView en Channel9](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command).
