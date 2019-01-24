---
title: Cambios importantes en la extensibilidad de Visual Studio 2017 | Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5305a5fd5dea53554e4ac9c0015e8181d5906788
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841955"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Cambios en la extensibilidad de Visual Studio 2017

Con Visual Studio 2017, le ofrecemos un [experiencia de instalación de Visual Studio más rápido y ligero](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer) que reduce el impacto de Visual Studio en sistemas de usuario, mientras proporciona a los usuarios más opciones a través de las características y las cargas de trabajo que se instalan. Para admitir estas mejoras, se ha realizado cambios en el modelo de extensibilidad y han realizado algunos cambios importantes a la extensibilidad de Visual Studio. Este documento describirá los detalles técnicos de estos cambios, y qué se puede hacer para solucionarlos. Tenga en cuenta que cierta información es los detalles de implementación en un momento y se puede cambiar más adelante.

## <a name="changes-affecting-vsix-format-and-installation"></a>Cambios que afectan a la instalación y el formato VSIX

Estamos introduciendo la v3 VSIX formato (versión 3) para admitir la experiencia de instalación ligera.

Incluyen cambios en el formato VSIX:

* Declaración de requisitos previos del programa de instalación. Para hacer realidad la promesa de una ligera y rápida: instalación de Visual Studio, el instalador ahora ofrece más opciones de configuración a los usuarios. Como resultado, para asegurarse de que se instalan las características y los componentes requeridos por una extensión, las extensiones se deben declaran sus dependencias.
  * El instalador de Visual Studio 2017 ofrecerá automáticamente adquirir e instalar los componentes necesarios para el usuario como parte de la instalación de la extensión.
  * Los usuarios también se le avisará cuando se intenta instalar una extensión que no se creó mediante el nuevo formato VSIX v3, incluso si se han marcado en el manifiesto para seleccionar como destino la versión 15.0.
* Capacidades mejoradas para el formato VSIX. Para cumplir con un [instalación de bajo impacto](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install) de Visual Studio que también es compatible con instalaciones en paralelo, ya no guardar la mayoría de los datos de configuración en el registro del sistema y se han movido los ensamblados específico de Visual Studio fuera de la GAC. También se aumenta las capacidades del formato VSIX y motor de instalación de VSIX, que le permite usar en lugar de una MSI o EXE para instalar las extensiones para algunos tipos de instalación.

  Las nuevas capacidades incluyen:

  * En el registro en la instancia especificada de Visual Studio.
  * Instalación de fuera de la [carpeta extensions](set-install-root.md).
  * Detección de arquitectura de procesador.
  * Dependencia de paquetes de idioma separados por idioma.
  * Instalación con [compatibilidad con NGEN](ngen-support.md).

## <a name="building-an-extension-for-visual-studio-2017"></a>Compilar una extensión para Visual Studio 2017

Diseñador de herramientas para la creación del nuevo formato de manifiesto de VSIX v3 ahora está disponible en Visual Studio 2017. Consulte el documento adjunto [Cómo: Migrar proyectos de extensibilidad de Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) para obtener más información sobre el uso de las herramientas del diseñador o realizar actualizaciones manuales en el proyecto y el manifiesto para desarrollar extensiones VSIX v3.

## <a name="change-visual-studio-user-data-path"></a>Cambio: Ruta de acceso de datos de usuario en Visual Studio

Anteriormente, solo una instalación de cada versión principal de Visual Studio puede existir en cada máquina. Para admitir las instalaciones en paralelo de Visual Studio 2017, pueden existir varias rutas de acceso de datos de usuario para Visual Studio en el equipo del usuario.

Código que se ejecuta dentro del proceso de Visual Studio debe actualizarse para usar el Administrador de configuración de Visual Studio. Código que se ejecuta fuera del proceso de Visual Studio puede encontrar la ruta de acceso de usuario de una instalación específica de Visual Studio [siguiendo las instrucciones aquí](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Cambio: Caché global de ensamblados (GAC)

Mayoría de los ensamblados de núcleo de Visual Studio ya no se instala en la GAC. Se han realizado los siguientes cambios para que el código que se ejecuta en proceso de Visual Studio todavía puede encontrar los ensamblados necesarios en tiempo de ejecución.

> [!NOTE]
> [INSTALLDIR] a continuación, hace referencia al directorio raíz de instalación de Visual Studio. *VSIXInstaller.exe* se rellenará automáticamente esto, pero para escribir código de implementación personalizado, lea [localización de Visual Studio](locating-visual-studio.md).

* Ensamblados que solo se instalaron en la GAC:
  * Estos ensamblados se instalan ahora en <em>[INSTALLDIR] \Common7\IDE\*, * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> o *\Common7\IDE\PrivateAssemblies [INSTALLDIR]*. Estas carpetas son parte de las rutas de búsqueda del proceso de Visual Studio.

* Ensamblados que se instalaron en una ruta de acceso que no sean de sondeo y en la GAC:
  * La copia en la GAC se quitó del programa de instalación.
  * Un *.pkgdef* archivo se agregó para especificar una entrada de base de código para el ensamblado.

    Por ejemplo:

    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    En tiempo de ejecución, el subsistema de Visual Studio pkgdef combinará estas entradas en el archivo de configuración en tiempo de ejecución del proceso de Visual Studio (bajo *[VSAPPDATA]\devenv.exe.config*) como [ `<codeBase>` ](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) elementos. Se trata de la manera recomendada para permitir que el proceso de Visual Studio buscar el ensamblado, ya que se evita la búsqueda a través de las rutas de acceso de sondeo.

### <a name="reacting-to-this-breaking-change"></a>Reacción a este cambio importante

* Si la extensión se ejecuta dentro del proceso de Visual Studio:
  * El código podrá encontrar los ensamblados básicos de Visual Studio.
  * Considere el uso de un *.pkgdef* archivo para especificar una ruta de acceso a los ensamblados, si es necesario.
* Si la extensión se ejecuta fuera del proceso de Visual Studio:
  * Considere la posibilidad de buscar ensamblados básicos de Visual Studio en <em>[INSTALLDIR] \Common7\IDE\*, * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> o *[INSTALLDIR] \Common7\IDE\PrivateAssemblies*con resolución de ensamblado o archivo de configuración.

## <a name="change-reduce-registry-impact"></a>Cambio: Reducir el impacto en el registro

### <a name="global-com-registration"></a>Registro de COM global

* Visual Studio instalado anteriormente, muchas de las claves del registro en los subárboles HKEY_CLASSES_ROOT y HKEY_LOCAL_MACHINE para admitir el registro de COM nativo. Para eliminar este impacto, Visual Studio ahora usa [activación sin registro para los componentes COM](https://msdn.microsoft.com/library/ms973913.aspx).
* Como resultado, la mayoría de TLB / OLB / ya no se instalan los archivos DLL en % ProgramFiles (x86) %\Common Shared\MSEnv de programa\Microsoft Visual Studio de forma predeterminada. Estos archivos se instalan ahora en [INSTALLDIR] con correspondientes manifiestos COM sin registro utilizados por el proceso de host de Visual Studio.
* Como resultado, el código externo que se basa en el registro de COM global para las interfaces COM de Visual Studio ya no encontrará estos registros. Código que se ejecuta dentro del proceso de Visual Studio no podrá ver una diferencia.

### <a name="visual-studio-registry"></a>Registro Visual Studio

* Anteriormente, Visual Studio instalado muchas de las claves del registro en el sistema **HKEY_LOCAL_MACHINE** y **HKEY_CURRENT_USER** subárboles bajo una clave específica de Visual Studio:
  * **HKLM\Software\Microsoft\VisualStudio\{versión}**: Claves de registro creadas por los instaladores de MSI y extensiones de por equipo.
  * **HKCU\Software\Microsoft\VisualStudio\{versión}**: Claves de registro creadas por Visual Studio para almacenar la configuración específica del usuario.
  * **HKCU\Software\Microsoft\VisualStudio\{versión} _Config**: Combina una copia de la clave HKLM de Visual Studio anterior, además de las claves del registro de *.pkgdef* archivos con las extensiones.
* Para reducir el impacto en el registro, Visual Studio usa ahora la [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) función para almacenar las claves del registro en un archivo binario privado en *[VSAPPDATA]\privateregistry.bin*. Solo un número muy pequeño de claves específico de Visual Studio permanece en el registro del sistema.

* Código existente que se ejecuta dentro del proceso de Visual Studio no se ve afectado. Visual Studio le redirigirá a todas las operaciones del registro bajo la clave HKCU Visual Studio específica en el registro privado. Leer y escribir en otras ubicaciones del registro continuará con el registro del sistema.
* Código externo debe cargar y leer desde este archivo para las entradas del registro de Visual Studio.

### <a name="reacting-to-this-breaking-change"></a>Reacción a este cambio importante

* Para utilizar la activación sin registro para los componentes COM también se debe convertir código externo.
* Los componentes externos pueden encontrar la ubicación de Visual Studio [siguiendo las instrucciones aquí](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).
* Se recomienda usan los componentes externos la [externo Settings Manager](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) en lugar de leer o escribir directamente a las claves del registro de Visual Studio.
* Compruebe si los componentes que usa la extensión pueden haber implementado otra técnica para el registro. Por ejemplo, extensiones del depurador pueden ser capaces de aprovechar las ventajas del nuevo [msvsmon registro JSON archivo COM](migrate-debugger-COM-registration.md).
