---
title: Publicación de una aplicación ClickOnce mediante el Asistente para publicación | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- deploying applications [ClickOnce], Publish wizard
- Windows applications, ClickOnce deployments
- publishing, ClickOnce
ms.assetid: 2e4aa67c-4445-4f7b-9e03-9acb95829127
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1a6b916e8050bd68f4ccd601e92725768a01c4c7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935052"
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Procedimiento Publicación de una aplicación ClickOnce mediante el Asistente para publicación
Para que una aplicación ClickOnce esté disponible para los usuarios, debe publicarla en un recurso compartido de archivos o ruta de acceso, en un servidor FTP o en un medio extraíble. Puede publicar la aplicación con el Asistente para publicación. En la página **Publicar** del **Diseñador de proyectos** hay disponibles más propiedades relativas a la publicación. Para obtener más información, vea [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md).

Antes de ejecutar el Asistente para publicación, debe establecer las propiedades de publicación correctamente. Por ejemplo, si quiere designar una clave para firmar la aplicación ClickOnce, puede hacerlo en la página **Firma** del **Diseñador de proyectos**. Para obtener más información, consulte [aplicaciones ClickOnce Secure](../deployment/securing-clickonce-applications.md).

> [!NOTE]
> Cuando se instala más de una versión de una aplicación con ClickOnce, la instalación mueve las versiones anteriores de la aplicación a una carpeta llamada *Archivo*, en la ubicación de publicación que especifiques. Al archivar las versiones anteriores de esta manera, el directorio de instalación se mantiene limpio de carpetas de versiones anteriores.

> [!NOTE]
> Los cuadros de diálogo y los comandos de menú que se ven pueden diferir de los descritos en la Ayuda, dependiendo de los valores de configuración o de edición activos. Para cambiar la configuración, haga clic en **Importar y exportar configuraciones** en el menú **Herramientas** . Para obtener más información, vea [Restablecer la configuración](../ide/environment-settings.md#reset-settings).

## <a name="to-publish-to-a-file-share-or-path"></a>Para publicar en un recurso compartido de archivos o en una ruta de acceso

1. En el **Explorador de soluciones**, seleccione el proyecto de aplicación.

2. En el **compilar** menú, haga clic en **publicar** *Projectname*.

    Aparece el Asistente para publicación.

3. En la página **¿Dónde desea publicar la aplicación?**, escriba una dirección válida de servidor FTP o una ruta de acceso de archivo válida con uno de los formatos mostrados y después haga clic en **Siguiente**.

4. En la página **Instalación de la aplicación**, seleccione la ubicación donde los usuarios irán para instalar la aplicación:

   -   Si los usuarios la instalarán desde un sitio web, haga clic en **Desde un sitio web** y escriba la dirección URL correspondiente a la ruta de acceso al archivo especificada en el paso anterior. Haga clic en **Siguiente**. (Esta opción se usa normalmente cuando se especifica una dirección FTP como ubicación de publicación. No se permite la descarga directa desde FTP. Por lo tanto, tiene que especificar una dirección URL aquí).

   -   Si los usuarios instalarán la aplicación directamente desde el recurso compartido de archivos, haga clic en **Desde una ruta de acceso UNC o un recurso compartido de archivos** y después en **Siguiente**. (Esto es para ubicaciones de publicación con el formato *c:\deploy\myapp* o *\\\server\myapp*.)

   -   Si los usuarios instalarán desde medios extraíbles, haga clic en **Desde un CD-ROM o un DVD-ROM** y después haga clic en **Siguiente**.

5. En la página **¿La aplicación estará disponible sin conexión?**, haga clic en la opción apropiada:

   - Si quiere que la aplicación se ejecute cuando el usuario esté desconectado de la red, haga clic en **Sí, esta aplicación está disponible con o sin conexión**. Se creará un acceso directo a la aplicación en el menú **Inicio**.

   - Si quiere que la aplicación se ejecute directamente desde la ubicación de publicación, haga clic en **No, esta aplicación sólo está disponible en línea**. No se creará ningún acceso directo en el menú **Inicio**.

     Haga clic en **Siguiente** para continuar.

6. Haga clic en **Finalizar** para publicar la aplicación.

    El estado de publicación se muestra en el área de notificación del estado.

## <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>Para publicar en un CD-ROM o DVD-ROM

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto de aplicación y después haga clic en **Propiedades**.

    Aparece el **Diseñador de proyectos**.

2. Haga clic en la pestaña **Publicar** para abrir la página **Publicar** en el **Diseñador de proyectos** y haga clic en el botón **Asistente para publicación**.

    Aparece el Asistente para publicación.

3. En la página **¿Dónde desea publicar la aplicación?**, especifique la ruta de acceso del archivo o la ubicación FTP donde se publicará la aplicación, por ejemplo, *d:\deploy*. Después, haga clic en **Siguiente** para continuar.

4. En la página **Instalación de la aplicación**, Haga clic en **Desde un CD-ROM o un DVD-ROM** y después haga clic en **Siguiente**.

   > [!NOTE]
   >  Si quiere que la instalación se ejecute automáticamente cuando se inserte el CD-ROM en la unidad, abra la página **Publicar** en el **Diseñador de proyectos** y haga clic en el botón **Opciones**; después, en el asistente **Opciones de publicación**, seleccione **En las instalaciones desde CD, el programa de instalación se inicia automáticamente al insertar el CD**.

5. Si distribuye su aplicación en CD-ROM, quizás quiera proporcionar actualizaciones desde un sitio web. En la página **¿Dónde buscará la aplicación las actualizaciones?**, elija una opción de actualización:

   - Si la aplicación buscará actualizaciones, haga clic en **La aplicación buscará actualizaciones en la siguiente ubicación** y escriba el nombre de la ubicación donde se publicarán las actualizaciones. Puede ser una ubicación de archivos, un sitio web o un servidor FTP.

   - Si la aplicación no buscará actualizaciones, haga clic en **La aplicación no buscará actualizaciones**.

     Haga clic en **Siguiente** para continuar.

6. Haga clic en **Finalizar** para publicar la aplicación.

    El estado de publicación se muestra en el área de notificación del estado.

   > [!NOTE]
   >  Una vez completa la publicación, tendrá que usar un grabador de CD o de DVD para copiar los archivos desde la ubicación especificada en el paso 3 al CD-ROM o DVD-ROM.

## <a name="see-also"></a>Vea también

- [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Proteger aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)
- [Implementación de una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)