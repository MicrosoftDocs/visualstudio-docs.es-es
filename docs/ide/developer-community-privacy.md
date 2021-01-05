---
title: Datos privados para los informes de problemas
description: Aprenda a proteger mejor los datos privados al crear informes de problemas para que los revise el foro de la comunidad Developer Community.
ms.custom: SEO-VS-2020
ms.date: 06/21/2018
ms.topic: conceptual
helpviewer_keywords:
- developer community privacy
- privacy, developer community
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dccf962aef39227388f86134a9dd1f8c96440a3c
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668552"
---
# <a name="developer-community-data-privacy"></a>Privacidad de datos de la Comunidad de desarrolladores

De forma predeterminada, toda la información de los informes de problemas sobre la [Comunidad de desarrolladores](https://aka.ms/feedback/suggest?space=8), incluidos los comentarios y las respuestas, está visible de forma pública. Esto es una ventaja, porque permite que toda la comunidad pueda ver los problemas, las soluciones y las alternativas que han encontrado otros usuarios. Pero si le preocupa la privacidad de sus datos o su identidad, tiene distintas opciones.

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
   > En el sitio web de Developer Community, hay un límite de 2 GB en archivos adjuntos y un máximo de diez archivos. Si tiene que cargar un archivo más grande, puede enviar un nuevo informe de problemas o solicitar una dirección URL de carga de un empleado de Microsoft en un comentario privado.
   > Cuando cerremos un problema, los datos adjuntos asociados se eliminarán después de noventa días.

Para preservar su privacidad y mantener la información confidencial fuera de la vista pública, tenga cuidado de mantener todas las interacciones con Microsoft en forma de respuestas a un comentario de visibilidad restringida. Las respuestas a otros comentarios pueden provocar que accidentalmente se divulgue información confidencial.

## <a name="data-we-collect"></a>Datos que recopilamos

Si se inicia **Report a problem** (Notificar un problema) desde el Instalador de Visual Studio, recopilamos el registro de instalación más reciente.

Si se inicia **Report a problem** (Notificar un problema) desde Visual Studio, recopilamos uno o varios de los siguientes tipos de datos:

- Entradas Watson y .NET del registro de eventos

- Archivo de registro de actividad en memoria de Visual Studio

- Archivos PerfWatson, si la colección Watson está habilitada

- Archivos de registro de LiveShare, si existen

- Archivos de registro de Xamarin, si existen

- Archivos de registro de NuGet, si existen

- Archivos de registro del depurador web, si existen

- Registros del centro de servicio y registros de errores de MEF, si existen

- Registros de Python, si existen

- Registros del editor de LSP de Razor, si existen

- Registros de Windows Forms, si existen

- Una captura de pantalla, si opta por incluirla

- Datos de grabación, si decide incluir una grabación, que incluya:

  - Pasos para reproducir el problema

  - Archivo de seguimiento ETL

  - Archivo de volcado de memoria

> [!NOTE]
> Los archivos de registro, las capturas de pantalla y los datos de grabación que envíe pueden aumentar significativamente la capacidad de Microsoft para comprender su problema y atenderlo.  Por lo tanto, se recomienda incluirlos. Para proteger su privacidad, los archivos de registro, las instantáneas y los datos de registro adjuntos se envían a Microsoft solo cuando se proporciona el permiso; para ello, se envía el informe de problemas con el que se incluyen. Puede ver los archivos que se incluyen en el paso "Resumen" de la ventana "Notificar un problema" antes de enviar el informe. Para excluir los archivos de registro del sistema del informe, desactive "Asociar registros del sistema" en el paso "Resumen". Como referencia, vea la siguiente captura de pantalla. 
  > ![Notificar un problema: resumen de los registros recopilados](media/report-a-problem-logs-collected.png)


## <a name="see-also"></a>Vea también

- [Cómo notificar un problema con Visual Studio 2017](how-to-report-a-problem-with-visual-studio.md)
- [Privacidad de datos de los informes de problemas de C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)
