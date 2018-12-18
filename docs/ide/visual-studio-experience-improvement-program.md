---
title: Programa para la mejora de la experiencia del usuario
description: Obtenga información sobre cómo administrar la configuración de privacidad en Visual Studio.
ms.date: 05/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba68d0d369d178606777944c9dc4dcd633a503f4
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2018
ms.locfileid: "36280649"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Programa para la mejora de la experiencia del usuario de Visual Studio

El Programa para la mejora de la experiencia del usuario de Visual Studio (VSCEIP) está diseñado para ayudar a Microsoft a mejorar Visual Studio con el tiempo. Este programa [recopila información sobre errores](../ide/diagnostic-data-collection.md), hardware del equipo y el uso que se hace de Visual Studio, sin interrumpir a los usuarios en sus tareas en el equipo. La información recopilada ayuda a Microsoft a identificar qué características se deben mejorar. Este documento explica cómo participar o no en el VSCEIP.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]

## <a name="opt-in-or-out"></a>Participar o no en el programa

VSCEIP está activado de forma predeterminada. Para desactivarlo o volver a activarlo, siga estas instrucciones:

1. Inicie Visual Studio.

1. En el menú **Ayuda**, elija **Enviar comentarios** y, después, seleccione **Configuración**.

   Se abre el cuadro de diálogo **Programa para la mejora de la experiencia de Visual Studio**.

1. Para dejar de participar, seleccione **No, prefiero no participar** y **Aceptar**.
   Para participar, seleccione **Sí, deseo participar** y **Aceptar**.

   ![Cuadro de diálogo Programa para la mejora de la experiencia de Visual Studio](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Configuración del Registro

Si instala [Build Tools para Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017), debe actualizar el Registro para configurar el VSCEIP. Los clientes de empresa pueden crear una directiva de grupo para utilizar o no utilizar el VSCEIP configurando una directiva basada en el Registro.

La clave del Registro y la configuración necesarias son:

En un sistema operativo de 64 bits, la clave = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM** En un sistema operativo de 32 bits, la clave = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM** Cuando la directiva de grupo está habilitada, la clave = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

Entry = **OptIn**

Value = (DWORD)
- **0** es no participar (desactivar el VSCEIP)
- **1** es participar (activar el VSCEIP)

> [!CAUTION]
> Una modificación incorrecta del Registro puede provocar daños graves en el sistema. Antes de realizar cambios en el Registro, realice una copia de seguridad de los datos valiosos del equipo. También puede utilizar la opción de inicio **La última configuración válida conocida** si detecta problemas una vez aplicados los cambios manuales.

Para obtener más información sobre los datos que recopila, procesa o transmite el VSCEIP, consulte la [Declaración de privacidad de Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="see-also"></a>Vea también

* [Información de diagnóstico recopilada por Visual Studio](diagnostic-data-collection.md)
* [Hable con nosotros](../ide/talk-to-us.md)
* [Cómo notificar un problema con Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)
* [Comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/)
* [Declaración de privacidad de Microsoft](https://privacy.microsoft.com/privacystatement)
