---
title: Visualización de datos y datos adjuntos de diagnóstico para pruebas de carga en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, data and diagnostics attachments
ms.assetid: 73309bdd-437a-4eb0-88c8-702c3e24b9b0
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 228f8306b803fcbd0e83e23e5b8e919dc2116c37
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2018
ms.locfileid: "39382469"
---
# <a name="how-to-view-data-and-diagnostic-attachments-using-the-load-test-analyzer"></a>Cómo: Ver datos y datos adjuntos de diagnóstico mediante el Analizador de pruebas de carga

Antes de ejecutar una prueba de carga, puede seleccionar una configuración de pruebas que especifique los adaptadores de datos y diagnósticos que desea usar. Una vez finalizada la prueba de carga, use el **Analizador de pruebas de carga** para ver los detalles de esos adaptadores de datos y diagnósticos mientras analiza los resultados. Para ver los detalles de los adaptadores de datos y diagnósticos, haga clic en el botón **Ver datos adjuntos de datos y diagnósticos** en la barra de herramientas del **Analizador de pruebas de carga**. Por ejemplo, si la prueba de carga tenía configurado el adaptador de información del sistema en la configuración de pruebas, puede ver la información del sistema del equipo empleado para ejecutar la prueba de carga.

![Cuadro de diálogo Elegir datos adjuntos del adaptador de datos de diagnóstico](../test/media/load_adapterdialog.png)

Otro ejemplo es una prueba de carga que incluye el adaptador de IntelliTrace en la configuración de pruebas. El adaptador de IntelliTrace le permite abrir la página **Resumen de IntelliTrace**.

![Resumen de IntelliTrace](../test/media/load_intellitrace.png)

Para obtener más información, vea [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md) y [Cómo: Recopilar datos de IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).

## <a name="to-view-data-and-diagnostic-attachments-in-a-load-test-from-the-load-test-analyzer"></a>Para ver datos y datos adjuntos de diagnóstico en una prueba de carga desde el Analizador de prueba de carga

1.  Una vez completada una prueba de carga, o después de abrir el resultado de una prueba de carga, en la barra de herramientas del **Analizador de pruebas de carga**, elija **Ver datos adjuntos de datos y diagnósticos**.

     Aparecerá el cuadro de diálogo **Elegir datos adjuntos del adaptador de datos de diagnóstico**.

2.  Seleccione los datos adjuntos del adaptador de datos de diagnóstico que desee analizar y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

- [Analizar los resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
