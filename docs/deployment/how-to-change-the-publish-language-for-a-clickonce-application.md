---
title: Cambiar el idioma de publicación para la aplicación ClickOnce
description: Obtenga información sobre cómo especificar un idioma o una referencia cultural para una aplicación de configuración regional en ClickOnce, en lugar de establecer el idioma o la referencia cultural del equipo de desarrollo de forma predeterminada.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7fed8c137b5bce225d8a231bb5a263b87c2bf361
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350171"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Cómo: Cambiar el idioma de publicación de una aplicación ClickOnce

Al publicar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación, la interfaz de usuario mostrada durante la instalación tiene como valor predeterminado el idioma y la referencia cultural del equipo de desarrollo. Si está publicando una aplicación localizada, deberá especificar un idioma y una referencia cultural para que coincida con la versión localizada. Esto viene determinado por la `Publish language` propiedad del proyecto.

La `Publish language` propiedad se puede establecer en el cuadro de diálogo **Opciones de publicación** , accesible desde la página **publicar** del **Diseñador de proyectos**.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, vea [Restablecer la configuración](../ide/environment-settings.md#reset-settings).

## <a name="to-change-the-publish-language"></a>Para cambiar el idioma de publicación

1. Seleccione un proyecto en el **Explorador de soluciones** y, en el menú **Proyecto** , haga clic en **Propiedades**.

2. Haga clic en la pestaña **Publicar**.

3. Haga clic en el botón **Opciones** para abrir el cuadro de diálogo **Opciones de publicación** .

4. Haga clic en **Descripción**.

5. En el cuadro de diálogo **Opciones de publicación** , seleccione un idioma y una referencia cultural en la lista desplegable **idioma de publicación** y, a continuación, haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también

- [Publicación de aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)