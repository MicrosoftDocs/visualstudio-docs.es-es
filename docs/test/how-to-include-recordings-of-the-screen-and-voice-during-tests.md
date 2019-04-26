---
title: Icono Grabar pantalla y voz durante las pruebas
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, recording desktop video
ms.assetid: 2cefe8c2-430a-4cb4-bbe0-f3edb2e5bc03
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 663f89c65604c42b356830b3a0c6d61bdcb265e3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62950119"
---
# <a name="how-to-include-recordings-of-the-screen-and-voice-during-tests-using-test-settings"></a>Procedimiento Incluir grabaciones de la pantalla y de voz durante las pruebas mediante la configuración de pruebas

En el editor de configuración de Visual Studio, puede configurar el adaptador de datos de diagnóstico que graba la pantalla y la voz del usuario que ejecuta la prueba. Este adaptador de datos de diagnóstico guarda una grabación de pantalla y voz de la sesión de escritorio durante la prueba. La grabación se guarda con el resultado de la prueba o se puede adjuntar a un error. Otros miembros del equipo pueden usar la grabación para aislar defectos de la aplicación que son difíciles de reproducir.

> [!WARNING]
> Las grabaciones de pantalla y voz no admiten configuraciones de varios monitores.

La grabadora de pantalla y voz se puede usar con pruebas manuales o automatizadas. Por ejemplo, si ejecuta una prueba de IU codificada de forma remota, es posible que desee grabar el escritorio para ver la prueba de IU codificada mientras se ejecuta. Para obtener más información sobre cómo capturar una grabación de pantalla y voz de forma remota, vea [Cómo: Configurar el agente de pruebas para ejecutar pruebas que interactúen con el escritorio](../test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-configure-screen-and-voice-recording-for-your-test-settings"></a>Para configurar la grabación de pantalla y voz para la configuración de pruebas

1. Abra la configuración de pruebas para la que va a configurar grabaciones de pantalla y voz. Para obtener más información, vea [Collect diagnostic data while testing (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts) [Recopilar datos de diagnóstico durante las pruebas (Azure Test Plans)] o [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md).

2. En la configuración de pruebas, seleccione el **Rol** que se usará para grabar la pantalla y la voz.

    > [!NOTE]
    > En el caso de las pruebas manuales y automatizadas, seria el equipo que ejecuta las pruebas.

3. Seleccione **Grabadora de pantalla y voz** y, a continuación, elija **Configurar**.

     Se muestra el cuadro de diálogo **Configurar adaptador de datos de diagnóstico: Grabadora de pantalla y voz**.

     ![Configuración de vídeo](../test/media/testsettingvideoconfiggdr.png)

4. (Opcional) Seleccione **Habilitar grabación de voz** para capturar el contenido de audio en la grabación.

5. (Opcional) Active la casilla situada al lado de **Guardar grabación si se supera el caso de prueba** para especificar que se guarden las grabaciones de pantalla y voz de las pruebas tanto superadas como no superadas.

    > [!WARNING]
    > Si selecciona **Guardar grabación si se supera el caso de prueba**, la grabación se almacena con los resultados de la prueba, lo que consume espacio de almacenamiento en el servidor. Puede usar la herramienta **Test Attachment Cleaner** para limpiar estos datos adjuntos.

6. En **Calidad de la grabación de pantalla**, configure las siguientes opciones de lista desplegable:

    1. **Velocidad de fotogramas**: Especifique cuántos fotogramas por segundo quiere usar en la grabación de pantalla y voz. El valor predeterminado es 4 fotogramas por segundo. Se pueden especificar valores entre 2 y 20.

    2. **Velocidad de bits**: Especifique cuántos kilobytes por segundo se van a usar en las grabaciones de pantalla y voz. El valor predeterminado es 512. Se pueden especificar valores entre 512 y 10.000.

    3. **Calidad (1-100)**: Puede especificar la calidad de la grabación de pantalla y voz si selecciona un intervalo entre 1 y 100. El valor predeterminado es de 50 (intervalo medio).

7. Elija **Aceptar**. Ahora, la configuración del recopilador de seguimiento de diagnóstico está establecida y guardada para su configuración de pruebas.

    > [!TIP]
    > Para restablecer la configuración de este adaptador de datos de diagnóstico, elija **Restablecer la configuración predeterminada** para Visual Studio y **Restablecer valores predeterminados** para Microsoft Test Manager.

## <a name="see-also"></a>Vea también

- [Collect diagnostic data while testing (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts) [Recopilar datos de diagnóstico durante las pruebas (Azure Test Plans)]
- [Collect diagnostic data in manual tests (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts) [Recopilar datos de diagnóstico en pruebas manuales (Azure Test Plans)]
- [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md)
- [Run manual tests (Azure Test Plans)](/azure/devops/test/run-manual-tests?view=vsts) [Ejecutar pruebas manuales (Azure Test Plans)]