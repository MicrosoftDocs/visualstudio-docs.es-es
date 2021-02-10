---
title: Cuándo cambian las cargas de paquetes después de una publicación
description: Al crear un diseño, aprenda cómo determinar si las cargas del paquete cambiaron después de la publicación de una versión.
ms.date: 05/22/2019
ms.topic: how-to
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: bd0013df051def28c57552c0aeb733888d55e9b6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905543"
---
# <a name="package-payload-changes"></a>Cambios de carga de paquete

Algunas cargas de paquetes pueden cambiar después de la publicación de una versión. Cuando usted u otra persona crea un diseño, este comportamiento podría dar lugar a diferentes contenidos en el diseño, dependiendo de cuándo se creara un diseño.

## <a name="verify-that-a-layout-includes-package-payload-changes"></a>Comprobación de que un diseño incluye cambios de carga de paquete

Aquí le mostramos cómo determinar si el diseño que se creó anteriormente ha adquirido las cargas de paquetes que se modificaron después de la publicación de la versión:

1. Abra el registro de configuración. El registro se encuentra normalmente en `%TEMP%\dd_setup_[date].log`, donde `[date]` es el momento en que la operación de diseño dio comienzo en formato `yyyyMMddHHmmss`.

2. Busque una línea en el registro estructurada como el texto siguiente:

    `Falling back to signature and signer check because hash verification returned HashMismatch for path: [path]`

3. A continuación, busque líneas más adelante en el registro que indiquen que la descarga se realizó correctamente para [ruta de acceso]. Deberían tener un aspecto similar al siguiente texto:

    `Download of [url] succeeded using engine 'WebClient'`

    `END: Downloading [url] to [path]`

## <a name="see-also"></a>Vea también

* [Creación de una instalación de red de Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Actualizar una instalación basada en red de Visual Studio](update-a-network-installation-of-visual-studio.md)
