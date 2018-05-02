---
title: Inclusión de grabaciones de la pantalla y de voz durante las pruebas mediante la configuración de prueba en Visual Studio
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, recording desktop video
ms.assetid: 2cefe8c2-430a-4cb4-bbe0-f3edb2e5bc03
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 827b76f3b4b40f59fe22b3c5424c6d8c13087809
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-include-recordings-of-the-screen-and-voice-during-tests-using-test-settings"></a>Cómo: Incluir grabaciones de la pantalla y de voz durante las pruebas mediante la configuración de prueba

En el editor de configuración de Visual Studio, puede configurar el adaptador de datos de diagnóstico que graba la pantalla y la voz del usuario que ejecuta la prueba. Este adaptador de datos de diagnóstico guarda una grabación de pantalla y voz de la sesión de escritorio durante la prueba. La grabación se guarda con el resultado de la prueba o se puede adjuntar a un error. Otros miembros del equipo pueden usar la grabación para aislar defectos de la aplicación que son difíciles de reproducir.

> [!WARNING]
> Las grabaciones de pantalla y voz no admiten configuraciones de varios monitores.

La grabadora de pantalla y voz se puede usar con pruebas manuales o automatizadas. Por ejemplo, si ejecuta una prueba de IU codificada de forma remota, es posible que desee grabar el escritorio para ver la prueba de IU codificada mientras se ejecuta. Para obtener más información sobre cómo capturar una grabación de vídeo de forma remota, consulte [Cómo: Configurar el agente de pruebas para ejecutar pruebas que interactúen con el escritorio](../test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md).

## <a name="to-configure-screen-and-voice-recording-for-your-test-settings"></a>Para configurar la grabación de pantalla y voz para la configuración de pruebas

1.  Abra la configuración de pruebas para la que va a configurar grabaciones de pantalla y voz. Para obtener más información, vea [Recopilar datos de diagnóstico durante las pruebas (VSTS)](/vsts/manual-test/collect-diagnostic-data) o [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md).

2.  En la configuración de pruebas, seleccione el **Rol** que se usará para grabar la pantalla y la voz.

    > [!NOTE]
    > En el caso de las pruebas manuales y automatizadas, seria el equipo que ejecuta las pruebas.

3.  Seleccione **Grabadora de pantalla y voz** y, a continuación, elija **Configurar**.

     Se muestra el cuadro de diálogo Configurar adaptador de datos de diagnóstico: Grabadora de pantalla y voz.

     ![Configuración de vídeo](../test/media/testsettingvideoconfiggdr.png "TestSettingVideoConfigGDR")

4.  (Opcional) Seleccione **Habilitar grabación de voz** para capturar el contenido de audio en la grabación.

5.  (Opcional) Active la casilla situada al lado de **Guardar grabación si se supera el caso de prueba** para especificar que se guarden las grabaciones de pantalla y voz de las pruebas tanto superadas como no superadas.

    > [!WARNING]
    > Si selecciona **Guardar grabación si se supera el caso de prueba**, la grabación se almacena con los resultados de la prueba, lo que consume espacio de almacenamiento en el servidor. Puede usar la herramienta Test Attachment Cleaner para limpiar estos datos adjuntos.

6.  En **Calidad de la grabación de pantalla**, configure las siguientes opciones de lista desplegable:

    1.  **Velocidad de fotogramas:** especifica cuántos fotogramas por segundo desea usar en la grabación de pantalla y voz. El valor predeterminado es 4 fotogramas por segundo. Se pueden especificar valores entre 2 y 20.

    2.  **Velocidad de bits:** especifique cuántos kilobytes por segundo se usarán en las grabaciones de pantalla y voz. El valor predeterminado es 512. Se pueden especificar valores entre 512 y 10.000.

    3.  **Calidad (1-100):** puede especificar la calidad de la grabación de pantalla y voz seleccionando un intervalo entre 1 y 100. El valor predeterminado es de 50 (intervalo medio).

7.  Elija **Aceptar**. Ahora, la configuración del recopilador de seguimiento de diagnóstico está establecida y guardada para su configuración de pruebas.

    > [!TIP]
    > Para restablecer la configuración de este adaptador de datos de diagnóstico, elija **Restablecer la configuración predeterminada** para Visual Studio y **Restablecer valores predeterminados** para Microsoft Test Manager.

## <a name="see-also"></a>Vea también

- [Recopilar datos de diagnóstico durante las pruebas (VSTS)](/vsts/manual-test/collect-diagnostic-data)
- [Recopilar datos de diagnóstico en pruebas manuales (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests)
- [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md)
- [Ejecutar pruebas manuales (VSTS)](/vsts/manual-test/getting-started/run-manual-tests)