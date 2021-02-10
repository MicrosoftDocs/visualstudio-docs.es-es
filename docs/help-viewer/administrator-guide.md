---
title: Guía del administrador del Visor de Ayuda
description: Lea la guía del administrador de Visor de Ayuda de Microsoft. Implementar contenido de ayuda local desde Internet o implementar contenido de ayuda local preinstalado en los equipos cliente.
ms.date: 11/01/2017
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e52b03b01f53a8064dc6ec691f751c86266af6a4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944308"
---
# <a name="help-viewer-administrator-guide"></a>Guía del administrador del Visor de Ayuda

El Visor de Ayuda permite administrar instalaciones locales de ayuda para los entornos de red con o sin acceso a Internet. El contenido de la Ayuda local se configura en cada equipo. De forma predeterminada, los usuarios deben tener derechos de administrador para actualizar la instalación de Ayuda local.

Si el entorno de red permite a los clientes tener acceso a Internet, puede usar el ejecutable de **Help Content Manager** para implementar el contenido de la ayuda local desde Internet. Para obtener más información sobre *HlpCtntMgr.exe* sintaxis de la línea de comandos, vea [argumentos de la línea de comandos para Help Content Manager](../help-viewer/command-line-arguments.md).

Para obtener más información sobre la creación de contenido, la creación de un punto de conexión de servicio de intranet y otros tipos similares de actividades, vea [Help Viewer SDK](../extensibility/internals/microsoft-help-viewer-sdk.md) (SDK del Visor de Ayuda).

Si no tiene acceso a Internet en el entorno de red, el Visor de Ayuda puede implementar el contenido de Ayuda local desde la intranet o desde un recurso compartido de red. También puede deshabilitar las opciones de Ayuda del IDE de Visual Studio mediante el uso de [invalidaciones de la clave del Registro](../help-viewer/behavior-overrides.md) para funcionalidades como:

- Ayuda en línea frente a ayuda sin conexión

- Instalación de contenido en el primer inicio del IDE

- Especificación de un servicio de contenido de la intranet

- Administración de contenido

## <a name="deploy-local-help-content-from-the-internet"></a>Implementación de contenido de Ayuda local desde Internet

Puede usar **Help Content Manager** (*HlpCtntMgr.exe*) para implementar el contenido de la Ayuda local desde Internet en los equipos cliente. Use la sintaxis siguiente:

```cmd
\\%ProgramFiles(x86)%\Microsoft Help Viewer\v2.3\HlpCtntmgr.exe /operation \<*name*> /catalogname \<*catalog name*> /locale \<*locale*>
```

Para obtener más información sobre *HlpCtntMgr.exe* sintaxis de la línea de comandos, vea [argumentos de la línea de comandos para Help Content Manager](../help-viewer/command-line-arguments.md).

Requisitos:

- Los equipos cliente deben tener acceso a Internet.

- Los usuarios deben tener derechos de administrador para actualizar, agregar o quitar el contenido de la Ayuda local después de su instalación.

Advertencias:

- El origen predeterminado de la Ayuda seguirá siendo En línea.

### <a name="example"></a>Ejemplo

En el siguiente ejemplo se instala contenido en inglés de Visual Studio en un equipo cliente.

#### <a name="to-install-english-content-from-the-internet"></a>Para instalar contenido en inglés desde Internet

1. Elija **iniciar** y, a continuación, elija **Ejecutar**.

2. Escriba lo siguiente:

     `C:\Program Files (x86)\Microsoft Help Viewer\v2.3\hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us`

3. Presione **ENTRAR**.

## <a name="deploy-pre-installed-local-help-content-on-client-computers"></a>Implementación de contenido de Ayuda local preinstalado en equipos cliente

Puede instalar un conjunto de contenido en línea en un equipo y después copiar ese conjunto de contenido instalado en otros equipos.

Requisitos:

- El equipo en el que se instala el conjunto de contenido debe tener acceso a Internet.

- Los usuarios deben tener derechos de administrador para actualizar, agregar o quitar el contenido de la Ayuda local después de su instalación.

    > [!TIP]
    > Si los usuarios no tienen derechos de administrador, es recomendable deshabilitar la pestaña **Administrar contenido** en el Visor de Ayuda. Para obtener más información, consulte [invalidaciones de Help Content Manager](../help-viewer/behavior-overrides.md).

Advertencias:

- El origen predeterminado de la Ayuda seguirá siendo En línea.

### <a name="create-the-content-set"></a>Creación del conjunto de contenido

Antes de crear el conjunto de contenido base, primero debe desinstalar todo el contenido de Visual Studio local en el equipo de destino.

#### <a name="to-uninstall-local-help"></a>Para desinstalar la Ayuda local

1. En el Visor de Ayuda, seleccione la pestaña **Administrar contenido**.

2. Vaya al conjunto de documentos de Visual Studio.

3. Seleccione **Quitar** junto a cada subelemento.

4. Seleccione **Actualizar** para desinstalar.

5. Vaya a *%ProgramData%\Microsoft\HelpLibrary2\Catalogs\VisualStudio15* y compruebe que la carpeta solo contiene el archivo *catalogType.xml*.

   Una vez que haya quitado todo el contenido local de Ayuda de Visual Studio instalado previamente, está listo para descargar el conjunto de contenido base.

#### <a name="to-download-the-content"></a>Para descargar el contenido

1. En el Visor de Ayuda, seleccione la pestaña **Administrar contenido**.

2. En **Documentación recomendada** o **Documentación disponible**, navegue hasta los conjuntos de documentación que quiera descargar y elija **Agregar**.

3. Seleccione **Actualizar**.

A continuación, debe empaquetar el contenido para poder implementarlo en los equipos cliente.

#### <a name="to-package-the-content"></a>Para empaquetar el contenido

1. Cree una carpeta para copiar el contenido para su posterior implementación. Por ejemplo: *C:\VSHelp*.

2. Abra *cmd.exe* con permisos de administrador.

3. Navegue hasta la carpeta que creó en el paso 1.

4. Escriba lo siguiente:

     `Xcopy %ProgramData%\Microsoft\HelpLibrary2 \<*foldername*>\ /y /e /k /o`

     Por ejemplo: `Xcopy %ProgramData%\Microsoft\HelpLibrary2 c:\VSHelp\ /y /e /k /o`

### <a name="deploy-the-content"></a>Implementación del contenido

1. Cree un recurso compartido de red y copie el contenido de Ayuda en esa ubicación.

     Por ejemplo, copie el contenido de *C:\VSHelp* en *\\ \myserver\VSHelp*.

2. Cree un archivo *.bat* que contendrá el script de implementación para el contenido de Ayuda. Puesto que el cliente podría tener un bloqueo de lectura en cualquiera de los archivos que se estén eliminando como parte de la inserción, debe cerrar el cliente antes de insertar las actualizaciones. Por ejemplo:

    ```cmd
    REM - copy pre-ripped content to ProgramData
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to ProgramData (%ERRORLEVEL%)
    ```

3. Ejecute el archivo *. bat* en los equipos locales en los que desea instalar el contenido de la ayuda.

## <a name="see-also"></a>Vea también

- [Argumentos de la línea de comandos para Help Content Manager](../help-viewer/command-line-arguments.md)
- [Invalidaciones de Help Content Manager](../help-viewer/behavior-overrides.md)
- [Visor de Ayuda de Microsoft](../help-viewer/overview.md)
- [SDK del Visor de Ayuda](../extensibility/internals/microsoft-help-viewer-sdk.md)