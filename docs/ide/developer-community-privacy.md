---
title: Datos privados para los informes de problemas
ms.date: 06/21/2018
ms.topic: conceptual
helpviewer_keywords:
- developer community privacy
- privacy, developer community
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3db48578d2b316ddd203316a15536b144cb28cf
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55910459"
---
# <a name="developer-community-data-privacy"></a>Privacidad de datos de la Comunidad de desarrolladores

De forma predeterminada, toda la información de los informes de problemas sobre la [Comunidad de desarrolladores](https://developercommunity.visualstudio.com/), incluidos los comentarios y las respuestas, está visible de forma pública. Esto es una ventaja, porque permite que toda la comunidad pueda ver los problemas, las soluciones y las alternativas que han encontrado otros usuarios. Pero si le preocupa la privacidad de sus datos o su identidad, tiene distintas opciones.

## <a name="identity-privacy"></a>Privacidad de identidad

Si le preocupa que se revele su identidad, [cree una cuenta de Microsoft](https://signup.live.com/) que no divulgue ningún detalle sobre usted. Utilice esta cuenta para crear el informe.

## <a name="data-privacy"></a>Privacidad de datos

Si le preocupa la publicidad de los datos, no ponga nada que no quiera revelar en el título ni en el contenido del informe inicial, que siempre es público. En su lugar, cree el informe y, luego, tenga en cuenta que deberá enviar detalles de forma privada en un comentario independiente. Una vez creado el informe de problemas, puede especificar quién puede ver las respuestas y los datos adjuntos:

1. En el informe que ha creado, elija **Agregar comentario** para crear una descripción privada del problema.

2. En el editor de respuestas, use el control que aparece debajo de los botones **Enviar** y **Cancelar** para especificar los destinatarios de la respuesta. Elija **Viewable by moderators and the original poster** (Visible para los moderadores y el autor de la publicación original) para limitar la visibilidad a los empleados de Microsoft y a usted mismo.

   ![Control de privacidad en la Comunidad de desarrolladores](media/developer-community-privacy-control.png)

   Solo las personas que especifique podrán ver el comentario y las imágenes, los vínculos o el código que incluya en él. Las respuestas incluidas dentro del comentario tendrán la misma visibilidad que el comentario original. Esto se cumple aunque el control de privacidad de las respuestas no muestre el estado de visibilidad restringida correctamente.

3. Agregue la descripción y cualquier otra información, imágenes y datos adjuntos de archivo necesarios para la reproducción. Elija el botón **Enviar** para enviar esta información de forma privada.

   > [!NOTE]
   > Hay un límite de 2 GB en archivos adjuntos y un máximo de 10 archivos. Si tiene que cargar un archivo más grande, puede enviar un nuevo informe de problemas o solicitar una dirección URL de carga de un empleado de Microsoft en un comentario privado.

Para preservar su privacidad y mantener la información confidencial fuera de la vista pública, tenga cuidado de mantener todas las interacciones con Microsoft en forma de respuestas a un comentario de visibilidad restringida. Las respuestas a otros comentarios pueden provocar que accidentalmente se divulgue información confidencial.

## <a name="data-we-collect"></a>Datos que recopilamos

Si se inicia **Report a problem** (Notificar un problema) desde el Instalador de Visual Studio, recopilamos el registro de instalación más reciente.

Si se inicia **Report a problem** (Notificar un problema) desde Visual Studio, recopilamos uno o varios de los siguientes tipos de datos:

- Entradas Watson y .NET del registro de eventos

- Archivo de registro de actividad en memoria de Visual Studio

- Archivos PerfWatson, si la colección Watson está habilitada, desde la carpeta *VSFeedbackPerfWatsonData*

- Archivos de registro LiveShare, si existen, desde la carpeta *VSFeedbackVSRTCLogs*

- Archivos de registro de Xamarin, si existen, desde *%LOCALAPPDATA%\Xamarin\Logs*

- Archivos de registro de NuGet, si existen, desde *%TEMP%\NuGetScratch\nuget-dg\nugetSpec.dg*

- Archivos de registro del depurador web, si existen:

   - *%TEMP%\vscode-chrome-debug.txt*

   - *%TEMP%\vscode-node-debug2.txt*

   - *%TEMP%\vscode-edge-debug.txt*

- Una captura de pantalla, si opta por incluirla

- Datos de grabación, si decide incluir una grabación, que incluya:

   - Pasos para reproducir el problema

   - Archivo de seguimiento ETL

   - Archivo de volcado de memoria

    > [!NOTE]
    > Puede eliminar cualquiera de los datos de grabación que no quiera enviar antes de enviar el informe.

## <a name="see-also"></a>Vea también

- [Cómo notificar un problema con Visual Studio 2017](how-to-report-a-problem-with-visual-studio-2017.md)
- [Privacidad de datos de los informes de problemas de C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)