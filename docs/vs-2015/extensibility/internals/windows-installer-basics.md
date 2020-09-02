---
title: Aspectos básicos de Windows Installer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4693654e12dc37209cb92e3e2ba95bde8bd13e77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687680"
---
# <a name="windows-installer-basics"></a>Datos básicos de Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En el Windows Installer se instalan y desinstalan aplicaciones o productos de software en el equipo de un usuario, lo que realiza estas tareas en unidades denominadas Windows Installer componentes (a veces denominados WICs o simplemente componentes). Un GUID identifica cada WIC, que es la unidad básica de instalación y el recuento de referencias para las configuraciones mediante Windows Installer.  
  
 Para obtener documentación completa del Windows Installer, vea el tema de Platform SDK [Windows Installer](/previous-versions/2kt85ked(v=vs.120)).  
  
## <a name="authoring-a-vspackage"></a>Creación de un VSPackage  
 Windows Installer usa paquetes de instalación, que contienen información que Windows Installer debe instalar, desinstalar o reparar un producto y ejecutar la interfaz de usuario (UI) del programa de instalación. Cada paquete de instalación incluye un archivo. msi que contiene una base de datos de instalación, un flujo de información de Resumen y secuencias de datos para varias partes de la instalación. Para usar el instalador, debe crear una instalación de. Dado que el instalador organiza las instalaciones en torno al concepto de componentes y almacena información acerca de la instalación en una base de datos relacional, el proceso de creación de un paquete de instalación conlleva amplios pasos:  
  
1. Planifique la creación de la instalación para que admita las versiones y las estrategias en paralelo.  
  
2. Identifique las características que se van a presentar a los usuarios.  
  
3. Organice el VSPackage y las dependencias en componentes.  
  
4. Rellene la base de datos de instalación con información.  
  
5. Valide el paquete de instalación.  
  
   Esta documentación se centra principalmente en el primer y tercer paso del proceso. Durante estos pasos, organizará las características de VSPackage en WICs para que pueda enmarcar la estrategia de control de versiones y servicio para tener en cuenta las versiones posteriores de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Los tres pasos restantes se explican en detalle en Windows Installer documentación del SDK de la plataforma.  
  
## <a name="key-terms"></a>Términos clave  
 A continuación se enumeran las definiciones de los términos clave relacionados con la tecnología de Windows Installer.  
  
 Resource  
 Archivos, claves del registro, accesos directos, etc. que se pueden instalar en un equipo. Estos recursos se agrupan lógicamente en componentes de Windows Installer.  
  
 Componente de Windows Installer (WIC)  
 Unidad básica de instalación que representa una agrupación lógica de recursos relacionados que se instalan y desinstalan como una unidad. Los componentes de Windows Installer se identifican mediante un identificador de componente único o un GUID. Además, Windows Installer mantiene su recuento de referencias en el nivel de WIC. Para obtener la máxima flexibilidad de control de versiones, no incluya más de un recurso principal, como un archivo DLL, en un WIC determinado. Tenga en cuenta que, después de identificar y rellenar WIC, darle un GUID e implementarlo, no podrá cambiar su composición. Para obtener más información, vea [organizar aplicaciones en componentes](https://msdn.microsoft.com/library/aa370561.aspx).  
  
 Paquete (paquete redistribuible)  
 Una unidad de implementación que consta de un archivo. msi y archivos de código fuente externos a los que puede apuntar este archivo. Un paquete contiene toda la información que Windows Installer necesita para ejecutar la interfaz de usuario y para instalar o desinstalar la aplicación.  
  
 Archivo. msi  
 Archivo de almacenamiento estructurado en COM que contiene las instrucciones y los datos necesarios para instalar una aplicación. Cada paquete contiene al menos un archivo. msi. El archivo. msi contiene la base de datos del instalador, una secuencia de información de Resumen y, posiblemente, una o más transformaciones y archivos de código fuente internos. Los archivos que se van a instalar pueden comprimirse en un contenedor y almacenarse en una secuencia del archivo. msi o almacenarse, comprimirse o descomprimirse fuera del archivo. msi en el medio de origen. Para obtener más información, vea [Windows Installer extensiones de archivo](https://msdn.microsoft.com/library/aa372842\(VS.85\).aspx).  
  
## <a name="windows-installer-rules-enforcement"></a>Aplicación de reglas de Windows Installer  
 Dos conjuntos de reglas determinan la implementación de recursos a través de los componentes del programa de instalación. El propio Windows Installer mantiene un conjunto de reglas, mientras que debe aplicar el segundo conjunto como autor de la instalación.  
  
> [!NOTE]
> La aplicación de reglas de Windows Installer solo se produce si se ejecuta una validación del archivo. msi. No obstante, se recomienda tratar estas reglas como procedimientos recomendados. Para obtener más información, vea [validar una base de datos de instalación](https://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) y la validación de [paquetes](https://msdn.microsoft.com/library/aa370569\(VS.85\).aspx).  
  
#### <a name="installer-enforced-rules"></a>Reglas aplicadas por el instalador  
  
- Todos los archivos de un componente determinado deben instalarse en el mismo directorio. Por el contrario, los archivos instalados en carpetas independientes deben pertenecer a componentes independientes.  
  
- Solo puede haber una ruta de acceso de clave por componente. La ruta de acceso de la clave es simplemente un archivo o una clave del registro que representa todo el componente.  
  
#### <a name="component-provider-responsibilities"></a>Responsabilidades del proveedor de componentes  
  
- Dos recursos cualesquiera que podrían distribuirse por separado en versiones posteriores deben existir en componentes independientes. Los recursos deben agruparse en el mismo componente solo si está seguro de que estos recursos nunca se enviarán por separado. De hecho, se recomienda que todos los recursos principales (archivos dll, por ejemplo) se encuentren siempre en WICs independientes. Para obtener más información, vea [definir componentes del instalador](https://msdn.microsoft.com/library/aa368269\(VS.85\).aspx).  
  
- Ningún recurso con versión debe distribuirse en más de un WIC.  
  
## <a name="see-also"></a>Consulte también  
 [¿Qué ocurre si se interrumpen las reglas de componentes?](https://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)
