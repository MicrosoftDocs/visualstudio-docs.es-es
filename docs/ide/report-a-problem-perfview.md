---
title: Recopilación del seguimiento de ETL con PerfView
ms.date: 06/27/2019
ms.topic: conceptual
helpviewer_keywords:
- perfview
- ETL Trace
author: mikeblome
ms.author: mblome
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: 6b1f61888fa642ed544c6da7d1cf77c43b52b2d9
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461550"
---
# <a name="collect-an-etl-trace-with-perfview"></a>Recopilación del seguimiento de ETL con PerfView

PerfView es una herramienta que crea archivos ETL (registro de seguimiento de eventos) basados en el [Seguimiento de eventos para Windows](/windows/desktop/ETW/event-tracing-portal) que pueden resultar útiles para solucionar diferentes tipos de problemas con Visual Studio. Ocasionalmente, cuando informa un problema, el equipo del producto puede solicitarle que ejecute PerfView para recopilar información adicional.

## <a name="install-perfview"></a>Instalación de PerfView

Descargue PerfView del [Centro de descarga de Microsoft](http://www.microsoft.com/download/details.aspx?id=28567).

## <a name="run-perfview"></a>Ejecución de PerfView

1. Haga clic derecho en **PerfView.exe** en el Explorador de Windows y elija **Ejecutar como administrador** como administrador.
1. En el menú Collect (Recopilar), elija **Collect** (Recopilar).
1. Active **Zip** (Comprimir), **Merge** (Combinar), and **ThreadTime** (Tiempo de subproceso).
1. Aumente **Circular MB** (MB circular) a 1000.
1. Cambie **Current Dir** (Dir actual) para guardar los seguimientos de ETL en una carpeta especificada y el archivo de datos si va a recopilar más de una vez.
1. Para iniciar el registro de los datos, seleccione el botón **Start Collection** (Iniciar la recopilación).
1. Para detener el registro de los datos, seleccione el botón **Stop Collection** (Detener la recopilación). El archivo PrefView.etl.zip se guardará en el directorio especificado.

PerfView puede almacenar solo los datos más recientes que quepan en su búfer. Por lo tanto, intente detener la recolección en cuanto perciba que Visual Studio empieza a bloquearse o ralentizarse. No recopile durante más de 30 segundos después de encontrar un problema.

Para obtener más información, vea el [tutorial de PerfView en Channel9](http://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command).
