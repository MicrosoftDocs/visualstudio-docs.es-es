---
title: Conceptos básicos de Windows Installer ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aeea0b17a3c234bb7670642fb9ae0a442c9d60cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703413"
---
# <a name="windows-installer-basics"></a>Datos básicos de Windows Installer
Windows Installer instala y desinstala aplicaciones o productos de software en el equipo de un usuario, realizando estas tareas en unidades denominadas componentes de Windows Installer (a veces denominados WIC o simplemente componentes). Un GUID identifica cada WIC, que es la unidad básica de instalación y recuento de referencias para las configuraciones mediante Windows Installer.

 Para obtener documentación completa de Windows Installer, consulte el tema Platform SDK, [Windows Installer](/previous-versions/2kt85ked(v=vs.120)).

## <a name="authoring-a-vspackage"></a>Creación de un VSPackage
 Windows Installer usa paquetes de instalación, que contienen información que Windows Installer necesita para instalar, desinstalar o reparar un producto y ejecutar la interfaz de usuario (UI) de instalación. Cada paquete de instalación incluye un archivo .msi, que contiene una base de datos de instalación, una secuencia de información de resumen y secuencias de datos para varias partes de la instalación. Para utilizar el instalador, debe crear una instalación. Dado que el instalador organiza las instalaciones en torno al concepto de componentes y almacena información sobre la instalación en una base de datos relacional, el proceso de creación de un paquete de instalación implica en general los siguientes pasos:

1. Planifique la creación de la configuración para admitir sus estrategias de control de versiones y en paralelo.

2. Identifique las características que se presentarán a los usuarios.

3. Organice el VSPackage y las dependencias en componentes.

4. Rellene la base de datos de instalación con información.

5. Valide el paquete de instalación.

   Esta documentación se refiere principalmente al primer y tercer paso del proceso. Durante estos pasos se organizan las características de VSPackage en WICs para que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]pueda enmarcar la estrategia de control de versiones y mantenimiento para tener en cuenta las versiones posteriores de . Los tres pasos restantes se tratan en detalle en la documentación de Windows Installer en Platform SDK.

## <a name="key-terms"></a>Términos clave
 A continuación se muestran definiciones de términos clave relacionados con la tecnología de Windows Installer.

 Archivos de recursos, claves del Registro, accesos directos, etc. que se pueden instalar en un equipo. Estos recursos se agrupan lógicamente en componentes de Windows Installer.

 Componente de Windows Installer (WIC) La unidad básica de instalación que representa una agrupación lógica de recursos relacionados que se instalan y desinstalan como una unidad. Los componentes de Windows Installer se identifican mediante un identificador de componente único o GUID. Además, Windows Installer mantiene su recuento de referencias en el nivel WIC. Para obtener la máxima flexibilidad de control de versiones, no incluya más de un recurso principal, como un archivo DLL, en un WIC determinado. Tenga en cuenta que después de identificar y rellenar un WIC, darle un GUID e implementarlo, no puede cambiar su composición. Para obtener más información, consulte [Organización de aplicaciones en componentes](/windows/desktop/Msi/organizing-applications-into-components).

 Paquete (paquete Redist) Una unidad de implementación que consta de un archivo .msi y archivos de origen externos a los que puede apuntar este archivo. Un paquete contiene toda la información que Windows Installer necesita para ejecutar la interfaz de usuario e instalar o desinstalar la aplicación.

 Archivo .msi Un archivo de almacenamiento estructurado COM que contiene las instrucciones y los datos necesarios para instalar una aplicación. Cada paquete contiene al menos un archivo .msi. El archivo .msi contiene la base de datos del instalador, una secuencia de información de resumen y, posiblemente, una o más transformaciones y archivos de origen internos. Los archivos que se van a instalar se pueden comprimir en un archivador y almacenarse en una secuencia en el archivo .msi o almacenarse, comprimirse o descomprimirse fuera del archivo .msi del medio de origen. Para obtener más información, consulte [Extensiones](/windows/desktop/Msi/windows-installer-file-extensions)de archivo de Windows Installer .

## <a name="windows-installer-rules-enforcement"></a>Aplicación de reglas de Windows Installer
 Dos conjuntos de reglas determinan la implementación de recursos a través de los componentes de la instalación. El propio Windows Installer mantiene un conjunto de reglas, mientras que debe aplicar el segundo conjunto como autor de la instalación.

> [!NOTE]
> La aplicación de las reglas de Windows Installer solo se produce si ejecuta una validación del archivo .msi. Sin embargo, se le advierte que trate estas reglas como mejores prácticas. Para obtener más información, consulte [Validación de una base](/windows/desktop/Msi/validating-an-installation-database) de datos de instalación y validación de [paquetes](/windows/desktop/Msi/package-validation).

#### <a name="installer-enforced-rules"></a>Reglas aplicadas por el instalador

- Todos los archivos de un componente determinado deben instalarse en el mismo directorio. Por el contrario, los archivos instalados en carpetas separadas deben pertenecer a componentes independientes.

- Solo puede haber una ruta de acceso clave por componente. La ruta de acceso de clave es simplemente un archivo o una clave del Registro que representa todo el componente.

#### <a name="component-provider-responsibilities"></a>Responsabilidades del proveedor de componentes

- Los dos recursos que puedan enviarse por separado en versiones posteriores deben existir en componentes independientes. Los recursos deben agruparse en el mismo componente solo cuando esté seguro de que estos recursos nunca se enviarán por separado. De hecho, se recomienda que todos los recursos primarios (DLL, por ejemplo) siempre existan en WIC independientes. Para obtener más información, consulte [Definición de componentes del instalador](/windows/desktop/Msi/defining-installer-components).

- Ningún recurso versionado debe enviarse nunca en más de un WIC.

## <a name="see-also"></a>Vea también
- [¿Qué sucede si se rompen las reglas de componentes?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)
