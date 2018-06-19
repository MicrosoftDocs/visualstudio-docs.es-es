---
title: Conceptos básicos de Windows Installer | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8fba35aba1e1947ee4eeeb59ca2225253e2aa3a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144755"
---
# <a name="windows-installer-basics"></a>Conceptos básicos de Windows Installer
Windows Installer instala y desinstala las aplicaciones o productos de software en el equipo del usuario, llevar a cabo estas tareas en unidades denominadas componentes de Windows Installer (a veces denominados WICs o simplemente componentes). Un GUID identifica cada WIC, que es la unidad básica de la instalación y el recuento de referencias para configuraciones mediante Windows Installer.  
  
 Para obtener documentación completa de Windows Installer, vea el tema de Platform SDK, [Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx).  
  
## <a name="authoring-a-vspackage"></a>Creación de un paquete VSPackage  
 Windows Installer utiliza paquetes de instalación, que contienen información que Windows Installer necesita para instalar, desinstalar o reparar un producto y para ejecutar la interfaz de usuario (UI) de instalación. Cada paquete de instalación incluye un archivo .msi, que contiene una base de datos de instalación, una secuencia de información de resumen y secuencias de datos para distintas partes de la instalación. Para usar el programa de instalación, debe crear una instalación. Dado que el instalador organiza las instalaciones de la idea de componentes y almacena información sobre la instalación en una base de datos relacional, el proceso de creación de un paquete de instalación ampliamente implica los pasos siguientes:  
  
1.  Planear la configuración de creación para admitir el control de versiones y las estrategias de side-by-side.  
  
2.  Identificar las características que se presentan a los usuarios.  
  
3.  Organizar el VSPackage y dependencias en componentes.  
  
4.  Rellenar la base de datos de instalación con la información.  
  
5.  Validar el paquete de instalación.  
  
 Esta documentación se refiere principalmente con los pasos primeros y terceros del proceso. Durante estos pasos organizar sus características de VSPackage en WICs por lo que también puede enmarcar el control de versiones y la estrategia para las versiones posteriores de la cuenta de servicio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Los tres pasos restantes se tratan detalladamente en la documentación de Windows Installer en Platform SDK.  
  
## <a name="key-terms"></a>Términos clave  
 Siguiente es definiciones de términos clave relacionados con la tecnología de Windows Installer.  
  
 Recurso  
 Archivos, claves del registro, accesos directos, o y así sucesivamente, que puede instalarse en un equipo. Estos recursos se agrupan lógicamente en componentes de Windows Installer.  
  
 Componente de Windows Installer (WIC)  
 La unidad básica de instalación que representa una agrupación lógica de los recursos relacionados que se instalan y desinstalan como una unidad. Componentes de Windows Installer se identifican mediante un identificador de componente único, o un GUID. Además, Windows Installer mantiene su nivel de WIC de recuento de referencias. Para tener una flexibilidad máxima de control de versiones, incluir no más de un recurso principal, como un archivo DLL, en un determinado WIC. Tenga en cuenta que después de identificar y rellenar un WIC, asígnele un GUID e implementarlo, no se puede cambiar su composición. Para obtener más información, consulte [organizar las aplicaciones en componentes](http://msdn.microsoft.com/library/aa370561.aspx).  
  
 Paquete redistribuible (paquete)  
 Una unidad de implementación que consta de un archivo .msi y archivos de origen externo a la que puede ser indicativo de este archivo. Un paquete contiene toda la información que Windows Installer necesita para ejecutar la interfaz de usuario y para instalar o desinstalar la aplicación.  
  
 archivo .msi  
 Un archivo de almacenamiento estructurado COM que contiene las instrucciones y los datos necesarios para instalar una aplicación. Cada paquete contiene al menos un archivo MSI. El archivo .msi contiene la base de datos de instalador, una secuencia de información de resumen y posiblemente una o varias transformaciones y los archivos de código fuente interna. Que se instalen archivos pueden se comprimen en un gabinete y almacenarse en una secuencia en el archivo .msi o almacenados, comprimidos o no lo está, fuera del archivo .msi en el medio de origen. Para obtener más información, consulte [extensiones de archivo de Windows Installer](http://msdn.microsoft.com/library/aa372842\(VS.85\).aspx).  
  
## <a name="windows-installer-rules-enforcement"></a>Cumplimiento de las reglas del instalador de Windows  
 Dos conjuntos de reglas determinan la implementación de recursos a través de los componentes del programa de instalación. Un conjunto de reglas se mantiene por Windows Installer, mientras que debe aplicar el segundo conjunto como autor de la instalación.  
  
> [!NOTE]
>  Cumplimiento de reglas de Windows Installer se produce sólo si se ejecuta una validación del archivo MSI. No obstante, se les advierte para tratar estas reglas como prácticas recomendadas. Para obtener más información, consulte [validar una base de datos de instalación](http://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) y [validación del paquete](http://msdn.microsoft.com/library/aa370569\(VS.85\).aspx).  
  
#### <a name="installer-enforced-rules"></a>Reglas exigidas por el programa de instalación  
  
-   Todos los archivos de un determinado componente deben instalarse en el mismo directorio. Por el contrario, los archivos instalados para separar las carpetas deben pertenecer para separar los componentes.  
  
-   Puede haber solo una ruta de acceso de clave por componente. La ruta de acceso de clave es simplemente una clave de registro o del archivo que representa todo el componente.  
  
#### <a name="component-provider-responsibilities"></a>Responsabilidades del proveedor de componentes  
  
-   Los dos recursos que pueden enviar por separado en las versiones posteriores deben existir en componentes independientes. Los recursos deben estar agrupados en el mismo componente sólo cuando esté seguro de que estos recursos nunca se enviarán por separado. De hecho, se recomienda que todos los recursos principales (por ejemplo, archivos DLL) siempre se encuentran en WICs independientes. Para obtener más información, consulte [definir componentes del instalador](http://msdn.microsoft.com/library/aa368269\(VS.85\).aspx).  
  
-   Nunca debe enviar ningún recurso con control de versiones en más de un WIC.  
  
## <a name="see-also"></a>Vea también  
 [¿Qué ocurre si se siguen las reglas de componentes?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)