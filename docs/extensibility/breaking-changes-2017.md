---
title: Cambios importantes en la extensibilidad de Visual Studio de 2017 | Documentos de Microsoft
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 2e6e4b3d9d1528d57fe181b3765e1ce3624bebad
ms.lasthandoff: 03/07/2017

---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Cambios en la extensibilidad de Visual Studio de 2017

Con Visual Studio de 2017, le ofrecemos un [más rápido y ligero experiencia de instalación de Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer) que reduce el impacto de Visual Studio en los sistemas de usuario, mientras se brinda a los usuarios mayor variedad de cargas de trabajo y características instalados. Para admitir estas mejoras, ha realizado cambios en el modelo de extensibilidad y ha realizado algunos cambios importantes a la extensibilidad de Visual Studio. Este documento describe los detalles técnicos de estos cambios y qué se puede hacer para solucionarlos. Tenga en cuenta que algunos datos se detalles de implementación en un momento y se pueden cambiar más adelante.

## <a name="changes-affecting-vsix-format-and-installation"></a>Cambios que afectan a la instalación y el formato VSIX

Estamos introduciendo el v3 VSIX formato (versión 3) para admitir la experiencia de instalación ligera.

Cambios en el formato VSIX incluyen:

* Declaración de requisitos previos de instalación. Para entregar la promesa de una ligera, rápida o instalar Visual Studio, el programa de instalación ahora ofrece más opciones de configuración a los usuarios. Como resultado, para asegurarse de que se instalan las características y los componentes requeridos por una extensión, las extensiones deberá declarar sus dependencias.
  * El instalador de Visual Studio de 2017 automáticamente ofrecerá a adquirir e instalar los componentes necesarios para el usuario como parte de la instalación de la extensión.
  * Los usuarios también le avisará cuando intenta instalar una extensión que no se ha creado con el nuevo formato VSIX v3, incluso si se han marcado en su manifiesto como objetivo versión 15.0.
* Capacidades mejoradas para el formato VSIX. Para entregar en un [instalación de bajo impacto](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install) de Visual Studio que también es compatible con instalaciones en paralelo, ya no guardar la mayoría de los datos de configuración en el registro del sistema y ha movido los ensamblados de la GAC específico de Visual Studio. También aumentamos las capacidades del formato VSIX y motor de instalación de VSIX, que permite usar en lugar de un MSI o EXE para instalar las extensiones para algunos tipos de instalación.

  Las nuevas capacidades incluyen:

  * Registro en la instancia especificada de Visual Studio.
  * Instalación de fuera de la [carpeta extensiones](set-install-root.md).
  * Detección de arquitectura de procesador.
  * Dependencia de paquetes de idioma lenguaje separados.
  * Instalación con [compatibilidad con NGEN](ngen-support.md).

## <a name="building-an-extension-for-visual-studio-2017"></a>Creación de una extensión de Visual Studio de 2017

Diseñador de herramientas para la creación del nuevo formato de manifiesto de VSIX v3 ahora está disponible en 2017 de Visual Studio. Consulte el documento de acompañamiento [Cómo: migrar proyectos de extensibilidad en Visual Studio de 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) para obtener más información sobre el uso de las herramientas del diseñador o realizar actualizaciones manuales en el proyecto y el manifiesto para desarrollar extensiones VSIX v3.

## <a name="change-visual-studio-user-data-path"></a>Cambio: Ruta de datos de usuario de Visual Studio

Anteriormente, sólo una instalación de cada versión principal de Visual Studio puede existir en cada máquina. Para admitir las instalaciones en paralelo de 2017 de Visual Studio, pueden existir varias rutas de acceso de datos de usuario de Visual Studio en el equipo del usuario.

Código que se ejecuta dentro del proceso de Visual Studio debe actualizarse para utilizar el Administrador de configuración de Visual Studio. Código que se ejecuta fuera del proceso de Visual Studio puede encontrar la ruta de acceso de usuario de una instalación específica de Visual Studio [siguiendo las instrucciones aquí](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).

## <a name="change-global-assembly-cache-gac"></a>Cambio: Caché de ensamblados Global (GAC)

Mayoría de los ensamblados de Visual Studio core ya no se instala en la GAC. Se han realizado los siguientes cambios para que el código se ejecuta en proceso de Visual Studio todavía puede encontrar los ensamblados necesarios en tiempo de ejecución.

* Ensamblados que sólo estaban instalados en la GAC:
  * Estos ensamblados se instalan ahora en %VsFolder%\Common7\IDE\, %VsFolder%\Common7\IDE\PublicAssemblies o % VsFolder%\Common7\IDE\PrivateAssemblies. Estas carpetas son parte de las rutas de búsqueda del proceso de Visual Studio.
* Ensamblados que se instalaron en una ruta de acceso de sondeo no y en la GAC:
  * El programa de instalación se ha quitado la copia en la GAC.
  * Se agregó un archivo .pkgdef para especificar una entrada del código base del ensamblado.

    Por ejemplo:
    
    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    En tiempo de ejecución, el subsistema de Visual Studio pkgdef combinará estas entradas en el archivo de configuración de tiempo de ejecución del proceso de Visual Studio (en % VsAppDataFolder%\devenv.exe.config) como [ `<codeBase>` ](https://msdn.microsoft.com/en-us/library/efs781xb(v=vs.110).aspx) elementos. Este es el método recomendado para permitir que el proceso de Visual Studio encontrar el ensamblado, porque evita la búsqueda a través de rutas de acceso de sondeo.

### <a name="reacting-to-this-breaking-change"></a>Reaccionar ante este cambio problemático

* Si la extensión se ejecuta dentro del proceso de Visual Studio:
  * El código podrá encontrar los ensamblados básicos de Visual Studio.
  * Considere el uso de un archivo .pkgdef para especificar una ruta de acceso a los ensamblados si es necesario.
* Si la extensión se ejecuta fuera del proceso de Visual Studio:
  * Considere la posibilidad de buscar los ensamblados básicos de Visual Studio en %VsFolder%\Common7\IDE\, %VsFolder%\Common7\IDE\PublicAssemblies o %VsFolder%\Common7\IDE\PrivateAssemblies con resolución de ensamblado o archivo de configuración.

## <a name="change-reduce-registry-impact"></a>Cambio: Reducir el impacto en el registro

### <a name="global-com-registration"></a>Registro COM global

* Visual Studio instalado anteriormente, muchas de las claves del registro en los subárboles HKEY_CLASSES_ROOT y HKEY_LOCAL_MACHINE para admitir el registro de COM nativo. Para eliminar este impacto, Visual Studio utiliza ahora [activación sin registro para los componentes COM](https://msdn.microsoft.com/en-us/library/ms973913.aspx).
* Como resultado, la mayoría de TLB / OLB archivos DLL bajo % ProgramFiles (x86) %\Common Shared\MSEnv de programa\Microsoft ya no está instalado de manera predeterminada en Visual Studio. Ahora, estos archivos se instalan en % VsFolder % con correspondientes manifiestos COM sin registro utilizados por el proceso de host de Visual Studio.
* Como resultado, el código externo que se basa en el registro global de COM para las interfaces COM de Visual Studio ya no encontrará estos registros. Código que se ejecuta dentro del proceso de Visual Studio no podrá ver una diferencia.

### <a name="visual-studio-registry"></a>Registro Visual Studio

* Visual Studio instalados anteriormente, muchas de las claves del registro en los subárboles HKEY_LOCAL_MACHINE y HKEY_CURRENT_USER del sistema bajo una clave específico de Visual Studio:
  * HKLM\Software\Microsoft\VisualStudio\\**versión**: claves del registro creadas por los instaladores MSI y extensiones de máquina.
  * HKCU\Software\Microsoft\VisualStudio\\**versión**: las claves del registro creadas por Visual Studio para almacenar la configuración específica del usuario.
  * HKCU\Software\Microsoft\VisualStudio\\**versión**_Config: una copia de la clave HKLM de Visual Studio anterior, además de las claves del registro combinados desde archivos .pkgdef extensiones.
* Para reducir el impacto en el registro, Visual Studio utiliza ahora el [RegLoadAppKey](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724886(v=vs.85).aspx) (función) para almacenar las claves del registro en un archivo binario privado en % VsAppDataFolder%\privateregistry.bin. Solo un número muy pequeño de claves específico de Visual Studio permanece en el registro del sistema.
* Código existente que se ejecuta dentro del proceso de Visual Studio no se ve afectado. Visual Studio le redirigirá todas las operaciones del registro bajo la clave HKCU Visual Studio específica en el registro privado. Leer y escribir en otras ubicaciones del registro seguirán usando el registro del sistema.
* Código externo deberá cargar y leer desde este archivo para las entradas del registro de Visual Studio.

### <a name="reacting-to-this-breaking-change"></a>Reaccionar ante este cambio problemático

* Código externo se debe convertir para utilizar la activación sin registro para los componentes COM también.
* Componentes externos pueden encontrar la ubicación de Visual Studio [siguiendo las instrucciones aquí](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).
* Se recomienda que utilizan componentes externos la [externo Settings Manager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.settings.externalsettingsmanager.aspx) en lugar de leer o escribir directamente a las claves del registro de Visual Studio.
* Compruebe si los componentes que usa la extensión pueden haber implementado otra técnica para el registro. Por ejemplo, extensiones del depurador pueden aprovechar la nueva [msvsmon registro COM del archivo JSON](migrate-debugger-COM-registration.md).

## <a name="change-lightweight-solution-load"></a>Cambio: Carga de la solución ligera

Cargar solución ligera (LSL) reduce el tiempo de carga de la solución completamente cargando proyectos hasta que el usuario comience a trabajar con ellos. Esto puede afectar a las extensiones que suponen que un proyecto está completamente cargado. Consulte [ligero solución carga](lightweight-solution-load-extension-impact.md) para saber si la extensión puede verse afectado y obtener orientación sobre la actualización de la extensión.

