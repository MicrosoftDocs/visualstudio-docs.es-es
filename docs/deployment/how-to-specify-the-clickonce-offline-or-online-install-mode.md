---
title: Especificar el modo de instalación en línea o sin conexión (ClickOnce)
description: Obtenga información sobre cómo especificar el modo de instalación de una aplicación ClickOnce, que determina si la aplicación está disponible sin conexión o en línea.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 918cb7e60f4e3fed2beee024d51b94499b14b632
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900427"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Cómo: Especificar el modo de instalación en línea y sin conexión de ClickOnce
El `Install Mode` para una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación determina si la aplicación estará disponible sin conexión o en línea. Cuando elija **la aplicación solo está disponible en línea**, el usuario debe tener acceso a la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Ubicación de publicación (una página web o un recurso compartido de archivos) para poder ejecutar la aplicación. Cuando se elige **la aplicación también está disponible sin conexión**, la aplicación agrega entradas al menú **Inicio** y al cuadro de diálogo **Agregar o quitar programas** . el usuario puede ejecutar la aplicación cuando no está conectada.

`Install Mode`Se puede establecer en la página **publicar** del diseñador de **proyectos**.

> [!NOTE]
> `Install Mode`También se puede establecer mediante el Asistente para publicación. Para obtener más información, consulte [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-make-a-clickonce-application-available-online-only"></a>Para que una aplicación ClickOnce esté disponible solo en línea

1. Seleccione un proyecto en el **Explorador de soluciones** y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. En el área **modo de instalación y configuración** , haga clic en el botón de opción **la aplicación solo está disponible en línea** .

### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Para que una aplicación ClickOnce esté disponible en línea o sin conexión

1. Seleccione un proyecto en el **Explorador de soluciones** y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. En el área **modo de instalación y configuración** , haga clic en el botón de opción **la aplicación también está disponible sin conexión** .

     Cuando se instala, la aplicación agrega entradas al menú **Inicio** y a **Agregar o quitar programas** en el panel de control.

## <a name="see-also"></a>Vea también
- [Publicación de aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Selección de una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)