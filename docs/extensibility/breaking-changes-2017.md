---
title: Cambios importantes en la extensibilidad de Visual Studio 2017
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a1a12470530589c8d19a088428bc265c530b55f0
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252316"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Cambios en la extensibilidad de Visual Studio 2017

Visual Studio 2017 proporciona una [experiencia de instalación de Visual Studio más rápida y más ligera](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) que reduce el impacto de Visual Studio en los sistemas de usuario, a la vez que proporciona a los usuarios más opciones sobre las cargas de trabajo y características que están instaladas. Para admitir estas mejoras, hemos realizado cambios en el modelo de extensibilidad, incluidos algunos cambios importantes. En este artículo se describen los detalles técnicos de estos cambios y lo que se puede hacer para solucionarlos.

> [!NOTE]
> Algunos datos son detalles de la implementación a un momento dado y se pueden cambiar más adelante.

## <a name="changes-affecting-vsix-format-and-installation"></a>Cambios que afectan al formato VSIX y a la instalación

Visual Studio 2017 presentó el formato VSIX V3 (versión 3) para admitir la experiencia de instalación ligera.

Los cambios en el formato VSIX incluyen:

* Declaración de los requisitos previos de instalación. Para ofrecer una promesa de una instalación rápida y sencilla de Visual Studio, el instalador ofrece ahora más opciones de configuración a los usuarios. Como resultado, para asegurarse de que se instalan las características y los componentes necesarios para una extensión, las extensiones deben declarar sus dependencias.

  * El instalador de Visual Studio 2017 ofrece automáticamente la adquisición e instalación de los componentes necesarios para el usuario como parte de la instalación de la extensión.
  * También se advierte a los usuarios cuando intentan instalar una extensión que no se compiló con el nuevo formato VSIX V3, aunque se hayan marcado en su manifiesto como destino de la versión 15,0.

* Capacidades mejoradas para el formato VSIX. Para ofrecer una [instalación de bajo impacto](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) de Visual Studio que también admite instalaciones en paralelo, ya no se guardan la mayoría de los datos de configuración en el registro del sistema y se han pasado los ensamblados específicos de Visual Studio de la GAC. También hemos aumentado las capacidades del formato VSIX y del motor de instalación de VSIX, permitiéndole usarlo en lugar de MSI o EXE para instalar las extensiones para algunos tipos de instalación.

Las nuevas capacidades incluyen:

* Registro en la instancia especificada de Visual Studio.
* Instalación fuera de la [carpeta de extensiones](set-install-root.md).
* Detección de la arquitectura del procesador.
* Dependencia de paquetes de idioma independientes del lenguaje.
* Instalación con [compatibilidad con Ngen](ngen-support.md).

## <a name="build-an-extension-for-visual-studio-2017"></a>Compilar una extensión para Visual Studio 2017

Las herramientas del diseñador para la creación del nuevo formato de manifiesto VSIX V3 están disponibles en Visual Studio 2017. Vea el documento [adjunto cómo: Migre los proyectos de extensibilidad a Visual Studio](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) 2017 para más información sobre el uso de las herramientas de diseñador o la realización de actualizaciones manuales en el proyecto y el manifiesto para desarrollar extensiones VSIX V3.

## <a name="change-visual-studio-user-data-path"></a>Cambios Ruta de datos de usuario de Visual Studio

Anteriormente, solo podía existir una instalación de cada versión principal de Visual Studio en cada máquina. Para admitir instalaciones en paralelo de Visual Studio 2017, pueden existir varias rutas de acceso de datos de usuario para Visual Studio en el equipo del usuario.

El código que se ejecuta dentro del proceso de Visual Studio debe actualizarse para usar el administrador de configuración de Visual Studio. El código que se ejecuta fuera del proceso de Visual Studio puede encontrar la ruta de acceso de usuario de una instalación específica de Visual Studio siguiendo estas [instrucciones](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Cambios Caché de ensamblados global (GAC)

La mayoría de los ensamblados principales de Visual Studio ya no se instalan en la GAC. Los siguientes cambios se realizaron para que el código que se ejecuta en el proceso de Visual Studio todavía pueda encontrar los ensamblados necesarios en tiempo de ejecución.

> [!NOTE]
> [INSTALLDIR] a continuación se hace referencia al directorio raíz de instalación de Visual Studio. *VSIXInstaller. exe* rellenará automáticamente esto, pero para escribir código de implementación personalizado, lea [Buscar Visual Studio](locating-visual-studio.md).

* Ensamblados que solo se instalaron en la GAC:

  Estos ensamblados se instalan ahora en <em>[INSTALLDIR\*] \Common7\IDE, * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> o *[INSTALLDIR] \Common7\IDE\PrivateAssemblies*. Estas carpetas forman parte de las rutas de acceso de sondeo del proceso de Visual Studio.

* Ensamblados que se instalaron en una ruta de acceso de no sondeo y en la GAC:

  * La copia de la GAC se quitó del programa de instalación.
  * Se ha agregado un archivo *. pkgdef* para especificar una entrada base de código para el ensamblado.

    Por ejemplo:

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    En tiempo de ejecución, el subsistema de Visual Studio pkgdef combina estas entradas en el archivo de configuración en tiempo de ejecución del proceso de Visual Studio (en [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) *[VSAPPDATA] \devenv.exe.config*) como elementos. Esta es la manera recomendada de permitir que el proceso de Visual Studio busque el ensamblado, ya que evita la búsqueda a través de rutas de acceso de sondeo.

### <a name="reacting-to-this-breaking-change"></a>Reacción a este cambio importante

* Si la extensión se ejecuta en el proceso de Visual Studio:

  * El código podrá encontrar ensamblados principales de Visual Studio.
  * Considere la posibilidad de usar un archivo *. pkgdef* para especificar una ruta de acceso a los ensamblados si es necesario.

* Si la extensión se ejecuta fuera del proceso de Visual Studio:

  Considere la posibilidad de buscar ensamblados principales de Visual Studio en <em>[\*INSTALLDIR] \Common7\IDE, * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> o *[INSTALLDIR] \Common7\IDE\PrivateAssemblies* mediante el archivo de configuración o el ensamblado resolución.

## <a name="change-reduce-registry-impact"></a>Cambios Reducir el impacto del registro

### <a name="global-com-registration"></a>Registro COM global

* Anteriormente, Visual Studio instalaba muchas claves del registro en los subárboles HKEY_CLASSES_ROOT y HKEY_LOCAL_MACHINE para admitir el registro COM nativo. Para eliminar este impacto, Visual Studio ahora usa [la activación sin registro para los componentes com](https://msdn.microsoft.com/library/ms973913.aspx).
* Como resultado, Visual Studio ya no instala de forma predeterminada la mayoría de los archivos TLB/OLB/DLL de% ProgramFiles (x86)% \ Common Files\Microsoft Shared\MSEnv. Estos archivos se instalan ahora en [INSTALLDIR] con los manifiestos COM sin registro correspondientes que usa el proceso de host de Visual Studio.
* Como resultado, el código externo que se basa en el registro COM global para las interfaces COM de Visual Studio ya no encontrará estos registros. El código que se ejecuta dentro del proceso de Visual Studio no verá ninguna diferencia.

### <a name="visual-studio-registry"></a>Registro de Visual Studio

* Anteriormente, Visual Studio instalaba muchas claves del registro en los subárboles **HKEY_LOCAL_MACHINE** y **HKEY_CURRENT_USER** del sistema con una clave específica de Visual Studio:

  * **HKLM\Software\Microsoft\VisualStudio\{Version}** : Claves del registro creadas por instaladores MSI y extensiones por máquina.
  * **HKCU\Software\Microsoft\VisualStudio\{Version}** : Claves del registro creadas por Visual Studio para almacenar la configuración específica del usuario.
  * **HKCU\Software\Microsoft\VisualStudio\{Version}_Config**: Una copia de la clave HKLM de Visual Studio anterior, además de las claves del registro combinadas de los archivos *. pkgdef* por extensiones.

* Para reducir el impacto en el registro, Visual Studio ahora usa la función [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) para almacenar las claves del registro en un archivo binario privado en *[VSAPPDATA] \privateregistry.bin*. Solo un número muy pequeño de claves específicas de Visual Studio permanece en el registro del sistema.
* El código existente que se ejecuta dentro del proceso de Visual Studio no se ve afectado. Visual Studio redirigirá todas las operaciones del registro en la clave específica de Visual Studio HKCU al registro privado. La lectura y la escritura en otras ubicaciones del registro seguirán usando el registro del sistema.
* El código externo tendrá que cargar y leer en este archivo para las entradas del registro de Visual Studio.

### <a name="react-to-this-breaking-change"></a>Reaccionar ante este cambio importante

* El código externo se debe convertir para utilizar también la activación sin registro para los componentes COM.
* Los componentes externos pueden encontrar la ubicación de Visual Studio siguiendo [las instrucciones aquí](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup).
* Se recomienda que los componentes externos usen el [Administrador de configuración externa](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) en lugar de leer y escribir directamente en las claves del registro de Visual Studio.
* Compruebe si los componentes que usa la extensión pueden haber implementado otra técnica para el registro. Por ejemplo, las extensiones del depurador pueden aprovechar el nuevo [registro com de archivo JSON de msvsmon](migrate-debugger-COM-registration.md).
