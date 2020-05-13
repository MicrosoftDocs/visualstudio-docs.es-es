---
title: Cambios importantes en la extensibilidad de Visual Studio 2017
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b3a04c925ef897171de51c73c90973a12c3b17d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739971"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Cambios en la extensibilidad de Visual Studio 2017

Visual Studio 2017 proporciona una experiencia de instalación de [Visual Studio más rápida y ligera](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) que reduce el impacto de Visual Studio en los sistemas de usuario al tiempo que ofrece a los usuarios una mayor variedad de opciones sobre las cargas de trabajo y las características que se instalan. Para admitir estas mejoras, hemos realizado cambios en el modelo de extensibilidad, incluidos algunos cambios importantes. Este artículo describe los detalles técnicos de estos cambios y lo que se puede hacer para abordarlos.

> [!NOTE]
> Parte de la información son detalles de implementación a un momento dado y se pueden cambiar más adelante.

## <a name="changes-affecting-vsix-format-and-installation"></a>Cambios que afectan al formato y la instalación de VSIX

Visual Studio 2017 introdujo el formato VSIX v3 (versión 3) para admitir la experiencia de instalación ligera.

Los cambios en el formato VSIX incluyen:

* Declaración de los requisitos previos de configuración. Para cumplir con la promesa de un Visual Studio ligero y de instalación rápida, el instalador ahora ofrece más opciones de configuración a los usuarios. Como resultado, para asegurarse de que las características y componentes requeridos por una extensión están instalados, las extensiones deben declarar sus dependencias.

  * El instalador de Visual Studio 2017 ofrece automáticamente adquirir e instalar los componentes necesarios para el usuario como parte de la instalación de la extensión.
  * También se advierte a los usuarios al intentar instalar una extensión que no se creó con el nuevo formato VSIX v3, incluso si se han marcado en su manifiesto como la versión de destino 15.0.

* Capacidades mejoradas para el formato VSIX. Para ofrecer una instalación de [bajo impacto](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) de Visual Studio que también admite instalaciones en paralelo, ya no guardamos la mayoría de los datos de configuración en el registro del sistema y hemos movido ensamblados específicos de Visual Studio fuera de la GAC. También aumentamos las capacidades del formato VSIX y el motor de instalación VSIX, lo que le permite utilizarlo en lugar de un MSI o EXE para instalar sus extensiones para algunos tipos de instalación.

Las nuevas capacidades incluyen:

* Registro en la instancia de Visual Studio especificada.
* Instalación fuera de la [carpeta de extensiones](set-install-root.md).
* Detección de arquitectura de procesador.
* Dependencia de paquetes de idioma separados por el idioma.
* Instalación con [soporte NGEN](ngen-support.md).

## <a name="build-an-extension-for-visual-studio-2017"></a>Crear una extensión para Visual Studio 2017

Las herramientas de diseñador para la creación del nuevo formato de manifiesto de VSIX v3 están disponibles en Visual Studio 2017. Consulte el documento adjunto Cómo: migrar proyectos de [extensibilidad a Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) para obtener más información sobre el uso de las herramientas del diseñador o la realización de actualizaciones manuales del proyecto y el manifiesto para desarrollar extensiones VSIX v3.

## <a name="change-visual-studio-user-data-path"></a>Cambiar: ruta de acceso de datos de usuario de Visual Studio

Anteriormente, solo podía existir una instalación de cada versión principal de Visual Studio en cada equipo. Para admitir instalaciones en paralelo de Visual Studio 2017, pueden existir varias rutas de acceso de datos de usuario para Visual Studio en el equipo del usuario.

El código que se ejecuta dentro del proceso de Visual Studio debe actualizarse para usar el Administrador de configuración de Visual Studio. El código que se ejecuta fuera del proceso de Visual Studio puede encontrar la ruta de acceso del usuario de una instalación específica de Visual Studio [siguiendo las instrucciones aquí.](locating-visual-studio.md)

## <a name="change-global-assembly-cache-gac"></a>Cambiar: Caché global de ensamblados (GAC)

La mayoría de los ensamblados principales de Visual Studio ya no están instalados en la GAC. Se realizaron los siguientes cambios para que el código que se ejecuta en el proceso de Visual Studio pueda seguir encontrando los ensamblados necesarios en tiempo de ejecución.

> [!NOTE]
> [INSTALLDIR] a continuación hace referencia al directorio raíz de instalación de Visual Studio. *VSIXInstaller.exe* rellenará automáticamente esto, pero para escribir código de implementación personalizado, lea [localizar Visual Studio](locating-visual-studio.md).

* Ensamblados que solo se instalaron en la GAC:

  Estos ensamblados ahora se instalan en <em>[INSTALLDIR], Common7,\*IDE , *[INSTALLDIR], Common7, IDE, PublicAssemblies,</em> o *[INSTALLDIR], Common7, IDE, PrivateAssemblies*. Estas carpetas forman parte de las rutas de acceso de sondeo del proceso de Visual Studio.

* Ensamblados que se instalaron en una ruta de acceso sin sondeo y en la GAC:

  * La copia de la GAC se eliminó de la configuración.
  * Se ha agregado un archivo *.pkgdef* para especificar una entrada base de código para el ensamblado.

    Por ejemplo:

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    En tiempo de ejecución, el subsistema pkgdef de Visual Studio combina estas entradas en el archivo de configuración en tiempo [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) de ejecución del proceso de Visual Studio (en *[VSAPPDATA]-devenv.exe.config*) como elementos. Esta es la forma recomendada de permitir que el proceso de Visual Studio encuentre el ensamblado, ya que evita buscar en las rutas de acceso de sondeo.

### <a name="reacting-to-this-breaking-change"></a>Reaccionando a este cambio de ruptura

* Si la extensión se ejecuta en el proceso de Visual Studio:

  * El código podrá encontrar los ensamblados principales de Visual Studio.
  * Considere la posibilidad de usar un archivo *.pkgdef* para especificar una ruta de acceso a los ensamblados si es necesario.

* Si la extensión se ejecuta fuera del proceso de Visual Studio:

  Considere la posibilidad de buscar los ensamblados principales de Visual Studio en <em>[INSTALLDIR], Common7,\*IDE , *[INSTALLDIR], Common7, IDE, PublicAssemblies,</em> o *[INSTALLDIR], Common7, IDE, PrivateAssemblies* mediante el archivo de configuración o el solucionador de ensamblados.

## <a name="change-reduce-registry-impact"></a>Cambio: Reducir el impacto en el registro

### <a name="global-com-registration"></a>Registro COM global

* Anteriormente, Visual Studio instalaba muchas claves del Registro en los subárboles HKEY_CLASSES_ROOT y HKEY_LOCAL_MACHINE para admitir el registro COM nativo. Para eliminar este impacto, Visual Studio ahora usa [activación sin registro para componentes COM](https://msdn.microsoft.com/library/ms973913.aspx).
* Como resultado, la mayoría de los archivos TLB / OLB / DLL en %ProgramFiles(x86)%-Archivos comunes-Microsoft Shared-MSEnv ya no se instalan de forma predeterminada por Visual Studio. Estos archivos ahora se instalan en [INSTALLDIR] con los manifiestos COM sin registro correspondientes utilizados por el proceso de host de Visual Studio.
* Como resultado, el código externo que se basa en el registro COM global para las interfaces COM de Visual Studio ya no encontrará estos registros. El código que se ejecuta dentro del proceso de Visual Studio no verá una diferencia.

### <a name="visual-studio-registry"></a>Registro de Visual Studio

* Anteriormente, Visual Studio instalaba muchas claves del Registro en los **subárboles HKEY_LOCAL_MACHINE** y **HKEY_CURRENT_USER** del sistema en una clave específica de Visual Studio:

  * **HKLM-Software-Microsoft-VisualStudio\{Version:** claves del Registro creadas por los instaladores MSI y extensiones por equipo.
  * **HKCU-Software-Microsoft-VisualStudio\{Version:** claves del Registro creadas por Visual Studio para almacenar la configuración específica del usuario.
  * **HKCU-Software-Microsoft-VisualStudio\{Version-_Config**: Una copia de la clave HKLM de Visual Studio anterior, además de las claves del Registro combinadas de archivos *.pkgdef* por extensiones.

* Para reducir el impacto en el registro, Visual Studio ahora usa la función [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) para almacenar las claves del Registro en un archivo binario privado en *[VSAPPDATA]-privateregistry.bin*. Solo un número muy pequeño de claves específicas de Visual Studio permanecen en el registro del sistema.
* El código existente que se ejecuta dentro del proceso de Visual Studio no se ve afectado. Visual Studio redirigirá todas las operaciones del Registro bajo la clave específica de HKCU Visual Studio al registro privado. La lectura y escritura en otras ubicaciones del registro seguirá utilizando el registro del sistema.
* El código externo tendrá que cargar y leer desde este archivo para las entradas del Registro de Visual Studio.

### <a name="react-to-this-breaking-change"></a>Reaccionar a este cambio de ruptura

* El código externo también se debe convertir para usar la activación sin registro para los componentes COM.
* Los componentes externos pueden encontrar la ubicación de Visual Studio [siguiendo las instrucciones aquí](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup).
* Se recomienda que los componentes externos usen el Administrador de [configuración externa](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) en lugar de leer y escribir directamente en las claves del Registro de Visual Studio.
* Compruebe si los componentes que utiliza la extensión pueden haber implementado otra técnica para el registro. Por ejemplo, las extensiones del depurador pueden aprovechar el nuevo registro COM de [archivo JSON msvsmon.](migrate-debugger-COM-registration.md)
