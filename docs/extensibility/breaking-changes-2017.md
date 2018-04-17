---
title: Cambios importantes en la extensibilidad de Visual Studio de 2017 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bff9c97b052f359f3d03e12093b1cdae86d5dfbd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Cambios en la extensibilidad de Visual Studio de 2017

Con Visual Studio de 2017, le ofrecemos un [más rápido, ligero experiencia de instalación de Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer) que reduce el impacto de Visual Studio en los sistemas de usuario, mientras se proporciona a los usuarios elección mayor sobre las características y las cargas de trabajo que se instalan. Para admitir estas mejoras, se ha realizado cambios en el modelo de extensibilidad y han realizado algunos cambios importantes a la extensibilidad de Visual Studio. Este documento describirá los detalles técnicos de estos cambios, y qué puede hacer para solucionarlos. Tenga en cuenta que algunos datos se detalles de implementación en un momento y se pueden cambiar más adelante.

## <a name="changes-affecting-vsix-format-and-installation"></a>Cambios que afectan a la instalación y el formato VSIX

Estamos introduciendo el v3 VSIX formato (versión 3) para admitir la experiencia de instalación ligera.

Incluyen cambios en el formato VSIX:

* Declaración de requisitos previos de instalación. Para entregar la promesa de una ligera, rápida o instalar Visual Studio, el programa de instalación ahora ofrece más opciones de configuración a los usuarios. Como resultado, para asegurarse de que se instalan las características y los componentes requeridos por una extensión, las extensiones deberá declarar sus dependencias.
  * El instalador de Visual Studio de 2017 proporcionará automáticamente adquirir e instalar los componentes necesarios para el usuario como parte de la instalación de la extensión.
  * Los usuarios también le avisará cuando intenta instalar una extensión que no se creó con el nuevo formato de v3 VSIX, incluso si se han marcado en el manifiesto como destinado a la versión 15.0.
* Capacidades mejoradas para el formato VSIX. Entregar un [instalación de impacto reducido](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install) de Visual Studio que también es compatible con instalaciones en paralelo, ya no guardar la mayoría de los datos de configuración en el registro del sistema y han entrado ensamblados específicos de Visual Studio fuera de la GAC. También hemos incrementado las capacidades del formato VSIX y el motor de instalación de VSIX, lo que le permite usar en lugar de un MSI o EXE para instalar las extensiones para algunos tipos de instalación.

  Las nuevas capacidades incluyen:

  * Registro en la instancia especificada de Visual Studio.
  * Instalación de fuera de la [carpeta extensions](set-install-root.md).
  * Detección de arquitectura de procesador.
  * Dependencia de paquetes de idioma separados por idioma.
  * Instalación con [compatibilidad con NGEN](ngen-support.md).

## <a name="building-an-extension-for-visual-studio-2017"></a>Crear una extensión para Visual Studio de 2017

Diseñador de herramientas para la creación del nuevo formato de manifiesto de VSIX v3 ahora está disponible en Visual Studio de 2017. Vea el documento de acompañamiento [Cómo: migrar los proyectos de extensibilidad en Visual Studio de 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) para obtener más información sobre el uso de las herramientas del diseñador o realizar actualizaciones manuales en el proyecto y el manifiesto para desarrollar extensiones de v3 VSIX.

## <a name="change-visual-studio-user-data-path"></a>Cambio: Ruta de acceso de datos de usuario de Visual Studio

Anteriormente, solo una instalación de cada versión principal de Visual Studio podría existir en cada equipo. Para admitir las instalaciones en paralelo de 2017 de Visual Studio, pueden existir varias rutas de acceso de datos de usuario de Visual Studio en el equipo del usuario.

Código que se ejecuta dentro del proceso de Visual Studio debe actualizarse para utilizar el Administrador de configuración de Visual Studio. Código que se ejecuta fuera del proceso de Visual Studio puede encontrar la ruta de acceso de usuario de una instalación de Visual Studio específica [siguiendo las instrucciones aquí](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Cambio: Caché de ensamblados Global (GAC)

Mayoría de los ensamblados de núcleo de Visual Studio ya no se instala en la GAC. Se realizaron los siguientes cambios para que el código que se ejecuta en proceso de Visual Studio encontrará los ensamblados necesarios en tiempo de ejecución.

> [!NOTE]
> [INSTALLDIR] a continuación hace referencia al directorio raíz de instalación de Visual Studio. VSIXInstaller.exe automáticamente se rellenar esto, pero para escribir código de implementación personalizados, lea [buscar Visual Studio](locating-visual-studio.md).

* Ensamblados que solo se instalaron en la GAC:
  * Estos ensamblados ya están instalados en \Common7\IDE [INSTALLDIR]\, [INSTALLDIR] \Common7\IDE\PublicAssemblies o \Common7\IDE\PrivateAssemblies [INSTALLDIR]. Estas carpetas son parte de las rutas de búsqueda del proceso de Visual Studio.
* Ensamblados que se instalaron en una ruta de acceso de sondeo no y en la GAC:
  * El programa de instalación se ha quitado la copia en la GAC.
  * Un archivo .pkgdef se agregó para especificar una entrada del código base del ensamblado.

    Por ejemplo:
    
    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    En tiempo de ejecución, el subsistema de pkgdef de Visual Studio combinará estas entradas en el archivo de configuración de tiempo de ejecución del proceso de Visual Studio (en [VSAPPDATA]\devenv.exe.config) como [ `<codeBase>` ](https://msdn.microsoft.com/en-us/library/efs781xb(v=vs.110).aspx) elementos. Se trata de la manera recomendada para permitir que el proceso de Visual Studio encuentra el ensamblado, porque evita buscar a través de las rutas de acceso de sondeo.

### <a name="reacting-to-this-breaking-change"></a>Reacción a este cambio problemático

* Si la extensión se ejecuta dentro del proceso de Visual Studio:
  * El código podrá encontrar los ensamblados básicos de Visual Studio.
  * Considere la posibilidad de usar un archivo .pkgdef para especificar una ruta de acceso a los ensamblados si es necesario.
* Si la extensión se ejecuta fuera del proceso de Visual Studio:
  * Considere la posibilidad de buscar ensamblados básicos de Visual Studio en \Common7\IDE [INSTALLDIR]\, [INSTALLDIR] \Common7\IDE\PublicAssemblies o \Common7\IDE\PrivateAssemblies [INSTALLDIR] con la resolución de ensamblado o archivo de configuración.

## <a name="change-reduce-registry-impact"></a>Cambio: Reducir el impacto en el registro

### <a name="global-com-registration"></a>Registro de COM global

* Visual Studio instalado anteriormente, muchas de las claves del registro en los subárboles HKEY_CLASSES_ROOT y HKEY_LOCAL_MACHINE para admitir el registro de COM nativo. Para eliminar este impacto, Visual Studio ahora usa [activación sin registro para los componentes COM](https://msdn.microsoft.com/en-us/library/ms973913.aspx).
* Como resultado, la mayoría de TLB / OLB / archivos DLL en % ProgramFiles (x86) %\Common Shared\MSEnv de programa\Microsoft ya no se instalan de manera predeterminada en Visual Studio. Ahora, estos archivos se instalan en [INSTALLDIR] con correspondientes manifiestos COM sin registro utilizados por el proceso de host de Visual Studio.
* Como resultado, el código externo que se basa en el registro de COM global para las interfaces COM de Visual Studio ya no encontrará estos registros. Código que se ejecuta dentro de proceso de Visual Studio no podrán ver una diferencia.

### <a name="visual-studio-registry"></a>Registro Visual Studio

* Anteriormente, Visual Studio instalado muchas claves del registro en subárboles HKEY_LOCAL_MACHINE y HKEY_CURRENT_USER del sistema en una clave específicos de Visual Studio:
  * HKLM\Software\Microsoft\VisualStudio\\**versión**: claves del registro creadas por los instaladores MSI y extensiones de cada equipo.
  * HKCU\Software\Microsoft\VisualStudio\\**versión**: las claves del registro creadas por Visual Studio para almacenar la configuración específica del usuario.
  * HKCU\Software\Microsoft\VisualStudio\\**versión**_Config: una copia de la clave HKLM de Visual Studio anterior, además de las claves del registro se combinó de archivos .pkgdef por las extensiones.
* Para reducir el impacto en el registro, Visual Studio usa ahora la [RegLoadAppKey](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724886(v=vs.85).aspx) función para almacenar las claves del registro en un archivo binario privado en [VSAPPDATA]\privateregistry.bin. Solo un número muy pequeño de claves específicos de Visual Studio permanece en el registro del sistema.
* Código existente que se ejecuta dentro del proceso de Visual Studio no se ve afectado. Visual Studio le redirigirá todas las operaciones del registro bajo la clave HKCU Visual Studio-específica en el registro privado. Leer y escribir en otras ubicaciones del registro continuarán utilizando el registro del sistema.
* Código externo deberá cargar y leer desde este archivo de entradas del registro de Visual Studio.

### <a name="reacting-to-this-breaking-change"></a>Reacción a este cambio problemático

* Código externo se debe convertir para usar la activación sin registro para los componentes COM también.
* Componentes externos pueden encontrar la ubicación de Visual Studio [siguiendo las instrucciones aquí](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).
* Le recomendamos que usan componentes externos la [el Administrador de configuración externo](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.settings.externalsettingsmanager.aspx) en lugar de lectura/escritura directamente a las claves del registro de Visual Studio.
* Compruebe si los componentes que se está usando la extensión pueden haber implementado otra técnica para el registro. Por ejemplo, extensiones del depurador pueden aprovechar las ventajas del nuevo [msvsmon registro archivo JSON COM](migrate-debugger-COM-registration.md).
