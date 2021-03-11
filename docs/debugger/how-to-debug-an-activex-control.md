---
title: Depuración de un control ActiveX | Microsoft Docs
description: Vea cómo depurar un control ActiveX. Debe especificar un archivo ejecutable como contenedor. Puede hacerlo en las páginas de Propiedades del proyecto o al comenzar la depuración.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6728b498da91f540d92182ad60f23e490d614948
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160400"
---
# <a name="how-to-debug-an-activex-control"></a>Procedimiento Depuración de un control ActiveX

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para obtener más información, vea [Restablecer la configuración](../ide/environment-settings.md#reset-settings).

Para depurar el control ActiveX, debe especificar un contenedor (ejecutable) en el que ejecutar el control.

## <a name="to-specify-a-container-for-the-debug-session"></a>Para especificar un contenedor para la sesión de depuración

1. En el Explorador de soluciones, seleccione el proyecto.

2. En el menú **Ver**, seleccione **Páginas de propiedades**.

3. En el cuadro de diálogo **Páginas de propiedades del proyecto**, abra la carpeta **Propiedades de configuración** y seleccione **Depuración**.

4. Debajo de la categoría **Depuración**, busque la propiedad **Comando**.

5. Especifique el nombre de ruta de acceso para el contenedor. Por ejemplo, C:\Archivos de programa\Internet Explorer\IEXPLORE.EXE.

6. Si especifica Internet Explorer como el contenedor y está utilizando Active Desktop, escriba `/new` en el cuadro **Argumentos del comando**.

7. Haga clic en **Aceptar**.

     Si no especifica ningún contenedor en el cuadro de diálogo **Páginas de propiedades del proyecto**, puede especificarlo al iniciar la depuración. Cuando se selecciona un comando de ejecución para iniciar la depuración, aparece el [cuadro de diálogo Archivo ejecutable para sesión de depuración](../debugger/executable-for-debugging-session-dialog-box.md). Especifique el nombre de la ruta de acceso del contenedor en el cuadro de diálogo.

## <a name="see-also"></a>Vea también

- [Controles ActiveX](/cpp/mfc/activex-controls)
- [Prueba de propiedades y eventos con un contenedor de prueba](/cpp/mfc/testing-properties-and-events-with-test-container)
- [Depurar COM y ActiveX](../debugger/com-and-activex-debugging.md)
- [Depurar en Visual Studio](../debugger/index.yml)
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
