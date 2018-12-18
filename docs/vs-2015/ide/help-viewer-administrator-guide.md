---
title: Guía del administrador del Visor de Ayuda | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f470c55b08cc559e481ed75e962fda4f0e625a5c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871295"
---
# <a name="help-viewer-administrator-guide"></a>Guía del administrador del Visor de Ayuda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El Visor de Ayuda permite administrar instalaciones locales de ayuda para los entornos de red con o sin acceso a Internet. El contenido de la Ayuda local se configura en cada equipo. De forma predeterminada, los usuarios deben tener derechos de administrador para actualizar la instalación de Ayuda local.  
  
 Si el entorno de red permite a los clientes obtener acceso a Internet, el Visor de Ayuda permite utilizar scripts de la línea de comandos para implementar el contenido de Ayuda local desde Internet.  
  
 Si el entorno de red no permite a los clientes obtener acceso a Internet, el Visor de Ayuda puede implementar el contenido de Ayuda local desde la intranet o desde un recurso compartido de red. También se pueden deshabilitar las opciones de Ayuda del IDE de Visual Studio, tales como ayuda en línea o sin conexión, instalación de contenido en el primer inicio del IDE, especificar un servicio de contenido de la intranet y administrar el contenido, mediante invalidaciones de la clave del Registro.  
  
 La sintaxis básica es la siguiente:  
  
 \<*ruta de acceso a*>/Operation \HlpCtntmgr.exe \< *argumento*> /catalogname \< *nombre*> /locale \< *deconfiguraciónregional*>/SourceUri \< *.msha ruta o dirección URL*>  
  
 Para obtener más información sobre la sintaxis de la línea de comandos de HlpCtntMgr.exe, vea [Argumentos de línea de comandos para Help Content Manager](../ide/command-line-arguments-for-the-help-content-manager.md).  
  
 Para obtener más información sobre la creación de contenido, la creación de un punto de conexión de servicio de intranet y otros tipos similares de actividades, consulte el SDK del Visor de Ayuda.  
  
## <a name="deploying-local-help-content-from-the-internet"></a>Implementación de contenido de Ayuda local desde Internet  
 Puede utilizar el servicio de paquete de contenido de MSDN para distribuir el contenido de la Ayuda local desde Internet a los equipos cliente. Utilice la sintaxis siguiente:  
  
 \\<*ruta de acceso a*>/Operation \v2.2\HlpCtntmgr.exe \< *nombre*> /catalogname \< *CatalogName*> /locale \<  *configuración regional*>  
  
 Para obtener más información sobre la sintaxis de la línea de comandos de HlpCtntMgr.exe, vea [Argumentos de línea de comandos para Help Content Manager](../ide/command-line-arguments-for-the-help-content-manager.md).  
  
 Requisitos:  
  
- Los equipos cliente deben tener acceso a Internet.  
  
- Los usuarios deben tener derechos de administrador para actualizar, agregar o quitar el contenido de la Ayuda local después de su instalación.  
  
  Advertencias:  
  
- El origen predeterminado de la Ayuda seguirá siendo En línea.  
  
  > [!TIP]
  >  Puede cambiar el origen predeterminado de la Ayuda si modifica la clave del Registro HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\14.0\help\UseOnlineHelp. Para obtener más información, vea [Invalidaciones de Help Content Manager](../ide/help-content-manager-overrides.md).  
  
- A los clientes se les pedirá que instalen el contenido de la Ayuda básica la primera vez que se inicia Visual Studio. Puede deshabilitar este símbolo del sistema si modifica la clave del Registro HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\14.0\Help\DisableFirstRunHelpSelection.  
  
### <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se instala contenido en inglés de Visual Studio en un equipo cliente.  
  
##### <a name="to-install-english-content-from-the-internet"></a>Para instalar contenido en inglés desde Internet  
  
1.  Seleccione **Inicio** y **Ejecutar**.  
  
2.  Escriba lo siguiente:  
  
     C:\Archivos de programa (x86)\Microsoft Help Viewer\v2.2\hlpctntmgr.exe /operation install /catalogname VisualStudio14 /locale es-es  
  
3.  Presione ENTRAR.  
  
## <a name="deploying-pre-installed-local-help-content-on-client-computers"></a>Implementación de contenido de Ayuda local preinstalado en los equipos cliente  
 Puede instalar un conjunto de contenido en línea en un equipo y después copiar ese conjunto de contenido instalado en otros equipos.  
  
 Requisitos:  
  
- El equipo en el que se instala el conjunto de contenido debe tener acceso a Internet.  
  
- Los usuarios deben tener derechos de administrador para actualizar, agregar o quitar el contenido de la Ayuda local después de su instalación.  
  
  > [!TIP]
  >  Si los usuarios no tienen derechos de administrador, es recomendable deshabilitar la pestaña Administrar contenido en el Visor de Ayuda. Para obtener más información, vea [Invalidaciones de Help Content Manager](../ide/help-content-manager-overrides.md).  
  
  Advertencias:  
  
- Si los usuarios no tienen derechos de administrador, es recomendable deshabilitar la pestaña Administrar contenido en el Visor de Ayuda. Para obtener más información, vea [Invalidaciones de Help Content Manager](../ide/help-content-manager-overrides.md).  
  
- El origen predeterminado de la Ayuda seguirá siendo En línea.  
  
- A los clientes se les pedirá que instalen el contenido de la Ayuda básica la primera vez que se inicia Visual Studio. Para obtener más información, vea [Invalidaciones de Help Content Manager](../ide/help-content-manager-overrides.md).  
  
### <a name="create-the-content-set"></a>Creación del conjunto de contenido  
 Antes de crear el conjunto de contenido base, primero debe desinstalar todo el contenido de Visual Studio local en el equipo de destino.  
  
##### <a name="to-uninstall-local-help"></a>Para desinstalar la Ayuda local  
  
1. En el Visor de Ayuda, seleccione la pestaña **Administrar contenido**.  
  
2. En **documentación disponible**, navegue hasta el conjunto de documentos de Visual Studio.  
  
3. Seleccione **Quitar** junto a cada subelemento.  
  
4. Elija **iniciar** para desinstalar  
  
5. Vaya a *n*: \ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12 y compruebe que la carpeta solo contiene el archivo catalogType.xml.  
  
   Una vez que haya quitado todo el contenido local de Ayuda de Visual Studio instalado previamente, está listo para descargar el conjunto de contenido base.  
  
##### <a name="to-download-the-content"></a>Para descargar el contenido  
  
1. En el Visor de Ayuda, seleccione la pestaña **Administrar contenido**.  
  
2. En **documentación disponible**, vaya a los conjuntos de documentación que desee descargar y, a continuación, elija **agregar**.  
  
3. Elija **Iniciar**.  
  
   A continuación, debe empaquetar el contenido para poder implementarlo en los equipos cliente.  
  
##### <a name="to-package-the-content"></a>Para empaquetar el contenido  
  
1.  Cree una carpeta para copiar el contenido para su posterior implementación.  
  
     Por ejemplo: c:\VS12Help.  
  
2.  Abra cmd.exe con permisos de administrador.  
  
3.  Navegue hasta la carpeta que creó en el paso 1.  
  
4.  Escriba lo siguiente:  
  
     Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 \< *nombreDeCarpeta*> \ /y /e /k /o  
  
     Por ejemplo: `Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 c:\VS12Help\ /y /e /k /o`.  
  
### <a name="deploying-the-content"></a>Implementación del contenido  
  
##### <a name="to-deploy-the-content"></a>Para implementar el contenido  
  
1.  Cree un recurso compartido de red y copie el contenido de Ayuda a esa ubicación.  
  
     Por ejemplo, copiar el contenido de c:\VS12Help en \\\myserver\VS12Help.  
  
2.  Cree un archivo .bat que contendrá el script de implementación para el contenido de Ayuda. Puesto que el cliente podría tener un bloqueo de lectura en cualquiera de los archivos que se estén eliminando como parte de la inserción, debe cerrar el cliente antes de insertar las actualizaciones.  
  
     Por ejemplo:  
  
    ```  
    REM - copy pre-ripped content to ProgramData  
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o  
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to Programdata (%ERRORLEVEL%)  
  
    REM - get processor type and create/run registry update file  
    IF "%PROCESSOR_ARCHITECTURE%"=="AMD64" GOTO AMD64  
  
    @echo Architecture type is x86  
  
    ECHO Windows Registry Editor Version 5.00 > x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs] >> x86.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12] >> x86.reg  
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg  
    ECHO "FirstTimeRun"="False"  >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12\en-US]  >> x86.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg  
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help]  >> x86.reg  
    ECHO "UseOnlineHelp"=dword:00000000  >> x86.reg  
  
    regedit.exe /s x86.reg  
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x86 reg (%ERRORLEVEL%)  
  
    GOTO CONTINUE  
  
    :AMD64  
    @echo Architecture type is AMD64  
  
    ECHO Windows Registry Editor Version 5.00 > x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs] >> x64.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14] >> x64.reg  
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio14\\"  >> x64.reg  
    ECHO "FirstTimeRun"="False"  >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14\en-US]  >> x64.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\en-US\\"  >> x64.reg  
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\VSWinExpress\14.0\help]  >> x64.reg  
    ECHO "UseOnlineHelp"=dword:00000000  >> x64.reg  
  
    regedit.exe /s x64.reg  
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x64 reg (%ERRORLEVEL%)  
  
    :CONTINUE  
    ```  
  
3.  Ejecute el archivo bat en los equipos locales en los que desee instalar el contenido de Ayuda.  
  
## <a name="see-also"></a>Vea también  
 [Argumentos de línea de comandos para Help Content Manager](../ide/command-line-arguments-for-the-help-content-manager.md)   
 [Invalidaciones de Help Content Manager](../ide/help-content-manager-overrides.md)



