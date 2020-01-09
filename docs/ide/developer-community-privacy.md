---
title: Datos privados para los informes de problemas
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
ms.openlocfilehash: 09f3e5fed93cac3a251e4b7cdcaa988e63ff8741
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596273"
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

- Archivos PerfWatson, si la colección Watson está habilitada

- Archivos de registro de LiveShare, si existen

- Archivos de registro de Xamarin, si existen

- Archivos de registro de NuGet, si existen

- Archivos de registro del depurador web, si existen

- Registros del centro de servicio y registros de errores de MEF, si existen

- Registros de Python, si existen

- Registros de Windows Forms, si existen

- Una captura de pantalla, si opta por incluirla

- Datos de grabación, si decide incluir una grabación, que incluya:

  - Pasos para reproducir el problema

  - Archivo de seguimiento ETL

  - Archivo de volcado de memoria

> [!NOTE]
> Los archivos de registro, las instantáneas y los datos de registro se envían a Microsoft solo cuando se proporciona el permiso; para ello, se envía el informe de problemas con el que se incluyen. Puede ver los archivos que se incluyen en el paso "Resumen" de la ventana "Notificar un problema" (vea la captura de pantalla incluida en esta nota). Los registros y archivos recopilados se almacenan en la carpeta %temp% y se limpian periódicamente y después de cada carga. Si no quiere incluir un registro en el informe de problemas, elimine el archivo de la carpeta %temp% antes de enviar el informe.
  > ![Notificar un problema: resumen de los registros recopilados](media/report-a-problem-logs-collected.png)


## <a name="see-also"></a>Vea también

- [Cómo notificar un problema con Visual Studio 2017](how-to-report-a-problem-with-visual-studio.md)
- [Privacidad de datos de los informes de problemas de C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)
