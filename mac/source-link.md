---
title: Depuración de paquetes NuGet con el vínculo de origen
description: En este artículo se describe la característica de vínculo de origen en Visual Studio para Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 307196dc7e33d268c45a9bb126c002ad426c5558
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583923"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Depuración de paquetes NuGet con el vínculo de origen

La tecnología del vínculo de origen permite a los desarrolladores depurar el código fuente de los ensamblados de .NET de NuGet que se envían con .PDB con vínculos a archivos de código fuente. El vínculo de origen se ejecuta cuando los desarrolladores crean el paquete NuGet e inserta metadatos de control de código fuente dentro de los ensamblados y el paquete. Cuando el vínculo de origen está habilitado en Visual Studio para Mac, el IDE detectará si los archivos de origen están disponibles para los paquetes instalados. A continuación, Visual Studio para Mac le ofrecerá la descarga, lo que le permitirá recorrer el código del paquete. El vínculo de origen también funciona con el código de la biblioteca de clases base de Mono, lo que le permite depurar paso a paso por instrucciones también el código de .NET Framework. SourceLink proporciona metadatos de control de origen para crear una excelente experiencia de depuración.

> [!NOTE]
> Visual Studio para Mac no admite de momento servidores de símbolos. Debido a esto, no se admite el vínculo de origen con metadatos hospedados en servidores de símbolos.

## <a name="enable-source-link"></a>Habilitación del vínculo de origen

Para habilitar el vínculo de origen en Visual Studio para Mac, vaya a **Visual Studio > Preferencias... > Proyectos > Depurador** y asegúrese de que esté activada la casilla **Recorrer el código externo**.

![Captura de pantalla del cuadro de diálogo de preferencias que muestra la casilla Recorrer el código externo](media/source-link1.png)

Puede cambiar la configuración en **Descargar código externo** para que se adapte a sus preferencias:
* Preguntar: Visual Studio para Mac le pedirá que descargue el código externo.
* Siempre: Visual Studio para Mac descargará el código externo automáticamente.
* Nunca: Visual Studio para Mac no descargará el código externo relacionado.

La opción seleccionada de forma predeterminada es **Preguntar**. Recibirá el siguiente mensaje cuando se encuentre código externo para un paquete NuGet:

![Captura de pantalla del mensaje que aparece cuando se encuentra código externo para un paquete NuGet](media/source-link2.png)


## <a name="see-also"></a>Vea también

- El [repositorio de GitHub del vínculo de origen](https://github.com/dotnet/sourcelink/blob/master/README.md)
- La [documentación de .NET](/dotnet/standard/library-guidance/sourcelink) en el vínculo de origen y para obtener más información sobre cómo agregar compatibilidad con vínculos de origen a paquetes.